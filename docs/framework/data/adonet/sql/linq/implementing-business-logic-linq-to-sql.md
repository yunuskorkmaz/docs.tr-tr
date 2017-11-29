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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9cba4c71d895d9398e2444885f4f26bf04433251
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-business-logic-linq-to-sql"></a><span data-ttu-id="224a4-102">İş mantığı (LINQ-SQL) uygulama</span><span class="sxs-lookup"><span data-stu-id="224a4-102">Implementing Business Logic (LINQ to SQL)</span></span>
<span data-ttu-id="224a4-103">Bu konudaki "iş mantığı" terimi herhangi bir özel kurallar veya onu takıldığında, güncelleştirilmiş veya veritabanından silinmiş önce verilere uygulamak doğrulama testleri anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="224a4-103">The term "business logic" in this topic refers to any custom rules or validation tests that you apply to data before it is inserted, updated or deleted from the database.</span></span> <span data-ttu-id="224a4-104">İş mantığı da bazen "iş kurallarını" veya "etki alanı mantığı." adlandırılır</span><span class="sxs-lookup"><span data-stu-id="224a4-104">Business logic is also sometimes referred to as "business rules" or "domain logic."</span></span> <span data-ttu-id="224a4-105">Böylece sunu katmanı veya veri erişim katmanı bağımsız olarak değiştirilebilir n katmanlı uygulamalarda, genellikle bir mantıksal katman olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="224a4-105">In n-tier applications it is typically designed as a logical layer so that it can be modified independently of the presentation layer or data access layer.</span></span> <span data-ttu-id="224a4-106">İş mantığı, öncesinde veya sonrasında herhangi güncelleştirme, ekleme veya silme veritabanındaki verilerin, veri erişim katmanı tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="224a4-106">The business logic can be invoked by the data access layer before or after any update, insertion, or deletion of data in the database.</span></span>  
  
 <span data-ttu-id="224a4-107">İş mantığı alan türü tablo sütun türüyle uyumlu olduğundan emin olmak için bir şema doğrulaması kadar basit olabilir.</span><span class="sxs-lookup"><span data-stu-id="224a4-107">The business logic can be as simple as a schema validation to make sure that the type of the field is compatible with the type of the table column.</span></span> <span data-ttu-id="224a4-108">Veya, rasgele karmaşık yöntemle etkileşim nesneler kümesinden oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="224a4-108">Or it can consist of a set of objects that interact in arbitrarily complex ways.</span></span> <span data-ttu-id="224a4-109">Kurallar, veritabanı üzerinde saklı yordamları veya bellek içi nesneleri olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="224a4-109">The rules may be implemented as stored procedures on the database or as in-memory objects.</span></span> <span data-ttu-id="224a4-110">Ancak iş mantığı uygulanır, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kısmi sınıflar ve kısmi yöntemler iş mantığı veri erişim kodundan ayırmak için kullandığınız etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="224a4-110">However the business logic is implemented, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] enables you use partial classes and partial methods to separate the business logic from the data access code.</span></span>  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a><span data-ttu-id="224a4-111">LINQ-SQL iş mantığınızı nasıl çağırır</span><span class="sxs-lookup"><span data-stu-id="224a4-111">How LINQ to SQL Invokes Your Business Logic</span></span>  
 <span data-ttu-id="224a4-112">Ne zaman oluşturduğunuz bir varlık sınıfı tasarım zamanında el ile veya kullanarak [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] veya SQLMetal, kısmi bir sınıf olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="224a4-112">When you generate an entity class at design time, either manually or by using the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or SQLMetal, it is defined as a partial class.</span></span> <span data-ttu-id="224a4-113">Bu ayrı kod dosyasında, başka bir parçası, özel iş mantığı içeren varlık sınıfı tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="224a4-113">This means that, in a separate code file, you can define another part of the entity class that contains your custom business logic.</span></span> <span data-ttu-id="224a4-114">Derleme zamanında iki bölümden tek bir sınıf halinde birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="224a4-114">At compile time, the two parts are merged into a single class.</span></span> <span data-ttu-id="224a4-115">Ancak, varlık sınıflarını kullanarak yeniden oluşturmak zorunda kalırsanız [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] veya SQLMetal, bunu yapabilirsiniz ve bölümünüzün sınıfının değiştirilmeyecek.</span><span class="sxs-lookup"><span data-stu-id="224a4-115">But if you have to regenerate your entity classes by using the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or SQLMetal, you can do so and your part of the class will not be modified.</span></span>  
  
 <span data-ttu-id="224a4-116">Varlıklarını Tanımlama kısmi sınıflar ve <xref:System.Data.Linq.DataContext> kısmi yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="224a4-116">The partial classes that define entities and the <xref:System.Data.Linq.DataContext> contain partial methods.</span></span> <span data-ttu-id="224a4-117">Bunlar, önce ve sonra tüm güncelleştirme, ekleme veya silme bir varlık veya varlık özelliği için iş mantığını uygulamak için kullanabileceğiniz genişletilebilirlik noktalarıdır.</span><span class="sxs-lookup"><span data-stu-id="224a4-117">These are the extensibility points that you can use to apply your business logic before and after any update, insert, or delete for an entity or entity property.</span></span> <span data-ttu-id="224a4-118">Kısmi yöntemler, derleme zamanı olayları olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="224a4-118">Partial methods can be thought of as compile-time events.</span></span> <span data-ttu-id="224a4-119">Kod Oluşturucu get yöntemleri çağırır ve yöntem imzası tanımlar ve ayarlama özelliği erişimcileri `DataContext` oluşturucusu ve bazı durumlarda arka planda olduğunda <xref:System.Data.Linq.DataContext.SubmitChanges%2A> olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="224a4-119">The code-generator defines a method signature and calls the methods in the get and set property accessors, the `DataContext` constructor, and in some cases behind the scenes when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="224a4-120">Ancak, belirli bir kısmi yöntemi kullanılmaz, onu ve tanımına yapılan tüm başvuruları derleme zamanında kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="224a4-120">However, if you do not implement a particular partial method, then all the references to it and the definition are removed at compile time.</span></span>  
  
 <span data-ttu-id="224a4-121">Ayrı kod dosyanızda yazdığınız uygulama tanımında özel mantığı gereklidir gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="224a4-121">In the implementing definition that you write in your separate code file, you can perform whatever custom logic is required.</span></span> <span data-ttu-id="224a4-122">Etki alanı katmanı olarak, kısmi sınıfı kullanabilir veya kısmi yöntemi ayrı bir nesne veya nesneler, uygulama tanımından çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="224a4-122">You can use your partial class itself as your domain layer, or you can call from your implementing definition of the partial method into a separate object or objects.</span></span> <span data-ttu-id="224a4-123">Her iki durumda da, iş mantığı düzgün bir şekilde veri erişim kodunuzu hem sunu katmanı kodunuzu ayrılır.</span><span class="sxs-lookup"><span data-stu-id="224a4-123">Either way, your business logic is cleanly separated from both your data access code and your presentation layer code.</span></span>  
  
## <a name="a-closer-look-at-the-extensibility-points"></a><span data-ttu-id="224a4-124">Genişletilebilirlik noktaları yakından inceleyin</span><span class="sxs-lookup"><span data-stu-id="224a4-124">A Closer Look at the Extensibility Points</span></span>  
 <span data-ttu-id="224a4-125">Tarafından oluşturulan kod parçası, aşağıdaki örnekte [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] için `DataContext` iki tablo olan sınıfı: `Customers` ve `Orders`.</span><span class="sxs-lookup"><span data-stu-id="224a4-125">The following example shows part of the code generated by the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for the `DataContext` class that has two tables: `Customers` and `Orders`.</span></span> <span data-ttu-id="224a4-126">INSERT, Update ve Delete yöntemleri unutmayın sınıftaki her tablo için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="224a4-126">Note that Insert, Update, and Delete methods are defined for each table in the class.</span></span>  
  
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
  
 <span data-ttu-id="224a4-127">INSERT uygularsanız, güncelleştirme ve silme yöntemleri kısmi sınıfınızda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çalışma zamanı, kendi varsayılan yöntemlerini yerine bunları çağıracaktır zaman <xref:System.Data.Linq.DataContext.SubmitChanges%2A> olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="224a4-127">If you implement the Insert, Update and Delete methods in your partial class, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime will call them instead of its own default methods when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="224a4-128">Bu, oluşturma için varsayılan davranışı geçersiz kılma / okuma / güncelleştirme / silme işlemlerine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="224a4-128">This enables you to override the default behavior for create / read / update / delete operations.</span></span> <span data-ttu-id="224a4-129">Daha fazla bilgi için bkz: [izlenecek yol: Ekle özelleştirme, güncelleştirme ve Varlık davranışını silme](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span><span class="sxs-lookup"><span data-stu-id="224a4-129">For more information, see [Walkthrough: Customizing the insert, update, and delete behavior of entity classes](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span></span>  
  
 <span data-ttu-id="224a4-130">`OnCreated` Yöntemi, bir sınıf oluşturucu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="224a4-130">The `OnCreated` method is called in the class constructor.</span></span>  
  
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
  
 <span data-ttu-id="224a4-131">Varlık sınıfı tarafından çağrılır üç yöntem sahip [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varlık oluşturduğunuzda, yüklenen ve doğrulanmış çalışma zamanı (zaman `SubmitChanges` olarak adlandırılır).</span><span class="sxs-lookup"><span data-stu-id="224a4-131">The entity classes have three methods that are called by the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime when the entity is created, loaded, and validated (when `SubmitChanges` is called).</span></span> <span data-ttu-id="224a4-132">Varlık sınıflarını sonra çağrılan kısmi için iki yöntem her bir özellik, özelliğini ayarlamadan önce çağrılan, diğeri de.</span><span class="sxs-lookup"><span data-stu-id="224a4-132">The entity classes also have two partial methods for each property, one that is called before the property is set, and one that is called after.</span></span> <span data-ttu-id="224a4-133">Aşağıdaki kod örneği için oluşturulan yöntemlerin bazıları gösterir `Customer` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="224a4-133">The following code example shows some of the methods generated for the `Customer` class:</span></span>  
  
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
  
 <span data-ttu-id="224a4-134">Yöntemleri için aşağıdaki örnekte gösterildiği gibi özellik set erişimcisine denir `CustomerID` özelliği:</span><span class="sxs-lookup"><span data-stu-id="224a4-134">The methods are called in the property set accessor as shown in the following example for the `CustomerID` property:</span></span>  
  
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
  
 <span data-ttu-id="224a4-135">Sınıfının, bölümünde yöntemi uygulayan bir tanımını yazın.</span><span class="sxs-lookup"><span data-stu-id="224a4-135">In your part of the class, you write an implementing definition of the method.</span></span> <span data-ttu-id="224a4-136">İçinde [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)], yazdıktan sonra `partial` bir sınıf parçası yöntemi tanımlarında için IntelliSense görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="224a4-136">In [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)], after you type `partial` you will see IntelliSense for the method definitions in the other part of the class.</span></span>  
  
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
  
 <span data-ttu-id="224a4-137">Kısmi yöntemler kullanarak uygulamanıza iş mantığı ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="224a4-137">For more information about how to add business logic to your application by using partial methods, see the following topics:</span></span>  
  
 [<span data-ttu-id="224a4-138">Nasıl yapılır: sınıflar için doğrulama ekleme</span><span class="sxs-lookup"><span data-stu-id="224a4-138">How to: Add validation to entity classes</span></span>](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [<span data-ttu-id="224a4-139">İzlenecek yol: Ekle özelleştirme, güncelleştirme ve Varlık davranışını silme</span><span class="sxs-lookup"><span data-stu-id="224a4-139">Walkthrough: Customizing the insert, update, and delete behavior of entity classes</span></span>](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [<span data-ttu-id="224a4-140">İzlenecek yol: Sınıflar için doğrulama ekleme</span><span class="sxs-lookup"><span data-stu-id="224a4-140">Walkthrough: Adding Validation to Entity Classes</span></span>](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)  
  
## <a name="see-also"></a><span data-ttu-id="224a4-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="224a4-141">See Also</span></span>  
 [<span data-ttu-id="224a4-142">Kısmi sınıflar ve yöntemler</span><span class="sxs-lookup"><span data-stu-id="224a4-142">Partial Classes and Methods</span></span>](~/docs/csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)  
 [<span data-ttu-id="224a4-143">Kısmi yöntemler</span><span class="sxs-lookup"><span data-stu-id="224a4-143">Partial Methods</span></span>](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)  
 [<span data-ttu-id="224a4-144">LINQ-SQL Visual Studio Araçları</span><span class="sxs-lookup"><span data-stu-id="224a4-144">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
 [<span data-ttu-id="224a4-145">SqlMetal.exe (kod üretme aracı)</span><span class="sxs-lookup"><span data-stu-id="224a4-145">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
