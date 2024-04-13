import random

class Player:
    def __init__(self, name):
        self.name = name
        self.hp = 100
        self.attack = 10
        self.defense = 5

    def take_damage(self, damage):
        self.hp -= damage

    def is_alive(self):
        return self.hp > 0

class Enemy:
    def __init__(self, name, hp, attack):
        self.name = name
        self.hp = hp
        self.attack = attack

    def take_damage(self, damage):
        self.hp -= damage

    def is_alive(self):
        return self.hp > 0

def battle(player, enemy):
    print(f"A wild {enemy.name} appears!")
    while player.is_alive() and enemy.is_alive():
        print(f"{player.name}'s HP: {player.hp}")
        print(f"{enemy.name}'s HP: {enemy.hp}")
        print("1. Attack")
        print("2. Run")
        choice = input("Choose your action: ")
        if choice == "1":
            player_attack = random.randint(0, player.attack)
            enemy_attack = random.randint(0, enemy.attack)
            player.take_damage(enemy_attack)
            enemy.take_damage(player_attack)
            print(f"You dealt {player_attack} damage to {enemy.name}")
            print(f"{enemy.name} dealt {enemy_attack} damage to {player.name}")
        elif choice == "2":
            print("You ran away from the battle.")
            break
    if player.is_alive():
        print("You won the battle!")
    else:
        print("Game over. You were defeated.")

def main():
    player_name = input("Enter your name: ")
    player = Player(player_name)
    enemy = Enemy("Goblin", 50, 8) # Example enemy
    battle(player, enemy)

if __name__ == "__main__":
    main()
