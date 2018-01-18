---
title: "İş mantığı (LINQ-SQL) uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d905f34c29fbd8a15cb8225a4a547490a5c14efd
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="implementing-business-logic-linq-to-sql"></a>İş mantığı (LINQ-SQL) uygulama
Bu konudaki "iş mantığı" terimi herhangi bir özel kurallar veya onu takıldığında, güncelleştirilmiş veya veritabanından silinmiş önce verilere uygulamak doğrulama testleri anlamına gelir. İş mantığı da bazen "iş kurallarını" veya "etki alanı mantığı." adlandırılır Böylece sunu katmanı veya veri erişim katmanı bağımsız olarak değiştirilebilir n katmanlı uygulamalarda, genellikle bir mantıksal katman olarak tasarlanmıştır. İş mantığı, öncesinde veya sonrasında herhangi güncelleştirme, ekleme veya silme veritabanındaki verilerin, veri erişim katmanı tarafından çağrılabilir.  
  
 İş mantığı alan türü tablo sütun türüyle uyumlu olduğundan emin olmak için bir şema doğrulaması kadar basit olabilir. Veya, rasgele karmaşık yöntemle etkileşim nesneler kümesinden oluşabilir. Kurallar, veritabanı üzerinde saklı yordamları veya bellek içi nesneleri olarak uygulanabilir. Ancak iş mantığı uygulanır, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kısmi sınıflar ve kısmi yöntemler iş mantığı veri erişim kodundan ayırmak için kullandığınız etkinleştirir.  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a>LINQ-SQL iş mantığınızı nasıl çağırır  
 Ne zaman oluşturduğunuz bir varlık sınıfı tasarım zamanında el ile veya kullanarak [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] veya SQLMetal, kısmi bir sınıf olarak tanımlanır. Bu ayrı kod dosyasında, başka bir parçası, özel iş mantığı içeren varlık sınıfı tanımlayabilirsiniz, anlamına gelir. Derleme zamanında iki bölümden tek bir sınıf halinde birleştirilir. Ancak, varlık sınıflarını kullanarak yeniden oluşturmak zorunda kalırsanız [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] veya SQLMetal, bunu yapabilirsiniz ve bölümünüzün sınıfının değiştirilmeyecek.  
  
 Varlıklarını Tanımlama kısmi sınıflar ve <xref:System.Data.Linq.DataContext> kısmi yöntemler içerir. Bunlar, önce ve sonra tüm güncelleştirme, ekleme veya silme bir varlık veya varlık özelliği için iş mantığını uygulamak için kullanabileceğiniz genişletilebilirlik noktalarıdır. Kısmi yöntemler, derleme zamanı olayları olarak düşünülebilir. Kod Oluşturucu get yöntemleri çağırır ve yöntem imzası tanımlar ve ayarlama özelliği erişimcileri `DataContext` oluşturucusu ve bazı durumlarda arka planda olduğunda <xref:System.Data.Linq.DataContext.SubmitChanges%2A> olarak adlandırılır. Ancak, belirli bir kısmi yöntemi kullanılmaz, onu ve tanımına yapılan tüm başvuruları derleme zamanında kaldırılır.  
  
 Ayrı kod dosyanızda yazdığınız uygulama tanımında özel mantığı gereklidir gerçekleştirebilirsiniz. Etki alanı katmanı olarak, kısmi sınıfı kullanabilir veya kısmi yöntemi ayrı bir nesne veya nesneler, uygulama tanımından çağırabilirsiniz. Her iki durumda da, iş mantığı düzgün bir şekilde veri erişim kodunuzu hem sunu katmanı kodunuzu ayrılır.  
  
## <a name="a-closer-look-at-the-extensibility-points"></a>Genişletilebilirlik noktaları yakından inceleyin  
 Tarafından oluşturulan kod parçası, aşağıdaki örnekte [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] için `DataContext` iki tablo olan sınıfı: `Customers` ve `Orders`. INSERT, Update ve Delete yöntemleri unutmayın sınıftaki her tablo için tanımlanır.  
  
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
  
 INSERT uygularsanız, güncelleştirme ve silme yöntemleri kısmi sınıfınızda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çalışma zamanı, kendi varsayılan yöntemlerini yerine bunları çağıracaktır zaman <xref:System.Data.Linq.DataContext.SubmitChanges%2A> olarak adlandırılır. Bu, oluşturma için varsayılan davranışı geçersiz kılma / okuma / güncelleştirme / silme işlemlerine olanak sağlar. Daha fazla bilgi için bkz: [izlenecek yol: Ekle özelleştirme, güncelleştirme ve Varlık davranışını silme](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).  
  
 `OnCreated` Yöntemi, bir sınıf oluşturucu çağrılır.  
  
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
  
 Varlık sınıfı tarafından çağrılır üç yöntem sahip [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varlık oluşturduğunuzda, yüklenen ve doğrulanmış çalışma zamanı (zaman `SubmitChanges` olarak adlandırılır). Varlık sınıflarını sonra çağrılan kısmi için iki yöntem her bir özellik, özelliğini ayarlamadan önce çağrılan, diğeri de. Aşağıdaki kod örneği için oluşturulan yöntemlerin bazıları gösterir `Customer` sınıfı:  
  
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
  
 Yöntemleri için aşağıdaki örnekte gösterildiği gibi özellik set erişimcisine denir `CustomerID` özelliği:  
  
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
  
 Sınıfının, bölümünde yöntemi uygulayan bir tanımını yazın. İçinde [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)], yazdıktan sonra `partial` bir sınıf parçası yöntemi tanımlarında için IntelliSense görürsünüz.  
  
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
  
 [Nasıl yapılır: sınıflar için doğrulama ekleme](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [İzlenecek yol: Ekle özelleştirme, güncelleştirme ve Varlık davranışını silme](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [İzlenecek yol: Sınıflar için doğrulama ekleme](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Parçalı Sınıflar ve Yöntemler](~/docs/csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)  
 [Kısmi Yöntemler](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)  
 [LINQ-SQL Visual Studio Araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
 [SqlMetal.exe (Kod Üretme Aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
