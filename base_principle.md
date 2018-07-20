# Основные принципы

## SOLID принципы для классов
* SRP
    - The Single Responsibility Principle
        * A class should have one, and only one, reason to change.
* OCP
    - The Open Closed Principle
        * You should be able to extend a classes behavior, without modifying it.
* LSP
    - The Liskov Substitution Principle
        * Derived classes must be substitutable for their base classes.
* ISP
    - The Interface Segregation Principle
        * Make fine grained interfaces that are client specific.
* DIP
    - The Dependency Inversion Principle
        * Depend on abstractions, not on concretions.

## Принципы для компонентов
* REP
    - The Release Reuse Equivalency Principle
        * The granule of reuse is the granule of release.
* CCP
    - The Common Closure Principle
        * Classes that change together are packaged together.
* CRP
    - The Common Reuse Principle
        * Classes that are used together are packaged together.

## Принципы для архитектуры
* ADP
    - The Acyclic Dependencies Principle
        * The dependency graph of packages must have no cycles.
* SDP
    - The Stable Dependencies Principle
        * Depend in the direction of stability.
* SAP
    - The Stable Abstractions Principle
        * Abstractness increases with stability.

## Общие принципы
* DRY - Don't Repeat Yourself
* YAGNI - You Ain't Gonna Need It
* FNFD - Function Name - Function Do
* PMPP - Protected Methods: Private Properties
