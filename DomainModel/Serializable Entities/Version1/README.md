## Serializable Entities ##

The **Serializable Entities** templates package provides a code generation with the SerializableAttribute set on each of the domain classes of your model and an additional method preparing the entities for the serialization.

> C#

	[Serializable()]
	public partial class Category
	{
		...
		
		[OnSerializing()]
		internal void OnSerializingMethod(StreamingContext context)
		{
	#if DEBUG
			// The entity that will be serialized must be detached from the context
			// If the entity is not detached, all of its references and collections will be serialized too
			// in this case at the end the entire database will be serialized
			if (Telerik.OpenAccess.OpenAccessContext.PersistenceState.IsDetached(this) != true)
			{
				System.Diagnostics.Debug.Fail("Do not serialize entities that are still attached!");
			}
	#endif
			((PersistenceCapable)this).OpenAccessEnhancedPreSerialize();
		}
	}

> VB

	<Serializable()>
	Public Partial Class Category
		...
	  	<OnSerializing()>
		Friend Sub OnSerializingMethod(ByVal context As StreamingContext)
	#If DEBUG Then
			' The entity that will be serialized must be detached from the context
			' If the entity is not detached, all of its references and collections will be serialized too
			' in this case at the end the entire database will be serialized
			If Telerik.OpenAccess.OpenAccessContext.PersistenceState.IsDetached(Me) <> True Then
				System.Diagnostics.Debug.Fail("Do not serialize entities that are still attached!")
			End If
	#End If
			CType(Me, PersistenceCapable).OpenAccessEnhancedPreSerialize()
		End Sub
	End Class


### Prerequisites ###

- Telerik OpenAccess ORM Q2 2013 SP1 or higher installed.
- Visual Studio 2010.
- .NET Framework 3.5.

### Resources ###
- <a href="http://www.telerik.com/products/orm/getting-started.aspx" target="_blank">Telerik OpenAccess ORM - Getting Started</a>
- <a href="http://www.telerik.com/community/forums/orm.aspx" target="_blank">Telerik OpenAccess ORM - Community</a>
- <a href="http://www.telerik.com/help/openaccess-orm/openaccess-tasks-customise-code-generation-overview.html" target="_blank">Telerik OpenAccess ORM - Use Custom Code Generation Templates</a>

### Recommendations ###

In order to take advantage of the code generation templates you need to clone this repository on your local machine.

![](https://s3.amazonaws.com/github-images/blog/2012/gh4w/clone-in-windows-button.png)

Please bear in mind that in order to have this button available you need to have the <a href="http://windows.github.com" target="_blank">GitHub for Windows</a> application installed. <a href="https://github.com/blog/1127-github-for-windows" target="_blank">Here</a> you could find a step-by-step tuturial demonstrating this approach.

**Warning**: using the *"Download this repository as a zip file"* option could cause issues with the templates due to different carriage return.