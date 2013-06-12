## INotifyDataErrorInfo with Data Annotations Validation ##

The **INotifyDataErrorInfo with Data Annotations validation** template provides general implementation of INotifyDataErrorInfo interface for all of the domain classes of your model. In order to take advantage of this validation you just need to implement a partial method in a partial class for each property of your entities like the one below:

> C#

    public const string LestThanZeroMsg = "The Id cannot be less than 0";
    partial void ValidateId(string propertyName, int newValue){
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

- Telerik OpenAccess ORM Q2 2013 installed.
- Visual Studio 2010 or higher.

### Resources ###
- [Telerik OpenAccess ORM - Getting Started](http://www.telerik.com/products/orm/getting-started.aspx "Getting Started")
- [Telerik OpenAccess ORM - Community](http://www.telerik.com/community/forums/orm.aspx "Telerik OpenAccess ORM Forum")
- [Telerik OpenAccess ORM - Use Custom Code Generation Templates](http://www.telerik.com/help/openaccess-orm/openaccess-tasks-customise-code-generation-overview.html "Customizing Code Generation Templates") 
