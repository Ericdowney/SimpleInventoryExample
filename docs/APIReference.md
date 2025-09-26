# API Reference

This document provides a reference for all public classes, structs, properties, functions, and events exposed by the **SimpleInventory** plugin.

## **Modules**

- **SimpleInventory**: Runtime module containing core inventory logic.
- **SimpleInventoryEditor**: Editor module providing UI for debugging inventories.
- **SimpleInventoryTests**: Editor test module with automated unit tests.

## **Classes**

### **USimpleInventory**

Represents a single inventory instance.

#### Events

* `FOnInventoryChangeDelegate OnChangeEvent` – Broadcast when the inventory changes.

#### Properties

* `FName InventoryID`: Unique identifier for the inventory.
* `FText InventoryName`: Localized display name.
* `FText InventoryDescription`: Localized description.
* `int32 MaxSlots`: Maximum number of slots allowed.

#### Public Functions

* `FSimpleInventoryStorage GetStorage() const`
* `USimpleInventorySlot* FindSlotByItemID(FName InItemID) const`
* `TArray<USimpleInventorySlot*> FindAllSlotsByItemID(FName InItemID) const`
* `int32 GetTotalQuantityByItemID(FName InItemID) const`
* `bool HasFreeSlot() const`
* `USimpleInventorySlot* FindSlotByPredicate(FSimpleInventorySlotPredicate InPredicate) const`
* `TArray<USimpleInventorySlot*> FindSlotsByPredicate(FSimpleInventorySlotPredicate InPredicate) const`
* `bool SplitSlot(const int32 InSlotIndex, const int32 InQuantityToSplit, bool bBroadcastEvent = true)`
* `bool MergeSlots(int32 InSourceSlotIndex, int32 InTargetSlotIndex, bool bBroadcastEvent = true)`
* `bool CanAddItems(FSimpleInventoryItem InItem, const int32 InQuantity) const`
* `void AddItem(FSimpleInventoryItem InItem, const int32 InQuantity, bool bBroadcastEvent = true)`
* `void AddItems(TArray<FSimpleInventoryItem> InItems, bool bBroadcastEvent = true)`
* `void RemoveSlotAtIndex(const int32 InIndex, bool bBroadcastEvent = true)`
* `void RemoveItemAtIndex(const int32 InIndex, const int32 InQuantity, bool bBroadcastEvent = true)`
* `void RemoveItems(const TArray<FSimpleInventoryItem> InItems, bool bBroadcastEvent = true)`
* `void Clear(bool bBroadcastEvent = true)`
* `int32 GetLength() const`
* `int32 GetMaxSize() const`
* `USimpleInventorySlot* GetSlot(const int32 InIndex) const`
* `TArray<USimpleInventorySlot*> GetSlots() const`
* `bool HasItem(const FName InItemID, const int32 InQuantity)`
* `bool HasItemWithExactCount(const FName InItemID, const int32 InQuantity)`
* `void ForceOnChange() const`
* `void InflateFromStorage(FSimpleInventoryStorage Storage)`
* `void InflateFromDefinition(FSimpleInventoryDefinition Definition)`

### **USimpleInventoryComponent**

An `ActorComponent` wrapper for embedding and managing an inventory within an actor.

#### Events

* `FOnInventoryChangeDelegate OnChangeEvent`

#### Properties

* `FName DefaultInventoryID`
* `FText DefaultInventoryName`
* `FText DefaultInventoryDescription`
* `int32 DefaultMaxSlots`

#### Public Functions

* `FName GetInventoryID() const`
* `FText GetInventoryName() const`
* `FText GetInventoryDescription() const`
* `int32 GetMaxSlots() const`
* `void SetMaxSlots(int32 InMaxSlots)`
* `FSimpleInventoryStorage GetStorage() const`
* `USimpleInventorySlot* FindSlotByItemID(FName InItemID) const`
* `TArray<USimpleInventorySlot*> FindAllSlotsByItemID(FName InItemID) const`
* `int32 GetTotalQuantityByItemID(FName InItemID) const`
* `bool HasFreeSlot() const`
* `USimpleInventorySlot* FindSlotByPredicate(FSimpleInventorySlotPredicate InPredicate) const`
* `TArray<USimpleInventorySlot*> FindSlotsByPredicate(FSimpleInventorySlotPredicate InPredicate) const`
* `bool SplitSlot(const int32 InSlotIndex, const int32 InQuantityToSplit, bool bBroadcastEvent = true)`
* `bool MergeSlots(int32 InSourceSlotIndex, int32 InTargetSlotIndex, bool bBroadcastEvent = true)`
* `bool CanAddItems(FSimpleInventoryItem InItem, const int32 InQuantity) const`
* `void AddItem(FSimpleInventoryItem InItem, const int32 InQuantity, bool bBroadcastEvent = true)`
* `void AddItems(TArray<FSimpleInventoryItem> InItems, bool bBroadcastEvent = true)`
* `void RemoveSlotAtIndex(const int32 InIndex, bool bBroadcastEvent = true)`
* `void RemoveItemAtIndex(const int32 InIndex, const int32 InQuantity, bool bBroadcastEvent = true)`
* `void RemoveItems(const TArray<FSimpleInventoryItem> InItems, bool bBroadcastEvent = true)`
* `void Clear(bool bBroadcastEvent = true)`
* `int32 GetLength() const`
* `int32 GetMaxSize() const`
* `USimpleInventorySlot* GetSlot(const int32 InIndex) const`
* `TArray<USimpleInventorySlot*> GetSlots() const`
* `bool HasItem(const FName InItemID, const int32 InQuantity)`
* `bool HasItemWithExactCount(const FName InItemID, const int32 InQuantity)`
* `void ForceOnChange() const`
* `void InflateFromStorage(FSimpleInventoryStorage Storage)`

### **USimpleInventorySubsystem**

Global subsystem for managing multiple inventories.

#### Events

* `FOnInventoryChangeDelegate OnChangeEvent`

#### Properties

* `TMap<FName, USimpleInventory*> InventoryMap`

#### Public Functions

* `FSimpleInventorySubsystemStorage GetStorage() const`
* `TArray<USimpleInventory*> GetAllInventories() const`
* `USimpleInventory* GetInventory(FName InInventoryID) const`
* `USimpleInventorySlot* FindSlotByItemID(FName InInventoryID, FName InItemID) const`
* `TArray<USimpleInventorySlot*> FindAllSlotsByItemID(FName InInventoryID, FName InItemID) const`
* `int32 GetTotalQuantityByItemID(FName InInventoryID, FName InItemID) const`
* `bool HasFreeSlot(FName InInventoryID) const`
* `USimpleInventorySlot* FindSlotByPredicate(FName InInventoryID, FSimpleInventorySlotPredicate InPredicate) const`
* `TArray<USimpleInventorySlot*> FindSlotsByPredicate(FName InInventoryID, FSimpleInventorySlotPredicate InPredicate) const`
* `bool SplitSlot(FName InInventoryID, const int32 InSlotIndex, const int32 InQuantityToSplit, bool bBroadcastEvent = true)`
* `bool MergeSlots(FName InInventoryID, int32 InSourceSlotIndex, int32 InTargetSlotIndex, bool bBroadcastEvent = true)`
* `bool CanAddItems(FName InInventoryID, FSimpleInventoryItem InItem, const int32 InQuantity) const`
* `void AddItem(FName InInventoryID, FSimpleInventoryItem InItem, const int32 InQuantity, bool bBroadcastEvent = true)`
* `void AddItems(FName InInventoryID, TArray<FSimpleInventoryItem> InItems, bool bBroadcastEvent = true)`
* `void RemoveSlotAtIndex(FName InInventoryID, const int32 InIndex, bool bBroadcastEvent = true)`
* `void RemoveItemAtIndex(FName InInventoryID, const int32 InIndex, const int32 InQuantity, bool bBroadcastEvent = true)`
* `void RemoveItems(FName InInventoryID, const TArray<FSimpleInventoryItem> InItems, bool bBroadcastEvent = true)`
* `void Clear(FName InInventoryID, bool bBroadcastEvent = true)`
* `void ClearAll(bool bBroadcastEvent = true)`
* `int32 GetLength(FName InInventoryID) const`
* `int32 GetMaxSize(FName InInventoryID) const`
* `USimpleInventorySlot* GetSlot(FName InInventoryID, const int32 InIndex) const`
* `TArray<USimpleInventorySlot*> GetSlots(FName InInventoryID) const`
* `bool HasItem(FName InInventoryID, const FName InItemID, const int32 InQuantity)`
* `bool HasItemWithExactCount(FName InInventoryID, const FName InItemID, const int32 InQuantity)`
* `void ForceOnChange(FName InInventoryID) const`
* `void RegisterInventoryDefinition(USimpleInventorySubsystemDefinition* Definition)`
* `void InflateFromStorage(const FSimpleInventorySubsystemStorage Storage)`

## **Structs**

### `FSimpleInventoryItem`

Represents an inventory item.

* `FName ItemID`
* `FText ItemName`
* `FText ItemDescription`
* `bool bIsStackable`
* `int32 StackSize`
* `FInstancedStruct ItemMetadata`

### `FSimpleInventorySlotStorage`

Represents a single slot's storage state.

* `FSimpleInventoryItem StoredItem`
* `int32 Quantity`

### `FSimpleInventoryStorage`

Represents the full storage state of an inventory.

* `FName InventoryID`
* `FText InventoryName`
* `FText InventoryDescription`
* `int32 MaxSlots`
* `TArray<FSimpleInventorySlotStorage> StoredSlots`

### `FSimpleInventoryDefinition`

Defines the initial configuration of an inventory.

* `FName InventoryID`
* `FText InventoryName`
* `FText InventoryDescription`
* `int32 MaxSlots`

### `FSimpleInventorySubsystemStorage`

Represents the entire subsystem state for persistence.

* `TArray<FSimpleInventoryStorage> Inventories`

### `FSimpleInventorySlotPredicate`

Used for filtering slots during searches.

* `bool bRequiresItemID`
* `FName ItemID`
* `bool bOnlyStackable`
* `bool bRequiresMinQuantity`
* `int32 MinQuantity`
* `bool bRequiresMaxQuantity`
* `int32 MaxQuantity`

## **Enums**

### `ESimpleInventoryChangeType`

Defines the type of change event fired when an inventory changes.

* `Addition` – Items were added to the inventory.
* `Removal` – Items were removed from the inventory.
* `MultiRemoval` – Multiple items were removed at once.
* `Split` – A slot was split.
* `Merge` – Two slots were merged.
* `Full` – Inventory was full when trying to add items.
* `Clear` – Inventory was cleared.
* `Force` – Force broadcast of a change event. Useful for synchronizing UI even if a change has not occurred.

## **Data Assets**

### **USimpleInventorySubsystemDefinition**

Defines a collection of inventories to be registered in the subsystem.

#### Properties

* `TArray<FSimpleInventoryDefinition> InventoryDefinitions`
