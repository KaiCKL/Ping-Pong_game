# Ping-Pong_game
The repository contains a prototype of the Ping-Pong game.It is a multiplayer game.The game was implemented in Python using the Pygame library.Player 1 controls the left paddle using the keys.Player 2 controls the right paddle using the keys.

from pygame import *

from pygame import *

win_width = 600
win_height = 500
back = (200, 255, 255) 

background_image = image.load("fback.jpg")
background_image = transform.scale(background_image, (win_width, win_height))

img_paddle1 = 'fknight.png'
img_paddle2 = 'fknight2.png'
img_ball = 'fball.png'
img_background = 'fback.jpg'

font.init()
font = font.Font(None, 35)
lose1 = font.render('PLAYER 1 LOSES!',True, (180, 0, 0))
lose2 = font.render('PLAYER 2 LOSES!',True, (180, 0, 0))

class GameSprite(sprite.Sprite):
    def __init__(self, player_image, player_x, player_y, size_x, size_y, player_speed):
        sprite.Sprite.__init__(self)

        self.image = transform.scale(image.load(player_image), (size_x, size_y))
        self.speed = player_speed
        self.rect= self.image.get_rect()
        self.rect.x = player_x
        self.rect.y = player_y

class Player(GameSprite):
    def paddle1(self):
        keys = key.get_pressed()
        if keys[K_w] and self.rect.y > 10:
            self.rect.y -= self.speed
        if keys[K_s] and self.rect.y < win_height - 100:
            self.rect.y += self.speed

    def paddle2(self):
        keys = key.get_pressed()
        if keys[K_UP] and self.rect.y > 10:
            self.rect.y -= self.speed
        if keys[K_DOWN] and self.rect.y < win_height - 100:
            self.rect.y += self.speed

speed_x = 3
speed_y = 3

player_L = Player(img_paddle1,30, 200, 60, 90, 10)
player_R = Player(img_paddle2,820, 200, 60, 90, 10)
ball = GameSprite('fball.png', 200, 200, 50, 50, 50)

clock = time.Clock()
FPS = 60
game = True
game_over = False

while game:
    for e in event.get():
        if e.type == QUIT:
            game = False

    if finish != True:
        ball.rect.x += speed_x
        ball.rect.y += speed.y

    if ball.rect.y > win_height-50 or ball.rect.y < 0:
        speed_y *= -1

    if ball.rect.x < 0:
        finish = True
        window.blit(lose1, (200, 200))
        game_over = True

    if ball.rect.x > win_width:
        window.blit(lose2, (200, 200))
        game_over = True

    if game_over != True:
        window.fill(back)
        player_L.update_paddle1()
        player_R.update_paddle2()

    if sprite.collide_rect(player_L, ball) or sprite.collide_rect(player_R, ball):
        speed_x *= -1
        speed_y *= -1
        
player_L.reset()
player_R.reset()
ball.reset()

display.update()
clock.tick(FPS)
    
