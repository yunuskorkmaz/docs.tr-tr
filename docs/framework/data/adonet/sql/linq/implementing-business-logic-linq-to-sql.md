---
title: İş Mantığının Uygulanması (LINQ - SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 51b92549a40d0e5121cc390f5dbdf726cc06404b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174556"
---
# <a name="implementing-business-logic-linq-to-sql"></a>İş Mantığının Uygulanması (LINQ - SQL)
Bu konudaki "iş mantığı" terimi, veritabanına eklenmeden, güncellenmeden veya silinmeden önce verilere uyguladığınız özel kuralları veya doğrulama testlerini ifade eder. İş mantığı bazen "iş kuralları" veya "etki alanı mantığı" olarak da adlandırılır. N katmanlı uygulamalarda genellikle mantıksal bir katman olarak tasarlanmıştır, böylece sunu katmanından veya veri erişim katmanından bağımsız olarak değiştirilebilir. İş mantığı, veri tabanındaki verilerin güncelleştirilmesinden, eklenmesinden veya silinmesinden önce veya sonra veri erişim katmanı tarafından çağrılabilir.  
  
 İş mantığı, alan türünün tablo sütununun türüyle uyumlu olduğundan emin olmak için şema doğrulaması kadar basit olabilir. Veya rasgele karmaşık şekillerde etkileşim nesneleri kümesi nden oluşabilir. Kurallar veritabanında depolanan yordamlar olarak veya bellek nesneleri olarak uygulanabilir. Ancak iş mantığı uygulanır, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] iş mantığını veri erişim kodundan ayırmak için kısmi sınıflar ve kısmi yöntemler kullanmanıza olanak tanır.  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a>LINQ'dan SQL'e İş Mantığınızı Nasıl Çağırır?  
 Tasarım zamanında, el ile veya Nesne İlişkisel Tasarımcı veya SQLMetal kullanarak bir varlık sınıfı oluşturduğunuzda, kısmi sınıf olarak tanımlanır. Bu, ayrı bir kod dosyasında, özel iş mantığınızı içeren varlık sınıfının başka bir bölümünü tanımlayabileceğiniz anlamına gelir. Derleme zamanında, iki bölüm tek bir sınıf halinde birleştirilir. Ancak Object Relational Designer veya SQLMetal'i kullanarak varlık sınıflarınızı yeniden oluşturmanız gerekiyorsa, bunu yapabilirsiniz ve sınıfın sizin bölümünüz değiştirilmez.  
  
 Varlıkları tanımlayan kısmi sınıflar ve <xref:System.Data.Linq.DataContext> kısmi yöntemler içerir. Bunlar, bir varlık veya varlık özelliği için herhangi bir güncelleştirme, ekleme veya silme den önce ve sonra iş mantığınızı uygulamak için kullanabileceğiniz genişletilebilirlik noktalarıdır. Kısmi yöntemler derleme zamanı olayları olarak düşünülebilir. Kod oluşturucu bir yöntem imzasını tanımlar ve özellik erişime girenleri, `DataContext` oluşturucuyu ve bazı durumlarda <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağrıldığında perde arkasında yöntemleri çağırır. Ancak, belirli bir kısmi yöntemi uygulamazsanız, bu yönteme ve tanıma yapılan tüm başvurular derleme zamanında kaldırılır.  
  
 Ayrı kod dosyanıza yazdığınız uygulama tanımında, gereken özel mantığı gerçekleştirebilirsiniz. Kısmi sınıfınızın kendisini etki alanı katmanınız olarak kullanabilir veya kısmi yöntemin uygulama tanımından ayrı bir nesneye veya nesneye çağrılayabilirsiniz. Her iki şekilde de, iş mantığınız hem veri erişim kodunuzdan hem de sunu katmanı kodunuzdan temiz bir şekilde ayrılır.  
  
## <a name="a-closer-look-at-the-extensibility-points"></a>Genişletilebilirlik Noktalarına Daha Yakından Bakış  
 Aşağıdaki örnek, iki tabloya sahip sınıf için Nesne `DataContext` İlişkisel Tasarımcısı `Customers` tarafından `Orders`oluşturulan kodun bir bölümünü gösterir: ve . Sınıftaki her tablo için Ekle, Güncelleştir ve Sil yöntemlerinin tanımlandığını unutmayın.  
  
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
  
 Kısmi sınıfınızda Ekle, Güncelleştir ve Sil yöntemlerini [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygularsanız, çalışma zamanı çağrıldığında <xref:System.Data.Linq.DataContext.SubmitChanges%2A> kendi varsayılan yöntemleri yerine onları çağırır. Bu, oluşturma / okuma / güncelleme / silme işlemleri için varsayılan davranışı geçersiz kılmanızı sağlar. Daha fazla bilgi için [Bkz. Walkthrough: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme.](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 Yöntem `OnCreated` sınıf oluşturucu olarak adlandırılır.  
  
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
  
 Varlık sınıfları, varlık oluşturulduğunda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yüklendiğinde ve doğrulandığında (çağrıldığında) `SubmitChanges` çalışma zamanına göre çağrılan üç yönteme sahiptir. Varlık sınıfları da her özellik için iki kısmi yöntem vardır, bir özellik ayarlıönce denir ve sonra denir. Aşağıdaki kod örneği, sınıf için oluşturulan `Customer` yöntemlerden bazılarını gösterir:  
  
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
  
 Yöntem özelliği için `CustomerID` aşağıdaki örnekte gösterildiği gibi özellik kümesi erişimci denir:  
  
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
  
 Sınıfın sizin bölümünde, yöntemin uygulama tanımını yazarsınız. Visual Studio'da, `partial` yazdıktan sonra sınıfın diğer bölümündeki yöntem tanımları için IntelliSense'i görürsünüz.  
  
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
  
 Kısmi yöntemler kullanarak uygulamanız için iş mantığı nın nasıl eklenöğretilen hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
 [Nasıl yapılır: Varlık sınıflarına doğrulama ekleme](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [İzlenecek yol: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [Walkthrough: Varlık Sınıflarına Doğrulama Ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Parçalı Sınıflar ve Yöntemler](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [Kısmi Yöntemler](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [Visual Studio'daki LINQ to SQL Araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [SqlMetal.exe (Kod Üretme Aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
