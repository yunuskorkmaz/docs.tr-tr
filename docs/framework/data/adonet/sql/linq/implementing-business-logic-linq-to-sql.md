---
title: Iş mantığını uygulama (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 3d703f7a13f21947fb5d2b5adcac8ae4df6a1547
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158376"
---
# <a name="implementing-business-logic-linq-to-sql"></a>Iş mantığını uygulama (LINQ to SQL)

Bu konudaki "iş mantığı" terimi, verileri eklenmeden, yapılandırmadan veya veritabanından silinmeden önce, veri için uyguladığınız özel kurallara veya doğrulama testlerine başvurur. İş mantığı bazen "iş kuralları" veya "etki alanı mantığı" olarak da adlandırılır. N katmanlı uygulamalarda, genellikle, sunu katmanından veya veri erişim katmanından bağımsız olarak değiştirilebilecek şekilde mantıksal katman olarak tasarlanmıştır. İş mantığı, veritabanındaki verilerin güncelleştirilmesi, eklenmesi veya silinmesinden önce veya sonra veri erişim katmanı tarafından çağrılabilir.  
  
 Alan türünün tablo sütununun türüyle uyumlu olduğundan emin olmak için, iş mantığı bir şema doğrulaması kadar basit olabilir. Ya da rastgele karmaşık yollarla etkileşim kuran bir nesne kümesinden oluşabilir. Kurallar, veritabanında saklı yordamlar olarak veya bellek içi nesneler olarak uygulanabilir. Ancak iş mantığı uygulanır, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri erişim kodundan iş mantığını ayırmak için kısmi sınıflar ve kısmi Yöntemler kullanmanıza olanak sağlar.  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a>LINQ to SQL Iş mantığınızı nasıl çağırır  

 Tasarım zamanında, el ile veya Nesne İlişkisel Tasarımcısı ya da SQLMetal kullanarak bir varlık sınıfı oluşturduğunuzda, bu, kısmi bir sınıf olarak tanımlanır. Bu, ayrı bir kod dosyasında özel iş mantığınızı içeren varlık sınıfının başka bir bölümünü tanımlayabilmeniz anlamına gelir. Derleme zamanında, iki bölüm tek bir sınıfta birleştirilir. Ancak Nesne İlişkisel Tasarımcısı veya SQLMetal kullanarak varlık sınıflarınızı yeniden oluşturmanız gerekiyorsa, bunu yapabilirsiniz ve sınıfının bir kısmı değiştirilmez.  
  
 Varlıkları tanımlayan kısmi sınıflar ve <xref:System.Data.Linq.DataContext> kısmi yöntemler içerir. Bunlar bir varlık veya varlık özelliği için herhangi bir güncelleştirme, ekleme veya silme işleminden önce ve sonra iş mantığınızı uygulamak için kullanabileceğiniz genişletilebilirlik noktalardır. Kısmi Yöntemler, derleme zamanı olayları olarak düşünülebilir. Kod Oluşturucu bir yöntem imzasını tanımlar ve Get ve set özellik erişimcileri, `DataContext` Oluşturucu ve bazı durumlarda, çağrıldığında bu yöntemleri çağırır <xref:System.Data.Linq.DataContext.SubmitChanges%2A> . Ancak, belirli bir kısmi yöntemi gerçekleştirmeyin, bu durumda ona yapılan tüm başvurular ve tanım derleme sırasında kaldırılır.  
  
 Ayrı kod dosyanızda yazdığınız uygulama tanımında, gerekli olan her türlü özel mantığı yapabilirsiniz. Kısmi sınıfınızı kendi etki alanı katmanınız olarak kullanabilir veya kısmi yöntemin uygulama tanımınızdan ayrı bir nesneye veya nesnelere çağrı yapabilirsiniz. Her iki durumda da, iş mantığınız hem veri erişim kodunuzdan hem de sunum katmanı kodunuzda düzgün bir şekilde ayrılır.  
  
## <a name="a-closer-look-at-the-extensibility-points"></a>Genişletilebilirlik noktalarına daha yakından bakış  

 Aşağıdaki örnek, iki tablo içeren sınıf için Nesne İlişkisel Tasarımcısı tarafından oluşturulan kodun bir parçasını gösterir `DataContext` : `Customers` ve `Orders` . INSERT, Update ve DELETE yöntemlerinin sınıftaki her tablo için tanımlandığını unutmayın.  
  
```vb  
Partial Public Class Northwnd  
    Inherits System.Data.Linq.DataContext  
  
    Private Shared mappingSource As _  
        System.Data.Linq.Mapping.MappingSource = New _  
        AttributeMappingSource  
  
    #Region "Extensibility Method Definitions"  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub InsertCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub UpdateCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub DeleteCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub InsertOrder(instance As [Order])  
    End Sub  
    Partial Private Sub UpdateOrder(instance As [Order])  
    End Sub  
    Partial Private Sub DeleteOrder(instance As [Order])  
    End Sub  
    #End Region  
```  
  
```csharp  
public partial class MyNorthWindDataContext : System.Data.Linq.DataContext  
    {  
        private static System.Data.Linq.Mapping.MappingSource mappingSource = new AttributeMappingSource();  
  
        #region Extensibility Method Definitions  
        partial void OnCreated();  
        partial void InsertCustomer(Customer instance);  
        partial void UpdateCustomer(Customer instance);  
        partial void DeleteCustomer(Customer instance);  
        partial void InsertOrder(Order instance);  
        partial void UpdateOrder(Order instance);  
        partial void DeleteOrder(Order instance);  
        #endregion  
```  
  
 Kısmi sınıfınıza INSERT, Update ve DELETE yöntemlerini uygularsanız, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çağrıldığında çalışma zamanı bunları kendi varsayılan yöntemleri yerine çağırır <xref:System.Data.Linq.DataContext.SubmitChanges%2A> . Bu, oluşturma/okuma/güncelleştirme/silme işlemleri için varsayılan davranışı geçersiz kılmanıza olanak sağlar. Daha fazla bilgi için bkz. [Izlenecek yol: varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).  
  
 `OnCreated`Yöntemi sınıf oluşturucusunda çağrılır.  
  
```vb  
Public Sub New(ByVal connection As String)  
    MyBase.New(connection, mappingSource)  
    OnCreated()  
End Sub  
```  
  
```csharp  
public MyNorthWindDataContext(string connection) :  
            base(connection, mappingSource)  
        {  
            OnCreated();  
        }  
```  
  
 Varlık sınıflarının, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varlık oluşturulduğunda, yüklendiğinde ve doğrulandığında (çağrıldığında) çalışma zamanı tarafından çağrılan üç yöntemi vardır `SubmitChanges` . Varlık sınıflarının her bir özellik için iki kısmi yöntemi vardır, bir özellik ayarlanmadan önce çağırılır ve öğesinden sonra çağrılır. Aşağıdaki kod örneği, sınıfı için oluşturulan yöntemlerin bazılarını göstermektedir `Customer` :  
  
```vb  
#Region "Extensibility Method Definitions"  
    Partial Private Sub OnLoaded()  
    End Sub  
    Partial Private Sub OnValidate(action As _  
        System.Data.Linq.ChangeAction)  
    End Sub  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub OnCustomerIDChanging(value As String)  
    End Sub  
    Partial Private Sub OnCustomerIDChanged()  
    End Sub  
    Partial Private Sub OnCompanyNameChanging(value As String)  
    End Sub  
    Partial Private Sub OnCompanyNameChanged()  
    End Sub  
' ...Additional Changing/Changed methods for each property.  
```  
  
```csharp  
#region Extensibility Method Definitions  
    partial void OnLoaded();  
    partial void OnValidate();  
    partial void OnCreated();  
    partial void OnCustomerIDChanging(string value);  
    partial void OnCustomerIDChanged();  
    partial void OnCompanyNameChanging(string value);  
    partial void OnCompanyNameChanged();  
// ...additional Changing/Changed methods for each property  
```  
  
 Yöntemleri, özelliği için aşağıdaki örnekte gösterildiği gibi özellik kümesi erişimcisinde çağrılır `CustomerID` :  
  
```vb  
Public Property CustomerID() As String  
    Set  
        If (String.Equals(Me._CustomerID, value) = False) Then  
            Me.OnCustomerIDChanging(value)  
            Me.SendPropertyChanging()  
            Me._CustomerID = value  
            Me.SendPropertyChanged("CustomerID")  
            Me.OnCustomerIDChanged()  
        End If  
    End Set  
End Property  
```  
  
```csharp  
public string CustomerID  
{  
    set  
    {  
        if ((this._CustomerID != value))  
        {  
            this.OnCustomerIDChanging(value);  
            this.SendPropertyChanging();  
            this._CustomerID = value;  
            this.SendPropertyChanged("CustomerID");  
            this.OnCustomerIDChanged();  
        }  
     }  
}  
```  
  
 Sınıfının bölümünde, yönteminin bir uygulama tanımını yazarsınız. Visual Studio 'da, yazdıktan sonra `partial` sınıfının diğer bölümünde yöntem tanımları Için IntelliSense 'i görürsünüz.  
  
```vb  
Partial Public Class Customer  
    Private Sub OnCustomerIDChanging(value As String)  
        ' Perform custom validation logic here.  
    End Sub  
End Class  
```  
  
```csharp  
partial class Customer
    {  
        partial void OnCustomerIDChanging(string value)  
        {  
            //Perform custom validation logic here.  
        }  
    }  
```  
  
 Kısmi yöntemler kullanarak uygulamanıza iş mantığı ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
 [Nasıl yapılır: Varlık sınıflarına doğrulama ekleme](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [İzlenecek yol: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [İzlenecek yol: varlık sınıflarına doğrulama ekleme](/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Parçalı Sınıflar ve Yöntemler](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [Kısmi Yöntemler](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [Visual Studio'daki LINQ to SQL Araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
