---
title: Uygulama iş mantığı (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 9456340834c06e87f977cd784a37f7436523d29e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743139"
---
# <a name="implementing-business-logic-linq-to-sql"></a>Uygulama iş mantığı (LINQ to SQL)
Terim "iş mantığı" Bu konu başlığı altındaki herhangi bir özel kural veya onu eklenen, güncelleştirilen veya veritabanından silinmiş önce verileri için geçerli doğrulama testlerini ifade eder. İş mantığı da bazen "iş kurallarını" veya "etki alanı mantığı." adlandırılır Böylece sunu katmanı veya veri erişim katmanı bağımsız olarak değiştirilebilir n katmanlı uygulamalarda, genellikle bir mantıksal katmanı olarak tasarlanmıştır. İş mantığı, öncesinde veya sonrasında herhangi bir güncelleştirme, ekleme veya silme işlemi veritabanındaki verilerin veri erişim katmanı tarafından çağrılabilir.  
  
 İş mantığı alanının türü tablo sütununun türü ile uyumlu olduğundan emin olmak için bir şema doğrulaması kadar basit olabilir. Veya, rasgele karmaşık şekillerde etkileşim kuran bir nesne oluşabilir. Kurallar, saklı yordamları veritabanında veya bellek içi nesneler olarak uygulanabilir. Ancak, iş mantığı uygulanır, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] etkinleştirir, kısmi sınıflar ve kısmi yöntemler iş mantığı veri erişim kodu ayırmak için virgül kullanın.  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a>LINQ to SQL iş mantığınızı nasıl çağırır  
 Tasarım zamanında el ile veya SQLMetal ve Nesne İlişkisel Tasarımcısı'nı kullanarak bir varlık sınıfı oluşturduğunuzda, bu kısmi bir sınıf olarak tanımlanır. Bu, ayrı kod dosyasında, başka bir parçası, özel iş mantığı içeren varlık sınıf tanımlayabilirsiniz, anlamına gelir. Derleme zamanında iki bölümü tek bir sınıf halinde birleştirilir. Ancak Nesne İlişkisel Tasarımcısı veya SQLMetal kullanarak, varlık sınıfları yeniden varsa, bunu yapabilirsiniz ve bölümünüzün sınıfının değiştirilmeyecek.  
  
 Varlıklar tanımlayan kısmi sınıflar ve <xref:System.Data.Linq.DataContext> kısmi yöntemler içerir. Önce ve sonra herhangi bir update, INSERT veya delete bir varlık veya varlık özelliği için iş mantığı uygulamak için kullanabileceğiniz genişletilebilirlik noktaları şunlardır. Kısmi yöntemler, derleme zamanı olaylar olarak düşünülebilir. Kod oluşturucunun yöntem imzasını tanımlayan ve içinde get yöntemleri çağırır ve özellik erişimcileri `DataContext` oluşturucusu ve bazı durumlarda arka planda olduğunda <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağrılır. Ancak, belirli bir kısmi yöntemini uygulayamaz ve tanımı yapılan tüm başvurular derleme zamanında kaldırılır.  
  
 Ayrı bir kod dosyanızda yazdığınız uygulama tanımında özel mantığı gereklidir gerçekleştirebilirsiniz. Etki alanı katmanınızdaki, kısmi sınıf kullanabilir veya kısmi yönteminin uygulama tanımınızı ayrı bir nesne veya nesneler çağırabilirsiniz. Her iki durumda da, veri erişim kodu hem, sunu katmanı kodu iş mantığınızı düzgün bir şekilde ayrılır.  
  
## <a name="a-closer-look-at-the-extensibility-points"></a>Genişletilebilirlik noktaları daha yakından bakın  
 Aşağıdaki örnek, Nesne İlişkisel Tasarımcısı tarafından oluşturulan kodun bir parçası gösterir `DataContext` iki tablo sınıf: `Customers` ve `Orders`. INSERT, Update ve Delete yöntemleri unutmayın sınıftaki her tablo için tanımlanır.  
  
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
  
 INSERT uygularsanız, güncelleştirme ve silme, kısmi sınıftaki yöntemlerin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çalışma zamanı, kendi varsayılan yöntemler yerine bunları çağıracaktır olduğunda <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağrılır. Bu, oluşturmak varsayılan davranışın üzerine / okuma / güncelleştirme / silme işlemleri sağlar. Daha fazla bilgi için [izlenecek yol: INSERT özelleştirme, güncelleştirme ve silme davranışı varlık sınıflarının](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).  
  
 `OnCreated` Sınıfı Oluşturucu yöntemi çağrılır.  
  
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
  
 Varlık sınıfları tarafından aranır üç yöntem sahip [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varlık oluşturduğunuzda, yüklenmiş ve doğrulanmış bir çalışma zamanı (zaman `SubmitChanges` olarak adlandırılır). Varlık sınıflarının sonra çağrılan iki kısmi yöntem her bir özellik, özelliğin ayarlanması çağrılan, diğeri için de var. Aşağıdaki kod örneği için oluşturulan yöntemlerden bazıları gösterilmektedir `Customer` sınıfı:  
  
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
  
 Yöntemleri özellik kümesi erişimcisi için aşağıdaki örnekte gösterildiği gibi verilir `CustomerID` özelliği:  
  
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
  
 Sınıfı, kısmında yöntemini uygulayan bir tanımını yazın. Visual Studio'da yazdıktan sonra `partial` bir sınıfın parçası yöntemi tanımlar için IntelliSense görürsünüz.  
  
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
  
 Kısmi yöntemler kullanarak iş mantığı uygulamanıza ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
 [Nasıl yapılır: Varlık sınıflarına doğrulama ekleme](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [İzlenecek yol: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [İzlenecek yol: Varlık sınıflarına doğrulama ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Parçalı Sınıflar ve Yöntemler](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [Kısmi Yöntemler](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [Visual Studio'daki LINQ to SQL Araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [SqlMetal.exe (Kod Üretme Aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
