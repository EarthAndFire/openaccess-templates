## INotifyDataErrorInfo With Data Annotations Validation ##

The **INotifyDataErrorInfo with Data Annotations validation** template provides general implementation of INotifyDataErrorInfo interface for all of the domain classes of your model. In order to take advantage of this validation you just need to implement a partial method in a partial class for each property of your entities like the one below:

> C#

    public const string LestThanZeroMsg = "The Id cannot be less than 0";
    partial void ValidateId(string propertyName, int newValue)
	{
        if (newValue < 0)
        {
            this.AddError(propertyName, LestThanZeroMsg);
        }
        else
        {
            this.RemoveError(propertyName, LestThanZeroMsg);
        }
    }

> VB

    Public Const LestThanZeroMsg As String = "The Id cannot be less than 0"
    Private Sub ValidateId(ByVal propertyName As String, ByVal newValue As Integer)
        If newValue < 0 Then
            Me.AddError(propertyName, LestThanZeroMsg)
        Else
            Me.RemoveError(propertyName, LestThanZeroMsg)
        End If
    End Sub

### Additional Validation Based on Data Annotation Attributes ###

By enabling the *Generate Data Annotation Attributes* option of the Code Generation Tab of your Model Settings you will get additional validation for all of your properties decorated with Data Annotation Attributes.

### Prerequisites ###

- Telerik OpenAccess ORM Q2 2013 or higher installed.
- Visual Studio 2012.
- .NET Framework 4.5.

### Resources ###
- <a href="http://www.telerik.com/products/orm/getting-started.aspx" target="_blank">Telerik OpenAccess ORM - Getting Started</a>
- <a href="http://www.telerik.com/community/forums/orm.aspx" target="_blank">Telerik OpenAccess ORM - Community</a>
- <a href="http://www.telerik.com/help/openaccess-orm/openaccess-tasks-customise-code-generation-overview.html" target="_blank">Telerik OpenAccess ORM - Use Custom Code Generation Templates</a>

### Recommendations ###

In order to take advantage of the code generation templates you need to clone this repository on your local machine.

![](http://windows.github.com/images/clone-in-windows.png)

Please bear in mind that in order to have this button available you need to have the <a href="http://windows.github.com" target="_blank">GitHub for Windows</a> application installed. <a href="https://github.com/blog/1127-github-for-windows" target="_blank">Here</a> you could find a step-by-step tuturial demonstrating this approach.

**Warning**: using the *"Download this repository as a zip file"* option could cause issues with the templates due to different carriage return.