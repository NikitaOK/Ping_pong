from pygame import *

class GameSprite(sprite.Sprite):
    # конструктор класса
    def __init__(self, image_name, x, y, speed, wight, height):
        super().__init__()

        self.image = transform.scale(image.load(image_name), (wight, height))
        self.speed = speed
 
        self.rect = self.image.get_rect()
        self.rect.x = x
        self.rect.y = y

    def reset(self):
        window.blit(self.image, (self.rect.x, self.rect.y))


back = (200, 255, 255) # цвет фона (background)
win_width = 600
win_height = 500
window = display.set_mode((win_width, win_height))
window.fill(back)


game = True
finish = False
clock = time.Clock()
FPS = 60

while game:
    for e in event.get():
        if e.type == QUIT:
            game = False

    display.update()
    clock.tick(FPS)
