---
title: Uygulama iş mantığı (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 7e24bf24785538863738fe2c006834a77f47e1ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496096"
---
# <a name="implementing-business-logic-linq-to-sql"></a><span data-ttu-id="79554-102">Uygulama iş mantığı (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="79554-102">Implementing Business Logic (LINQ to SQL)</span></span>
<span data-ttu-id="79554-103">Terim "iş mantığı" Bu konu başlığı altındaki herhangi bir özel kural veya onu eklenen, güncelleştirilen veya veritabanından silinmiş önce verileri için geçerli doğrulama testlerini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="79554-103">The term "business logic" in this topic refers to any custom rules or validation tests that you apply to data before it is inserted, updated or deleted from the database.</span></span> <span data-ttu-id="79554-104">İş mantığı da bazen "iş kurallarını" veya "etki alanı mantığı." adlandırılır</span><span class="sxs-lookup"><span data-stu-id="79554-104">Business logic is also sometimes referred to as "business rules" or "domain logic."</span></span> <span data-ttu-id="79554-105">Böylece sunu katmanı veya veri erişim katmanı bağımsız olarak değiştirilebilir n katmanlı uygulamalarda, genellikle bir mantıksal katmanı olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="79554-105">In n-tier applications it is typically designed as a logical layer so that it can be modified independently of the presentation layer or data access layer.</span></span> <span data-ttu-id="79554-106">İş mantığı, öncesinde veya sonrasında herhangi bir güncelleştirme, ekleme veya silme işlemi veritabanındaki verilerin veri erişim katmanı tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="79554-106">The business logic can be invoked by the data access layer before or after any update, insertion, or deletion of data in the database.</span></span>  
  
 <span data-ttu-id="79554-107">İş mantığı alanının türü tablo sütununun türü ile uyumlu olduğundan emin olmak için bir şema doğrulaması kadar basit olabilir.</span><span class="sxs-lookup"><span data-stu-id="79554-107">The business logic can be as simple as a schema validation to make sure that the type of the field is compatible with the type of the table column.</span></span> <span data-ttu-id="79554-108">Veya, rasgele karmaşık şekillerde etkileşim kuran bir nesne oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="79554-108">Or it can consist of a set of objects that interact in arbitrarily complex ways.</span></span> <span data-ttu-id="79554-109">Kurallar, saklı yordamları veritabanında veya bellek içi nesneler olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="79554-109">The rules may be implemented as stored procedures on the database or as in-memory objects.</span></span> <span data-ttu-id="79554-110">Ancak, iş mantığı uygulanır, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] etkinleştirir, kısmi sınıflar ve kısmi yöntemler iş mantığı veri erişim kodu ayırmak için virgül kullanın.</span><span class="sxs-lookup"><span data-stu-id="79554-110">However the business logic is implemented, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] enables you use partial classes and partial methods to separate the business logic from the data access code.</span></span>  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a><span data-ttu-id="79554-111">LINQ to SQL iş mantığınızı nasıl çağırır</span><span class="sxs-lookup"><span data-stu-id="79554-111">How LINQ to SQL Invokes Your Business Logic</span></span>  
 <span data-ttu-id="79554-112">Ne zaman oluşturduğunuz varlık sınıfı tasarım zamanında el ile ya da kullanarak [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] veya SQLMetal, kısmi bir sınıf olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="79554-112">When you generate an entity class at design time, either manually or by using the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or SQLMetal, it is defined as a partial class.</span></span> <span data-ttu-id="79554-113">Bu, ayrı kod dosyasında, başka bir parçası, özel iş mantığı içeren varlık sınıf tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="79554-113">This means that, in a separate code file, you can define another part of the entity class that contains your custom business logic.</span></span> <span data-ttu-id="79554-114">Derleme zamanında iki bölümü tek bir sınıf halinde birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="79554-114">At compile time, the two parts are merged into a single class.</span></span> <span data-ttu-id="79554-115">Ancak, varlık sınıfları kullanarak yeniden varsa [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] veya SQLMetal, bunu yapabilirsiniz ve sınıf bölümünüzün değiştirilmeyecek.</span><span class="sxs-lookup"><span data-stu-id="79554-115">But if you have to regenerate your entity classes by using the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or SQLMetal, you can do so and your part of the class will not be modified.</span></span>  
  
 <span data-ttu-id="79554-116">Varlıklar tanımlayan kısmi sınıflar ve <xref:System.Data.Linq.DataContext> kısmi yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="79554-116">The partial classes that define entities and the <xref:System.Data.Linq.DataContext> contain partial methods.</span></span> <span data-ttu-id="79554-117">Önce ve sonra herhangi bir update, INSERT veya delete bir varlık veya varlık özelliği için iş mantığı uygulamak için kullanabileceğiniz genişletilebilirlik noktaları şunlardır.</span><span class="sxs-lookup"><span data-stu-id="79554-117">These are the extensibility points that you can use to apply your business logic before and after any update, insert, or delete for an entity or entity property.</span></span> <span data-ttu-id="79554-118">Kısmi yöntemler, derleme zamanı olaylar olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="79554-118">Partial methods can be thought of as compile-time events.</span></span> <span data-ttu-id="79554-119">Kod oluşturucunun yöntem imzasını tanımlayan ve içinde get yöntemleri çağırır ve özellik erişimcileri `DataContext` oluşturucusu ve bazı durumlarda arka planda olduğunda <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağrılır.</span><span class="sxs-lookup"><span data-stu-id="79554-119">The code-generator defines a method signature and calls the methods in the get and set property accessors, the `DataContext` constructor, and in some cases behind the scenes when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="79554-120">Ancak, belirli bir kısmi yöntemini uygulayamaz ve tanımı yapılan tüm başvurular derleme zamanında kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="79554-120">However, if you do not implement a particular partial method, then all the references to it and the definition are removed at compile time.</span></span>  
  
 <span data-ttu-id="79554-121">Ayrı bir kod dosyanızda yazdığınız uygulama tanımında özel mantığı gereklidir gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79554-121">In the implementing definition that you write in your separate code file, you can perform whatever custom logic is required.</span></span> <span data-ttu-id="79554-122">Etki alanı katmanınızdaki, kısmi sınıf kullanabilir veya kısmi yönteminin uygulama tanımınızı ayrı bir nesne veya nesneler çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79554-122">You can use your partial class itself as your domain layer, or you can call from your implementing definition of the partial method into a separate object or objects.</span></span> <span data-ttu-id="79554-123">Her iki durumda da, veri erişim kodu hem, sunu katmanı kodu iş mantığınızı düzgün bir şekilde ayrılır.</span><span class="sxs-lookup"><span data-stu-id="79554-123">Either way, your business logic is cleanly separated from both your data access code and your presentation layer code.</span></span>  
  
## <a name="a-closer-look-at-the-extensibility-points"></a><span data-ttu-id="79554-124">Genişletilebilirlik noktaları daha yakından bakın</span><span class="sxs-lookup"><span data-stu-id="79554-124">A Closer Look at the Extensibility Points</span></span>  
 <span data-ttu-id="79554-125">Tarafından oluşturulan kodun bir parçası aşağıdaki örnekte [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] için `DataContext` iki tablo sınıf: `Customers` ve `Orders`.</span><span class="sxs-lookup"><span data-stu-id="79554-125">The following example shows part of the code generated by the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for the `DataContext` class that has two tables: `Customers` and `Orders`.</span></span> <span data-ttu-id="79554-126">INSERT, Update ve Delete yöntemleri unutmayın sınıftaki her tablo için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="79554-126">Note that Insert, Update, and Delete methods are defined for each table in the class.</span></span>  
  
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
  
 <span data-ttu-id="79554-127">INSERT uygularsanız, güncelleştirme ve silme, kısmi sınıftaki yöntemlerin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çalışma zamanı, kendi varsayılan yöntemler yerine bunları çağıracaktır olduğunda <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağrılır.</span><span class="sxs-lookup"><span data-stu-id="79554-127">If you implement the Insert, Update and Delete methods in your partial class, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime will call them instead of its own default methods when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="79554-128">Bu, oluşturmak varsayılan davranışın üzerine / okuma / güncelleştirme / silme işlemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="79554-128">This enables you to override the default behavior for create / read / update / delete operations.</span></span> <span data-ttu-id="79554-129">Daha fazla bilgi için [izlenecek yol: INSERT özelleştirme, güncelleştirme ve silme davranışı varlık sınıflarının](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span><span class="sxs-lookup"><span data-stu-id="79554-129">For more information, see [Walkthrough: Customizing the insert, update, and delete behavior of entity classes](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span></span>  
  
 <span data-ttu-id="79554-130">`OnCreated` Sınıfı Oluşturucu yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="79554-130">The `OnCreated` method is called in the class constructor.</span></span>  
  
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
  
 <span data-ttu-id="79554-131">Varlık sınıfları tarafından aranır üç yöntem sahip [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varlık oluşturduğunuzda, yüklenmiş ve doğrulanmış bir çalışma zamanı (zaman `SubmitChanges` olarak adlandırılır).</span><span class="sxs-lookup"><span data-stu-id="79554-131">The entity classes have three methods that are called by the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime when the entity is created, loaded, and validated (when `SubmitChanges` is called).</span></span> <span data-ttu-id="79554-132">Varlık sınıflarının sonra çağrılan iki kısmi yöntem her bir özellik, özelliğin ayarlanması çağrılan, diğeri için de var.</span><span class="sxs-lookup"><span data-stu-id="79554-132">The entity classes also have two partial methods for each property, one that is called before the property is set, and one that is called after.</span></span> <span data-ttu-id="79554-133">Aşağıdaki kod örneği için oluşturulan yöntemlerden bazıları gösterilmektedir `Customer` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="79554-133">The following code example shows some of the methods generated for the `Customer` class:</span></span>  
  
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
  
 <span data-ttu-id="79554-134">Yöntemleri özellik kümesi erişimcisi için aşağıdaki örnekte gösterildiği gibi verilir `CustomerID` özelliği:</span><span class="sxs-lookup"><span data-stu-id="79554-134">The methods are called in the property set accessor as shown in the following example for the `CustomerID` property:</span></span>  
  
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
  
 <span data-ttu-id="79554-135">Sınıfı, kısmında yöntemini uygulayan bir tanımını yazın.</span><span class="sxs-lookup"><span data-stu-id="79554-135">In your part of the class, you write an implementing definition of the method.</span></span> <span data-ttu-id="79554-136">Visual Studio'da yazdıktan sonra `partial` bir sınıfın parçası yöntemi tanımlar için IntelliSense görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="79554-136">In Visual Studio, after you type `partial` you will see IntelliSense for the method definitions in the other part of the class.</span></span>  
  
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
  
 <span data-ttu-id="79554-137">Kısmi yöntemler kullanarak iş mantığı uygulamanıza ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="79554-137">For more information about how to add business logic to your application by using partial methods, see the following topics:</span></span>  
  
 [<span data-ttu-id="79554-138">Nasıl yapılır: Varlık sınıflarına doğrulama ekleme</span><span class="sxs-lookup"><span data-stu-id="79554-138">How to: Add validation to entity classes</span></span>](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [<span data-ttu-id="79554-139">İzlenecek yol: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="79554-139">Walkthrough: Customizing the insert, update, and delete behavior of entity classes</span></span>](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [<span data-ttu-id="79554-140">İzlenecek yol: Varlık sınıflarına doğrulama ekleme</span><span class="sxs-lookup"><span data-stu-id="79554-140">Walkthrough: Adding Validation to Entity Classes</span></span>](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)  
  
## <a name="see-also"></a><span data-ttu-id="79554-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79554-141">See also</span></span>
- [<span data-ttu-id="79554-142">Parçalı Sınıflar ve Yöntemler</span><span class="sxs-lookup"><span data-stu-id="79554-142">Partial Classes and Methods</span></span>](~/docs/csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [<span data-ttu-id="79554-143">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="79554-143">Partial Methods</span></span>](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [<span data-ttu-id="79554-144">Visual Studio'daki LINQ to SQL Araçları</span><span class="sxs-lookup"><span data-stu-id="79554-144">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [<span data-ttu-id="79554-145">SqlMetal.exe (Kod Üretme Aracı)</span><span class="sxs-lookup"><span data-stu-id="79554-145">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
