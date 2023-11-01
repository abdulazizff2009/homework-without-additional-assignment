import java.util.Random;

// Класс босса
class Boss {
    int health;
    int damage;

    public Boss() {
        health = 500;
        damage = 50;
    }

    public void takeDamage(int damage) {
        health -= damage;
    }
}

// Класс Golem
class Golem extends Hero {
    public Golem() {
        super(200, 30, "ROCK SHIELD");
    }

    @Override
    public void applySuperAbility(Boss boss) {
        int bossDamage = boss.damage;
        int golemDamage = damage + bossDamage / 2;
        boss.takeDamage(bossDamage);
        boss.takeDamage(golemDamage);
        System.out.println("Golem применил суперспособность " + superAbilityType);
    }
}

// Класс Magic
class Magic extends Hero {
    private int attackIncrease;

    public Magic() {
        super(100, 40, "MAGIC BOOST");
        attackIncrease = 10;
    }

    @Override
    public void applySuperAbility(Boss boss) {
        attack += attackIncrease;
        System.out.println("Magic применил суперспособность " + superAbilityType);
    }
}

// Класс Warrior
class Warrior extends Hero {
    public Warrior() {
        super(150, 50, "CRITICAL STRIKE");
    }

    @Override
    public void applySuperAbility(Boss boss) {
        int criticalMultiplier = new Random().nextInt(3) + 2;
        int warriorDamage = damage * criticalMultiplier;
        boss.takeDamage(warriorDamage);
        System.out.println("Warrior применил суперспособность " + superAbilityType);
    }
}

// Остальные классы героев остаются без изменений
