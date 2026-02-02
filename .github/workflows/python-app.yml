import pygame
import sys
import random

pygame.init()

width, height = 640, 480 
window = pygame.display.set_mode((width, height))
pygame.display.set_caption("Snake and Apple")

font = pygame.font.SysFont("comicsansms",40)

#colors
green = (0, 255, 0)
white = (255, 255, 255)
black = (0, 0, 0)
red = (255,0, 0)

#parameters
x = width // 2
y = height // 2
dx = 0
dy = 0
BLOCK = 20

snakeList=[]
snakeLength=1

x_apple= random.randrange(0,width-BLOCK,BLOCK)
y_apple= random.randrange(0,height-BLOCK,BLOCK)

#importing apple img and scaling it
apple = pygame.image.load("apple.png")
apple = pygame.transform.scale(apple, (BLOCK, BLOCK))

#background
background = pygame.image.load("bgimage.jpg")
background = pygame.transform.scale(background, (width, height))

#draws snake
def drawSnake(snakeList):
    for body in snakeList:
        pygame.draw.rect(window,green,(body[0],body[1],BLOCK,BLOCK))

#shows score on top left
def scoreShow(score):
    text = font.render(f"Score: {score}", True, white)
    window.blit(text, (10, 10))


while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

        if event.type == pygame.KEYDOWN:

#moves snake to left when left arrow key is pressed
            if event.key == pygame.K_LEFT:
                dx = -BLOCK
                dy = 0

#moves snake to right when right arrow key is pressed
            if event.key == pygame.K_RIGHT:
                dx = BLOCK
                dy = 0

#moves snake to north when up arrow key is pressed
            if event.key == pygame.K_UP:
                dx = 0
                dy = -BLOCK

#moves snake to south when down arrow key is pressed
            if event.key == pygame.K_DOWN:
                dx = 0
                dy = BLOCK

#ends the game if snake touches screen edges 
    if  x<0 or x>=width or y<0 or y>=height:
        break


    #snake position
    x += dx
    y += dy

#adds snake head every time it moves
    snakeList.append([x,y])

#checks that snake isnt longer than it should be
    while len(snakeList) > snakeLength:
        del snakeList[0]

#checks the snake length except head
    for body in snakeList[:-1]:
        if body == [x, y]: #if head is at its place
            pygame.quit()
            sys.exit() #ends game if snake touches itself

    
#adds block to snake when it eats apple
#spawns apple at a random place
    if x== x_apple and y == y_apple:
        snakeLength+= 1
        x_apple= random.randrange(0,width-BLOCK,BLOCK)
        y_apple= random.randrange(0,height-BLOCK,BLOCK)

    #draw bg
    window.blit(background, (0, 0))

    #draw apple
    window.blit(apple, (x_apple,y_apple))
    #pygame.draw.rect(window,red,(x_apple,y_apple,BLOCK,BLOCK))
    #draw snake
    drawSnake(snakeList)

    scoreShow(snakeLength - 1)

    pygame.display.update()
    fpsClock = pygame.time.Clock()
    fpsClock.tick(10)

pygame.quit()
sys.exit()
