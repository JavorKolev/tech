# Warehouse policies

Warehouse policies is a hierarchical system for applying policies to warehouse operations. 


# Policy kind
Warehouse policies have diferent kinds/types which specify what the actual action of the policy is. 

The list of the policy kinds is system predifined.  

| Kind | Details |
| :------ | :----------------- |
| AllowProductChange   | **Description:** Allows execution with a different lot than the ordered. <br/><br/> **Possible values:** true, false <br/><br/> **Action:** Used in the Orders execution in the WMS Worker app. <br/><br/> If there is an applicable policy to the line and its value is „false“, then the Lot (if any) which was initially specified in the Warehouse Order Line cannot be changed during the line execution. <br/><br/> If the user tries to enter a different lot, the app will make a negative sound and will display a pop message: _“Lot change is not allowed. Please select the suggested lot.”_ <br/><br/> Otherwise, the Lot can be changed during the execution.  |
| AllowLotChange   | **Description:** Allows execution with a different lot than the ordered. <br/><br/> **Possible values:** true, false <br/><br/> **Action:** Used in the Orders execution in the WMS Worker app. <br/><br/>  If there is an applicable policy to the line and its value is „false“, then the Lot (if any) which was initially specified in the Warehouse Order Line cannot be changed during the line execution. <br/><br/>  If the user tries to enter a different lot, the app will make a negative sound and will display a pop message: _“Lot change is not allowed. Please select the suggested lot.”_ <br/><br/> Otherwise, the Lot can be changed during the execution.  |
| AllowLocationChange   | **Description:** Allows execution from a different location than the ordered. <br/><br/>**Possible values:** true, false <br/><br/> **Action:** Used in the Orders execution in the WMS Worker app. <br/><br/> If there is an applicable policy to the line and its value is „false“, then the Warehouse Location (if any) which was initially specified in the Warehouse Order Line cannot be changed during the line execution. <br/><br/> If the user tries to enter a different location, the app will make a negative sound and will display a pop message: _"Location change is not allowed. Please select the suggested location."_ <br/><br/> Otherwise, the Location can be changed during the execution. |
| AllowUnitChange   | **Description:**_ Allows execution of a quantity in a different measurement unit than the ordered. <br/><br/> **Possible values:** true, false <br/><br/> **Action:** Used in the Orders execution in the WMS Worker app. <br/><br/> If there is an applicable policy to the line and its value is „false“, then the Quantity Unit which was initially specified in the Warehouse Order Line cannot be changed during the line execution. <br/><br/> If the user tries to enter a different quantity unit, the app will make a negative sound and will display a pop message: _"Quantity Unit change is not allowed. Please select the suggested quantity unit."_ <br/><br/> Otherwise, the Unit can be changed during the execution.  |
| RequireSourceScan   | **Description:** Requires scanning of the source location when moving or dispatching. <br/><br/> **Possible values:** true, false <br/><br/> **Action:** Used in the Orders execution in the WMS Worker app. <br/><br/> If there is an applicable policy to the line and its value is „true“, then the interface of the Location screen won‘t allow easy selection of the Warehouse Location. <br/><br/> The USE button will be hidden and the selection through the availability table will be inactive. |
| RequireDestinationScan   | **Description:** Requires scanning of the destination location when moving or receiving. <br/><br/> **Possible values:** true, false <br/><br/> **Action:** Used in the Orders execution in the WMS Worker app. <br/><br/> If there is an applicable policy to the line and its value is „true“, then the interface of the Destination screen won‘t allow easy selection of the Warehouse Location. <br/><br/> The USE button will be hidden and the selection through the availability table will be inactive. |
| AllowLineSkip   | **Description:** Allows skipping of an order line when executing (allow quantity = 0). <br/><br/> Not planned for release at the moment.  |
| ZoneType   | **Description:** Specifies the type of zone for receiving, shipping, packing, etc. <br/> Can be saved only if the Warehouse and Zone fields are filled in. <br/> The policy is hierarchical, this means that if it set for a particular zone it will applies to all of its subzones. <br/><br/> **Possible values:** picking, packing, receiving, shipping, and storage. <br/><br/> **Action:** Currenty only the picking value is taken into account of the algorithms. It is used by the @suggest-warehouse-locations function.|



# Applicability

You set up each warehouse policy by defining the conditions where it applies, to which products and for how long. 
Each warehouse policy can apply to:

* Warehouse

* Zone and its sub-zones

* Product group and its sub-groups

* Product type

* Specific product

* From date

* To date

NOTE: Some policies can be applied only at the warehouse or zone level.

 

# Importance

Policies have importance. When evaluating a policy, the setting with the highest importance is applied.

For example, if a policy is applied to a root zone and to a sub-zone, the importance of the sub-zone setting determines which setting will be applied:

* If the sub-zone setting has higher priority, it will be applied.

This can be used for hierarchical application of policies for zones.

* If the root zone setting has higher priority, it will be applied. 

This can be used for root zone (or even warehouse level) setting, which overrides the setting for specific zones.


Importance is an integer value, allowing even negative numbers (for very low importance).
