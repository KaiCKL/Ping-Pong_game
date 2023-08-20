# Ping-Pong_game
The repository contains a prototype of the Ping-Pong game.It is a multiplayer game.The game was implemented in Python using the Pygame library.Player 1 controls the left paddle using the keys.Player 2 controls the right paddle using the keys.

from pygame import *

back = (200, 255, 255)
win_width = 600
win_height = 500
window = display.set_mode((win_width, win_height))
window.fill(back)

clock = time.Clock()
FPS = 60
game = True

while game:
    for e in event.get():
        if e.type == QUIT:
            game = False

    display.update()
    clock.tick(FPS)

#left paddle
def update_1(self):
    keys = key.get_pressed()
    if keys[K_w] and self.rect.y > 5:
        self.rect.y -= self.speed
    if keys[K_s] and self.rect.y > 5:
        self.rect.y += self.speed

#right paddle
def update_r(self):
    keys = key.get_pressed()
    if keys[K_UP] and self.rect.y > 5:
        self.rect.y -= self.speed
    if keys[K_DOWN] and self.rect.y > 5:
        self.rect.y += self.speed
