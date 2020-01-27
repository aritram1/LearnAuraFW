# LearnAuraFW
To learn Aura framework

#Events

-----------------------------DEFINE THE EVENT-----------------------------
create an event a myevent.evt file

<aura:event type="COMPONENT">
	<aura:attribute contactName="contactName" type="String" default=""/>
</aura:event>

-----------------------------FIRE FROM COMPONENT--------------------------
In the component mark-up, register the event so it can be fired from the component.

<aura:registerEvent name="fireThisMethod" type="c:myevent"/>

-----------------------
-----------------------
In the component mark-up, fire the event on some action (e.g. cnclick).

<lightning:input type="Button" onclick="fireThisMethod" name="button1" value="Click Me"/>

-----------------------
-----------------------
in the component's js file, fire the event

function fireThisMethod(component, event, helper){
	var personalEvent = component.getEvent("myevent");
	personalEvent.setParams({
		contactName: 'Aritra' //a hardcoded name
	})
	personalEvent.fire();
}

--------------------HANDLE------------------------------------------------
In the parent component include the mycomponent to ensure it can fire some code when myevent occurs within the component or in the dom tree.
<div.../>
	<aura:attribute name="contactName" type="String" default=""/>
	<c:mycomponent myevent="{!c.handlemyevent}"/>
<div.../>

--------------------------------------------------------------------------
Handle the event with the function : handlemyevent()

handlemyevent : function(component, event, helper) {
	component.set("v.contactName", event.getParam("contactName"));
}





