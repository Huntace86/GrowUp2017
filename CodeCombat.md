# CodeCombat

## 地牢

**code block**

findnearstEnemy()

bool 可以类似字符串使用

寻找敌人可以用各种标签来确定区域敌人，比如right和left。

对于target最好还是if先确定之后再选择打击

函数调用不是方法调用，后者确实需要主体。

函数的出现就是因为要放到循环这种代码块里面，需要成为一个整体。


## 森林


物品有个item.pos.x/y位置能够进行自动选择


on后面设定好一个事件，然后由事件进行处理。

event并不是一个函数，设定完这个函数需要变量(event)，而后事件调不用带()。

event的作用就是同步进行，机器并不能确定每个时间步是否需要同时运行某些内容，但是event就是给了一个并行运行的机会。




## Web development

<br>













## Forest




### GO FETCH
```Python

# You've been caught in a burl trap!
# Send your pet to fetch the health potions!

def goFetch():
    # You can use loops in a handler function.
    while True:
        potion = hero.findNearestItem()
        if potion:
            # Use pet.fetch() to have your pet fetch a potion:
            pet.fetch(potion)
            pass

# When your pet is summoned, it triggers a "spawn" event.
# This tells your pet to run goFetch() at the start of the level
pet.on("spawn", goFetch)


```
此处应该注意文中写的是potion。


```Python



```


### Long Road
```Python
# Move to the right.

# Complete this function:
def onSpawn(event):
    
    # Inside a while-true loop:
    while True:
        # Use hero.findNearestItem()
        item = hero.findNearestItem()
        # If there's an item:
        if item:
            # Use pet.fetch(item) to fetch the item.
            pet.fetch(item)

# Use pet.on() to assign onSpawn to the "spawn" event
pet.on("spawn", onSpawn)

hero.moveXY(76, 35)



```



### Forest Cannon Dancing
```Python
# Your pet should run back and forth on the X marks.
# The hero should cheer the whole time!

# Write the event function onSpawn for the pet.
# This function should make the wolf run back and forth:
# First, run to the right mark, then the left one:
def onSpawn(event):
    while True:
        pet.moveXY(48, 8)
        pet.moveXY(12, 8)


pet.on("spawn",onSpawn)
    
# Cheer up your pet. Don't remove this:
while True:
    hero.say("Run!!!")
    hero.say("Faster!")

```

### REWARD AND RUINATION

```Python
# It seems like the Ogre Chieftain is stealing your gems!
# Use the two artillery cannons to defeat your enemies and gather the gems.

while True:
    enemy = hero.findNearestEnemy()
    if enemy:
        enemyPos = enemy.pos.x + " " + enemy.pos.y
        hero.say("Enemy at " + enemyPos)
        
    # Now that you have sweet revenge, why not have your cake and eat it, too?
    # Find the item's position and say it for your artillery to target.
    item = hero.findNearestItem()
    if item:
        itempos = item.pos.x +" " + item.pos.y
        hero.say("Item at "+ itempos)



```
注意此时需要把两个位置之间加上连接，传递给程序会自动进行分词处理并且说明该如何理解这个内容。


### DEJA BREW

```Python
# You can add strings together, and add numbers into strings.
# Sing along, using string concatenation:
# X potions of health on the wall!
# X potions of health!
# Take Y down, pass it around!
# X-Y potions of health on the wall.

potionsOnTheWall = 10
numToTakeDown = 1
while True:
    hero.say(potionsOnTheWall + " potions of health on the wall!")
    # Sing the next line:
    hero.say(potionsOnTheWall + " potions of health!")
    # Sing the next line:
    hero.say("Take "+ numToTakeDown + "down, pass it around!")
    potionsOnTheWall -= numToTakeDown
    # Sing the last line:
    hero.say(  potionsOnTheWall + " potions of health on the wall.")



```

### BACKWOODS BOMBARIDER

```Python
# The pos property is an object with x and y properties.
# pos.x is a number representing the horizontal position on the map
# pos.y is a number representing the vertical position on the map

while True:
    enemy = hero.findNearestEnemy()
    if enemy:
        x = enemy.pos.x
        # Get the enemy's y position!
        y = enemy.pos.y # ∆ Change this!
        
        # say the x and y position separated by a comma
        hero.say(x + "," + y)
    else:
        hero.say("Cease" + " Fire!")



```
### THE WIZARD'S DOOR


```Python
# Move to Laszlo and get his secret number.
hero.moveXY(30, 13)
las = hero.findNearestFriend().getSecret()

# Add 7 to Laszlo's number to get Erzsebet's number.
# Move to Erzsebet and say her magic number.
erz = las + 7
hero.moveXY(17, 26)
hero.say(erz)

# Divide Erzsebet's number by 4 to get Simonyi's number.
# Go to Simonyi and tell him his number.
simon = erz/4
hero.moveXY(30, 39)
hero.say(simon)
# Multiply Simonyi's number by Laszlo's to get Agata's number.
# Go to Agata and tell her her number.
aga = simon * las
hero.moveXY(43, 26)
hero.say(aga)



```

### THE WIZARD'S HAUNT

```Python
# Move to Zsofia and get the secret number from her.
hero.moveXY(18, 20)
zso = hero.findNearestFriend().getSecret()

# Divide Zsofia's number by 4 to get Mihaly's number.
# Move to Mihaly and say his magic number.
mih = zso / 4
hero.moveXY(30, 15)
hero.say(mih)

# Divide Mihaly's number by 5 to get Beata's number
# Move to Beata and say her magic number.
bea = mih / 5
hero.moveXY(42, 20)
hero.say(bea)


# Subtract Beata's number from Mihaly's to get Sandor's number.
# Move to Sandor and say his magic number.
san = mih - bea 
hero.moveXY(38, 37)
hero.say(san)


```

### THE WIZARD'S PLANE

```Python
# Move to Eszter and get the secret number from her.
hero.moveXY(16, 32)
esz = hero.findNearestFriend().getSecret()

# Multiply by 3 and subtract 2 to get Tamas's number.
# Remember to use parentheses to do calculations in the right order.
# Move to Tamas and say his magic number.
tam = (esz * 3) - 2
hero.moveXY(24, 28)
hero.say(tam)

# Subtract 1 and multiply by 4 to get Zsofi's number.
# Move to Zsofi and say her magic number.
zso = (tam - 1) * 4
hero.moveXY(32, 24)
hero.say(zso)
# Add Tamas's and Zsofi's numbers, then divide by 2 to get Istvan's number.
# Move to Istvan and say his magic number.
ist = (tam + zso) / 2
hero.moveXY(40, 20)
hero.say(ist)
# Add Tamas's and Zsofi's numbers. Subtract Istvan's number from Zsofi's. Multiply the two results to get Csilla's number.
# Move to Csilla and say her magic number.
csi = (tam + zso) * (zso - ist)
hero.moveXY(48, 16)
hero.say(csi)



```

### COINRUMBERS

```Python
# Follow the trail of coins to the red X at the exit.

while True:
    # This finds the nearest item.
    item = hero.findNearestItem()
    if item:
        # This stores the item's pos, or position in a variable.
        itemPosition = item.pos
        # Put the X and Y coordinates of the item into variables.
        itemX = itemPosition.x
        itemY = itemPosition.y
        # Now, use moveXY to move to itemX and itemY:
        hero.moveXY(itemX, itemY)



```

### WHITE RABIT

```Python
# Follow the lightstone to navigate the traps.

while True:
    item = hero.findNearestItem()
    if item:
        # Store the item's position in a new variable using item.pos:
        pos = item.pos
        # Store the X and Y coordinates using pos.x and pos.y:
        x = pos.x
        y = pos.y
        # Move to the coordinates using moveXY() and the X and Y variables:
        hero.moveXY(x, y)
        pass


```

### CHAMELEONS

```Python

# Ogres are disguised as coins or gems!

while True:
    enemy = hero.findNearestEnemy()
    # If you see an enemy - attack it:
    if enemy:
        hero.attack(enemy)
    item = hero.findNearestItem()
    # If you see a coin or a gem - move to it's X and Y position:
    if item:
        hero.moveXY(item.pos.x,  item.pos.y)


```

### BLIND DISTANCE

```Python
# Tell the wizard the distance to the coming ogres.

# This function finds the nearest enemy and returns the distance to it.
# If there is no enemy, the function returns 0.
def nearestEnemyDistance():
    enemy = hero.findNearestEnemy()
    result = 0
    if enemy:
        result = hero.distanceTo(enemy)
    return result

while True:
    # Call nearestEnemyDistance() and
    # save the result in the variable enemyDistance.
    enemyDistance = nearestEnemyDistance()
    # If the enemyDistance is greater than 0: 
    if enemyDistance > 0:
        # Say the value of enemyDistance variable.
        hero.say(enemyDistance)

```

### HIT AND FREEZE

```Python



```

### BURLBOLE GROVE

```Python
# Don't attack the burls!
# Functions can return a value.
# When a function is called, it will be equal to the value the function returns.

def shouldAttack(target):
	# return False if no target
    if not target:
        return False
	# return False if target.type == "burl"
    if target.type == "burl":
        return False
    # Otherwise, return True
    return True

while True:
    enemy = hero.findNearestEnemy()
    # Here we use shouldAttack() to decide if we should attack!
    # heroShouldAttack will be assigned the same value that shouldAttack() returns!
    heroShouldAttack = shouldAttack(enemy)
    if heroShouldAttack:
    	hero.attack(enemy)



```
### COIN HUNTER

```Python

# To make the training more interesting Senick poisoned you.
# While you aren't moving the poison is harmless.

# This function should check if a coin is closer than 20m.
def isCoinClose(coin):
    # Find the distance to the coin.
    distance = hero.distanceTo(coin)
    # If the distance is less than 20: 
    if distance < 20:
        # Return True
        return True
    # Else:
    else:
        # Return False
        return False
    pass

while True:
    item = hero.findNearestItem()
    if item:
        # If isCoinClose(item) returns true:
        if isCoinClose(item):
            hero.moveXY(item.pos.x, item.pos.y)


```
### SALTED EARTH

```Python

# Ogres are attacking a nearby settlement!
# Be careful, though, for the ogres have sown the ground with poison.
# Gather coins and defeat the ogres, but avoid the burls and poison!

while True:
    enemy = hero.findNearestEnemy()
    if enemy.type == "munchkin" or enemy.type == "thrower":
        hero.attack(enemy)
    item = hero.findNearestItem()
    # Check the item type to make sure the hero doesn't pick up poison!
    # Look for types: 'gem' and 'coin'
    if item.type != "poison":
        hero.moveXY(item.pos.x, item.pos.y)


```
需要对具体内容有所了解，不能仅仅获得就可以。获得就是走到那个位置去就可以。


### METAL DETECTOR

```Python

# The artillery uses coins as a target.
# You'll be the rangefinder for the artillery.

# Write the function.
def coinDistance():
    # Find the nearest coin,
    item = hero.findNearestItem()
    
    # If there is a coin, return the distance to it.
    if item:
        distance = hero.distanceTo(item)
        return distance
    # Else, return 0 (zero).
    else:
        return 0
    

while True:
    distance = coinDistance()
    if distance > 0:
        # Say the distance.
        hero.say(distance)
        pass


```
distance和item都得是进行确认过之后才能使用的变量，那么distance也要在item使用之后得到这个变量，毕竟得先if确认，确认过后可以得到这个变量内容。

但是跟下面这个比较却是在while True的情况下进行操作可能不需要这样的方式。

### STAR SHOWER

```Python

# Pick up coins only if they are closer than 20m.
# Pick up all gems.

while True:
    item = hero.findNearestItem()
    distance = hero.distanceTo(item)
    # If the item's type is "gem"
    # OR the distance to the item less than 20 meters:
    if item.type == "gem" or distance < 20:
        # Move to item's position.
        hero.moveXY(item.pos.x,  item.pos.y)


```
有可能出现无法生还但是可以多提交一次，问题并不明显。


### FOREST SHADOW

```Python
# Big ogres can't see you in the forest.
# Attack only the small ogres in the forest.
# Collect coins and gems only.
# Don't leave the forest and don't eat/drink anything.

while True:
    # Find the nearest enemy.
    # Attack it only if its type is "thrower" or "munchkin".
    enemy = hero.findNearestEnemy()
    distance1 = hero.distanceTo(enemy)
    if enemy.type == "thrower" or enemy.type == "munchkin" and distance1 < 20: 
        hero.attack(enemy)
    # Find the nearest item.
    # Collect it only if its type is "gem" or "coin".
    item = hero.findNearestItem()
    distance2 = hero.distanceTo(item)
    if item.type != "mushroom":
        if item.type == "gem" or item.type == "coin" and distance2 < 20:
            hero.moveXY(item.pos.x, item.pos.y)
    pass


```
注意，如果这时候判断是直接两个字符串名字带上or那么意味着明显这个判断是永远有效的，因为后者字符串不为空就意味着必然可以通过，而不是再用if条件去筛选，所以判断条件必须写完全。

### SPRING SUNDER

```Python
# Certain coins and gems attract lightning.
# The hero should only grab silver and blue gems.

while True:
    item = hero.findNearestItem()
    # A silver coin has a value of 2.
    # Collect if item.type is equal to "coin"
    # AND item.value is equal to 2.
    if item.type == "coin" and item.value == 2:
        hero.moveXY(item.pos.x, item.pos.y)
    # A blue gem has a value of 10.
    # Collect if item.type is equal to "gem"
    # AND item.value is equal to 10.
    if item.type == "gem" and item.value == 10:
        hero.moveXY(item.pos.x, item.pos.y)



```

### USUAL DAY

```Python
# Defeat munchkins, collect coins. Everything as usual.
# Use AND to check existence and type in one statement.

while True:
    enemy = hero.findNearestEnemy()
    # With AND, the type is only checked if enemy exists.
    if enemy and enemy.type == "munchkin":
        hero.attack(enemy)
    # Find the nearest item.
    item = hero.findNearestItem()
    
    # Collect item if it exists and its type is "coin".
    if item and item.type == "coin":
        hero.moveXY(item.pos.x, item.pos.y)



```
两个条件必须判断第一个过后才能说明第二个存在类型进行鉴定，这是题目的主旨。

### TELEPORT LASSO

```Python
# Our wizards teleport ogres from their camp here.
# They appear for a short period and they are stunned.
# Attack only weak and near ogres.

while True:
    enemy = hero.findNearestEnemy()
    if enemy:
        distance = hero.distanceTo(enemy)
        if  enemy.type == "munchkin" and distance < 20:
            hero.attack(enemy)
        # Then attack it.
            
# If enemy.type is "munchkin"
    # AND the distance to it is less than 20m



```
你就算是后面用到这个变量的类型，也得是嵌套在整体确认的if中才能实现，不然对于这个变量还是不能调用也不能用来判断。

### BRAWLER HUNT

```Python
# Don't worry about small and medium-sized ogres.
# Your targets are type "brawler".
# When a "brawler" is closer than 50m, fire artillery.

while True:
    # Find the nearest enemy and the distance to it.
    enemy = hero.findNearestEnemy()
    
    # If the enemy's type is "brawler"
    # AND the distance to it is less than 50 meters,
    # Then say "Fire!" to signal the artillery.
    if enemy :
        distance = hero.distanceTo(enemy)
        
        if enemy.type == "brawler" and distance < 50:
            hero.say("Fire!")
    pass

```
理论上可以连续将几个内容一起认定，但是distance还是得用到enemy，确认之后才能进行读取和判断。

### PASSING THROUGH

```Python
# Don't insult this tribe of peaceful ogres.

while True:
    item = hero.findNearestItem()
    if item:
        # If item.type IS NOT EQUAL TO "gem"
        if item.type != "gem":
            # Then follow your pet wolf.
            hero.moveXY(pet.pos.x, pet.pos.y)
        # Else:
        else:
            # Move to the gem's position.
            hero.moveXY(item.pos.x, item.pos.y)



```
宠物已经设定好了方向和位置，所以只要跟着走到相应的位置就好了。

### USEFUL COMPITITORS

```Python
# The coin field has been seeded with vials of deadly poison.
# Ogres are attacking, while their peons are trying to steal your coins!
# Attack the enemy only if the type is NOT equal to "peon".

while True:
    enemy = hero.findNearestEnemy()
    if enemy:
        if enemy.type != "peon":
            hero.attack(enemy)
    item = hero.findNearestItem()
    if item:
        # Gather the item only if the type is NOT equal to "poison".
        if item.type != "poison":
            hero.moveXY(item.pos.x, item.pos.y)
        pass



```
练习了一下不等于的用法。

### WONDERGLADE


```Python
# You need to collect several items.
# But, the burl wants the gems!
# Pick up all appearing items EXCEPT gems.

while True:a
    item = hero.findNearestItem()
    if item:
        # If item.type isn't equal to "gem":
        if item.type != "gem":
            
            # Move to the item's position.
            hero.moveXY(item.pos.x, item.pos.y)



```


### CURSED WONDERGLADE

```Python
# Wonderglade has changed since our last visit.
# Ogres cursed it and we should defeat them.
# The burl still is collecting gems, so don't touch them.
# Also don't attack the burl.

while True:
    # Find the nearest item.
    # Collect it (if it exists) only if its type isn't "gem".
    item = hero.findNearestItem()
    if item and item.type != "gem":
        hero.moveXY(item.pos.x, item.pos.y)
    
    # Find the nearest enemy.
    # Attack it if it exists and its type isn't "burl".
    enemy = hero.findNearestEnemy()
    if enemy and enemy.type != "burl":
        hero.attack(enemy)
    pass



```

### LOGICAL PATH


```Python
# Get two secret true/false values from the wizard.
hero.moveXY(14, 24)
secretA = hero.findNearestFriend().getSecretA()
secretB = hero.findNearestFriend().getSecretB()

# If BOTH secretA and secretB are true, take the high path; otherwise, take the low path.
# Check the guide for notes on how to write logical expressions.
secretC = secretA and secretB
if secretC:
    hero.moveXY(20, 33)
else:
    hero.moveXY(20, 15)
hero.moveXY(26, 24)

# If EITHER secretA or secretB is true, take the high path.
if secretA or secretB:
    hero.moveXY(32, 33)
else:
    hero.moveXY(32, 15)
hero.moveXY(38, 24)

# If secretB is NOT true, take the high path.
if not secretB:
    hero.moveXY(44, 33)
else:
    hero.moveXY(44, 15)
hero.moveXY(50, 23)



```

### LOGICAL CIRCLE

```Python
# Move to the wizard and get their secret values.
hero.moveXY(20, 24)
secretA = hero.findNearestFriend().getSecretA()
secretB = hero.findNearestFriend().getSecretB()
secretC = hero.findNearestFriend().getSecretC()

# If ALL three values are true, take the high path. Otherwise, take the low path.
secretD = secretA and secretB and secretC
if secretD:
    hero.moveXY(30, 33)
else:
    hero.moveXY(30, 15)

# If ANY of the three values are true, take the left path. Otherwise, go right.
secretE = secretA or secretB or secretC
if secretE:
    hero.moveXY(20, 24)
else:
    hero.moveXY(40, 24)

# If ALL five values are true, take the high path. Otherwise, take the low path.
secretF = secretA and secretB and secretC and secretD and secretE
if secretF:
    hero.moveXY(30, 33)
else:
    hero.moveXY(30, 15)



```
### LOGICAL CONCLUSION

```Python

# Move to Eszter and get three secret values from her.
hero.moveXY(24, 16)
secretA = hero.findNearestFriend().getSecretA()
secretB = hero.findNearestFriend().getSecretB()
secretC = hero.findNearestFriend().getSecretC()

# Say "TRUE" to Tamas if A AND B are true, OR if C is true. Otherwise, say "FALSE."
# Remember to use parentheses to do your logic in the proper order.
tam = (secretA and secretB) or secretC
hero.moveXY(19, 26)
hero.say(tam)

# Say "TRUE" to Zsofi if A OR B is true, AND if C is true. Otherwise, say "FALSE."
zso = (secretA or secretB) and secretC
hero.moveXY(26, 36)
hero.say(zso)

# Say "TRUE" to Istvan if A OR C is true, AND if B OR C is true. Otherwise, say "FALSE."
ist = (secretA or secretC) and (secretC or secretB)
hero.moveXY(37, 34)
hero.say(ist)

# Say "TRUE" to Csilla if A AND B are true, OR if B is true AND C is NOT true. Otherwise, say "FALSE."
csi = (secretA and secretB) or (secretB and not secretC)
hero.moveXY(40, 22)
hero.say(csi)


```
由于最后说明实际运行中还是检查出来一个拼写错误，证明运行和实际提交还是有一定区别的，要真的整理好内容。

### RETURN TO THORNBUSH FARM
```Python

# The function maybeBuildTrap defines TWO parameters!
def maybeBuildTrap(x, y):
    # Use x and y as the coordinates to move to.
    hero.moveXY(x, y)
    enemy = hero.findNearestEnemy()
    if enemy:
        pass
        # Use buildXY to build a "fire-trap" at the given x and y.
        hero.buildXY("fire-trap", x, y)
while True:
    # This calls maybeBuildTrap, with the coordinates of the top entrance.
    maybeBuildTrap(43, 50)
    
    # Now use maybeBuildTrap at the left entrance!
    maybeBuildTrap(25, 34)
    # Now use maybeBuildTrap at the bottom entrance!
    maybeBuildTrap(43, 20)
    


```

### CLOSED CROSSROAD 
```Python
# Only build if you see an enemy.

# The function defines THREE parameters.
def maybeBuildSomething(buildType, x, y):
    # Move to the position specified by x and y parameters.
    hero.moveXY(x, y)
    # Find the nearest enemy.
    enemy = hero.findNearestEnemy()
    
    # If there is an enemy
    if enemy:
        # then use buildXY with buildType, x, and y
        hero.buildXY(buildType, x, y)
    pass
    
while True:
    # Call maybeBuildSomething with "fire-trap" and the coordinates of the bottom X.
    maybeBuildSomething("fire-trap", 40, 20)
    # Call maybeBuildSomething, with "fence" at the left X!
    maybeBuildSomething("fence", 26, 34)
    # Call maybeBuildSomething with "fire-trap" at the top X!
    maybeBuildSomething("fire-trap", 40, 50)
    # Call maybeBuildSomething with "fence" at the right X!
    maybeBuildSomething("fence", 54, 34)


```

### GREED TRAPS
```Python
# Patrol and place traps ONLY if you see a coin.

# Write this function.
def maybeBuildTrap(x, y):
    # Move to the given x,y postion
    hero.moveXY(x, y)
    # Search a coin and  if you see it, build a "fire-trap"
    items = hero.findNearestItem()
    if items:
        if items.type == "coin":
            hero.buildXY("fire-trap", x, y)
    pass

while True:
    # Call maybeBuildTrap for the top left passage.
    maybeBuildTrap(12, 56)
    # Now for the top right passage.
    maybeBuildTrap(68, 56)
    # Now for the bottom right passage.
    maybeBuildTrap(68, 12)
    # Now for the bottom left passage.
    maybeBuildTrap(12, 12)
```

### COINUCOPIA
```Python
# Press Submit when you are ready to place flags.
# Flag buttons appear in the lower left after pressing Submit.
while True:
    flag = hero.findFlag()
    if flag:
        hero.pickUpFlag(flag)
    else:
        hero.say("Place a flag for me to go to.")
```

### RETURN TO THORNBUSH FARM A
```Python
# The function maybeBuildTrap defines TWO parameters!
def maybeBuildTrap(x, y):
    # Use x and y as the coordinates to move to.
    hero.moveXY(x, y)
    enemy = hero.findNearestEnemy()
    if enemy:
        pass
        # Use buildXY to build a "fire-trap" at the given x and y.
        hero.buildXY("fire-trap", x, y)
while True:
    # This calls maybeBuildTrap, with the coordinates of the left entrance.
    maybeBuildTrap(20, 34)
    
    # Now use maybeBuildTrap at the bottom entrance!
    maybeBuildTrap(38, 20)
    # Now use maybeBuildTrap at the right entrance!
    maybeBuildTrap(56, 34)
```

### COPPER MEADOWS
```Python
# Collect all the coins in each meadow.
# Use flags to move between meadows.
# Press Submit when you are ready to place flags.

while True:
    flag = hero.findFlag()
    if flag:
        pass  # pass is a placeholder, it has no effect.
        # Pick up the flag.
        hero.pickUpFlag(flag)
    else:
        # Automatically move to the nearest item you see.
        item = hero.findNearestItem()
        if item:
            position = item.pos
            x = position.x
            y = position.y
            hero.moveXY(x, y)

```

### RETURN TO THORNBUSH FARM B
```Python
# The function maybeBuildTrap defines TWO parameters!
def maybeBuildTrap(x, y):
    # Use x and y as the coordinates to move to.
    hero.moveXY(x, y)
    enemy = hero.findNearestEnemy()
    if enemy:
        pass
        # Use buildXY to build a "fire-trap" at the given x and y.
        hero.buildXY("fire-trap", x, y)
while True:
    # This calls maybeBuildTrap, with the coordinates of the bottom entrance.
    maybeBuildTrap(38, 20)
    
    # Now use maybeBuildTrap at the right entrance!
    maybeBuildTrap(56, 34)
    # Now use maybeBuildTrap at the top entrance!
    maybeBuildTrap(38, 48)

```

### DROP THE FLAG
```Python

# Put flags where you want to build traps.
# When you're not building traps, pick up coins!

while True:
    flag = hero.findFlag()
    if flag:
        # How do we get flagX and flagY from the flag's pos?
        # (Look below at how to get x and y from items.)
        hero.buildXY("fire-trap", flagX, flagY)
        hero.pickUpFlag(flag)
    else:
        item = hero.findNearestItem()
        if item:
            itemPos = item.pos
            itemX = itemPos.x
            itemY = itemPos.y
            hero.moveXY(itemX, itemY)


```

### BACKWOODS TREASURE
```Python
# Collect 100 gold from two or three groves.
# If you win, it gets harder (and more rewarding).
# If you lose, you must wait a day before you can resubmit.
# Remember, each submission gets a new random seed.

def getcoinAfterkillenemy():
    enemy = hero.findNearestEnemy()
    item = hero.findNearestItem()
    
    if enemy:
        hero.attack(enemy)
    else:
        if item:
            hero.moveXY(item.pos.x, item.pos.y)

while True:
    getcoinAfterkillenemy()


```

### DEADLY PURSUIT
```Python
# Grab all the coins and use flags to build traps behind
# you to deal with those ogres.

while True:
    flag = hero.findFlag()
    item = hero.findNearestItem()
    if flag:
        hero.moveXY(flag.pos.x, flag.pos.y)
        hero.buildXY("fire-trap", flag.pos.x, flag.pos.y)
        hero.pickUpFlag(flag)
    elif item:
        hero.moveXY(item.pos.x, item.pos.y)
      
```
此关不能仅仅是测试，直接就开始必须要进行互动了，必须要不停点上旗子让英雄过去设定陷阱。

### MIND THE TRAP

```Python
# If you try to attack a distant enemy, your hero will charge toward it, ignoring all flags.
# You'll need to make sure you only attack enemies who are close to you!

while True:
    flag = hero.findFlag()
    enemy = hero.findNearestEnemy()
    
    if flag:
        # Pick up the flag.
        hero.pickUpFlag(flag)
        hero.say("I should pick up the flag.")
    elif enemy:
        # Only attack if the enemy distance is < 10 meters
        distance = hero.distanceTo(enemy)
        if distance < 10:
            hero.attack(enemy)
```

### SINGAL CORPOSE
```Python
# You can use flags to choose different tactics.
# In this level, the green flag will mean you want to move to the flag.
# The black flag means you want to cleave at the flag.
# The doctor will heal you at the Red X

while True:
    green = hero.findFlag("green")
    black = hero.findFlag("black")
    nearest = hero.findNearestEnemy()
    
    if green:
        hero.pickUpFlag(green)
    elif black and hero.isReady("cleave"):
        hero.pickUpFlag(black)
        # Cleave!
        hero.cleave(nearest)
    elif nearest and hero.distanceTo(nearest) < 10:
        # Attack!
        hero.attack(nearest)
        pass

```

### REACH FORAGER
```Python
# Use "if" and "else if" to handle any situation.
# Put it all together to defeat enemies and pick up coins!
# Make sure you bought great armor from the item shop! 400 health recommended.

while True:
    flag = hero.findFlag()
    enemy = hero.findNearestEnemy()
    item = hero.findNearestItem()
    if flag:
        # What happens when I find a flag?
        hero.pickUpFlag(flag)
    elif enemy:
        # What happens when I find an enemy?
        hero.attack(enemy)
    elif item:
        # What happens when I find an item?
        hero.moveXY(item.pos.x, item.pos.y)
        

```

### SIEGE OF
```Python
# Help your friends beat the minions that Thoktar sends against you.
# You'll need great equipment and strategy to win.
# Flags might help, but it's up to you–be creative!
# There is a doctor behind the fence. Move to the X to get healed!
while True:
    enemy = hero.findNearestEnemy()
    
    flag = hero.findFlag()
    if flag:
        hero.pickUpFlag(flag)
    else:
        if enemy:
            hero.attack(enemy)

```
## STONE

### THE DUNES
```Python
# Collect coins. Ignore "sand-yak"s and "burl"s.
while True:
    enemy = hero.findNearestEnemy()
    item = hero.findNearestItem()
    if enemy:
        if enemy.type == "sand-yak" or enemy.type == "burl":
            # Don't attack! Collect coins.
            hero.moveXY(item.pos.x, item.pos.y)
            pass
        else:
            # Else, attack.
            hero.attack(enemy)
            pass
        
    elif item:
        # Collect coins: move to item's position.
        hero.moveXY(item.pos.x, item.pos.y)
        pass
    else:
        hero.moveXY(41, 31)
```

### THE MIGHTY SAND YAK
```Python
# Let yaks get close, then move 10m right to dodge.
# Dodge 4 yaks to complete the level.

while True:
    # Get hero's current x and y position.
    x = hero.pos.x
    y = hero.pos.y
    
    # Find the nearest yak.
    yak = hero.findNearestEnemy()
    
    # If the distanceTo the yak is less than 10:
    if hero.distanceTo(yak) < 10:
        # To move right, add 10 to hero's x position.
        x += 10
        # Use moveXY(x, y) to move!
        hero.moveXY(x, y)
        pass

```


```Python



```


```Python



```


```Python



```


```Python



```


```Python



```


```Python



```


```Python



```


```Python



```


```Python



```


```Python



```


```Python



```


```Python



```


```Python



```


```Python



```
