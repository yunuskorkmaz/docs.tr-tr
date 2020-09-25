---
title: Türü Belirtilmiş DataSets için Yorum Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 79d3913827d5df6f0ac4e77bfdb8f37b553a86d2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203754"
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="bf472-102">Türü Belirtilmiş DataSets için Yorum Ekleme</span><span class="sxs-lookup"><span data-stu-id="bf472-102">Annotating Typed DataSets</span></span>

<span data-ttu-id="bf472-103">Ek açıklamalar, temeldeki şemayı değiştirmeden, yazdığınız öğelerin adlarını değiştirmenize olanak sağlar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="bf472-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="bf472-104">Temel şemadaki öğelerin adlarını değiştirmek, yazılan veri **kümesinin** veri kaynağında mevcut olmayan nesnelere başvurmasına ve veri kaynağında var olan nesnelere yönelik bir başvuruyu kaybetmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="bf472-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="bf472-105">Ek açıklamaları kullanarak, yazılan **veri** kümenizdeki nesnelerin adlarını daha anlamlı adlarla özelleştirebilir, böylece kod daha okunabilir ve yazılan **Veri kümeniz** istemcilerin kullanması için daha kolay olur, temel şemayı bozulmadan bırakır.</span><span class="sxs-lookup"><span data-stu-id="bf472-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="bf472-106">Örneğin, **Northwind** veritabanının **Customers** tablosu için aşağıdaki şema öğesi, **CustomersRow** ve adlandırılmış müşterilerin bir **DataRow** nesne adı ile sonuçlanır <xref:System.Data.DataRowCollection> **Customers**.</span><span class="sxs-lookup"><span data-stu-id="bf472-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="bf472-107">Müşterilerin **DataRowCollection** adı istemci **Customers** kodunda anlamlıdır, ancak tek bir nesne olduğundan **CustomersRow** **DataRow** adı yanıltıcı olur.</span><span class="sxs-lookup"><span data-stu-id="bf472-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="bf472-108">Ayrıca, yaygın senaryolarda nesne, **satır** tanımlayıcı olmadan, bunun yerine yalnızca bir **Müşteri** nesnesi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="bf472-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="bf472-109">Çözüm, şemaya açıklama eklemek ve **DataRow** ve **DataRowCollection** nesnelerinin yeni adlarını belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="bf472-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="bf472-110">Önceki şemanın açıklamalı sürümü aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bf472-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="bf472-111">**Müşterinin** **typedName** değerini belirtmek, bir **DataRow** nesnesinin **Müşteri**adına neden olur.</span><span class="sxs-lookup"><span data-stu-id="bf472-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="bf472-112">**Müşteriler** Için **typedPlural** değeri belirtildiğinde **müşterilerin** **DataRowCollection** adı korunur.</span><span class="sxs-lookup"><span data-stu-id="bf472-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="bf472-113">Aşağıdaki tabloda kullanıma sunulan ek açıklamalar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bf472-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="bf472-114">Ek Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf472-114">Annotation</span></span>|<span data-ttu-id="bf472-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf472-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="bf472-116">**typedName**</span><span class="sxs-lookup"><span data-stu-id="bf472-116">**typedName**</span></span>|<span data-ttu-id="bf472-117">Nesnenin adı.</span><span class="sxs-lookup"><span data-stu-id="bf472-117">Name of the object.</span></span>|  
|<span data-ttu-id="bf472-118">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="bf472-118">**typedPlural**</span></span>|<span data-ttu-id="bf472-119">Bir nesne koleksiyonunun adı.</span><span class="sxs-lookup"><span data-stu-id="bf472-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="bf472-120">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="bf472-120">**typedParent**</span></span>|<span data-ttu-id="bf472-121">Üst ilişkide başvurulduğu sırada nesnenin adı.</span><span class="sxs-lookup"><span data-stu-id="bf472-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="bf472-122">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="bf472-122">**typedChildren**</span></span>|<span data-ttu-id="bf472-123">Bir alt ilişkiden nesneleri döndürmek için yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="bf472-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="bf472-124">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="bf472-124">**nullValue**</span></span>|<span data-ttu-id="bf472-125">Temel değer **DBNull**ise değeri.</span><span class="sxs-lookup"><span data-stu-id="bf472-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="bf472-126">**NullValue** ek açıklamaları için aşağıdaki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="bf472-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="bf472-127">Varsayılan değer **_throw**.</span><span class="sxs-lookup"><span data-stu-id="bf472-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="bf472-128">Aşağıdaki tabloda, **NullValue** ek açıklaması için belirtime değerleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bf472-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="bf472-129">nullValue değeri</span><span class="sxs-lookup"><span data-stu-id="bf472-129">nullValue Value</span></span>|<span data-ttu-id="bf472-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf472-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="bf472-131">*Değiştirme değeri*</span><span class="sxs-lookup"><span data-stu-id="bf472-131">*Replacement Value*</span></span>|<span data-ttu-id="bf472-132">Döndürülecek bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="bf472-132">Specify a value to be returned.</span></span> <span data-ttu-id="bf472-133">Döndürülen değerin öğe türüyle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf472-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="bf472-134">Örneğin, `nullValue="0"` null tamsayı alanları için 0 döndürmek üzere kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf472-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="bf472-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="bf472-135">**_throw**</span></span>|<span data-ttu-id="bf472-136">Bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf472-136">Throw an exception.</span></span> <span data-ttu-id="bf472-137">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="bf472-137">This is the default.</span></span>|  
|<span data-ttu-id="bf472-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="bf472-138">**_null**</span></span>|<span data-ttu-id="bf472-139">Bir temel tür ile karşılaşılırsa, null bir başvuru döndürün veya bir özel durum oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bf472-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="bf472-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="bf472-140">**_empty**</span></span>|<span data-ttu-id="bf472-141">Dizeler için, **String. Empty**döndürün, aksi halde boş bir oluşturucudan oluşturulan nesneyi döndürün.</span><span class="sxs-lookup"><span data-stu-id="bf472-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="bf472-142">İlkel bir tür ile karşılaşılırsa bir özel durum oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bf472-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="bf472-143">Aşağıdaki tabloda, türü belirtilmiş bir **veri kümesindeki** nesneler için varsayılan değerler ve kullanılabilir ek açıklamalar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bf472-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="bf472-144">Nesne/yöntem/olay</span><span class="sxs-lookup"><span data-stu-id="bf472-144">Object/Method/Event</span></span>|<span data-ttu-id="bf472-145">Varsayılan</span><span class="sxs-lookup"><span data-stu-id="bf472-145">Default</span></span>|<span data-ttu-id="bf472-146">Ek Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf472-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="bf472-147">**DataRow**</span><span class="sxs-lookup"><span data-stu-id="bf472-147">**DataTable**</span></span>|<span data-ttu-id="bf472-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="bf472-148">TableNameDataTable</span></span>|<span data-ttu-id="bf472-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="bf472-149">typedPlural</span></span>|  
|<span data-ttu-id="bf472-150">**DataTable** Yöntem</span><span class="sxs-lookup"><span data-stu-id="bf472-150">**DataTable** Methods</span></span>|<span data-ttu-id="bf472-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="bf472-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="bf472-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="bf472-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="bf472-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="bf472-153">DeleteTableNameRow</span></span>|<span data-ttu-id="bf472-154">typedName</span><span class="sxs-lookup"><span data-stu-id="bf472-154">typedName</span></span>|  
|<span data-ttu-id="bf472-155">**DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="bf472-155">**DataRowCollection**</span></span>|<span data-ttu-id="bf472-156">TableName</span><span class="sxs-lookup"><span data-stu-id="bf472-156">TableName</span></span>|<span data-ttu-id="bf472-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="bf472-157">typedPlural</span></span>|  
|<span data-ttu-id="bf472-158">**Nesnesinin**</span><span class="sxs-lookup"><span data-stu-id="bf472-158">**DataRow**</span></span>|<span data-ttu-id="bf472-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="bf472-159">TableNameRow</span></span>|<span data-ttu-id="bf472-160">typedName</span><span class="sxs-lookup"><span data-stu-id="bf472-160">typedName</span></span>|  
|<span data-ttu-id="bf472-161">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="bf472-161">**DataColumn**</span></span>|<span data-ttu-id="bf472-162">DataTable. ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="bf472-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="bf472-163">DataRow. ColumnName</span><span class="sxs-lookup"><span data-stu-id="bf472-163">DataRow.ColumnName</span></span>|<span data-ttu-id="bf472-164">typedName</span><span class="sxs-lookup"><span data-stu-id="bf472-164">typedName</span></span>|  
|<span data-ttu-id="bf472-165">**Özellik**</span><span class="sxs-lookup"><span data-stu-id="bf472-165">**Property**</span></span>|<span data-ttu-id="bf472-166">ÖzellikAdı</span><span class="sxs-lookup"><span data-stu-id="bf472-166">PropertyName</span></span>|<span data-ttu-id="bf472-167">typedName</span><span class="sxs-lookup"><span data-stu-id="bf472-167">typedName</span></span>|  
|<span data-ttu-id="bf472-168">**Alt öğe** Erişimci</span><span class="sxs-lookup"><span data-stu-id="bf472-168">**Child** Accessor</span></span>|<span data-ttu-id="bf472-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="bf472-169">GetChildTableNameRows</span></span>|<span data-ttu-id="bf472-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="bf472-170">typedChildren</span></span>|  
|<span data-ttu-id="bf472-171">**Üst öğe** Erişimci</span><span class="sxs-lookup"><span data-stu-id="bf472-171">**Parent** Accessor</span></span>|<span data-ttu-id="bf472-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="bf472-172">TableNameRow</span></span>|<span data-ttu-id="bf472-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="bf472-173">typedParent</span></span>|  
|<span data-ttu-id="bf472-174">**Veri kümesi** Olayları</span><span class="sxs-lookup"><span data-stu-id="bf472-174">**DataSet** Events</span></span>|<span data-ttu-id="bf472-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="bf472-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="bf472-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="bf472-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="bf472-177">typedName</span><span class="sxs-lookup"><span data-stu-id="bf472-177">typedName</span></span>|  
  
 <span data-ttu-id="bf472-178">Türü belirtilmiş **veri kümesi** ek açıklamalarını kullanmak Için XML şeması tanım DILI (xsd) şemanıza aşağıdaki **xmlns** başvurusunu eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf472-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="bf472-179">Veritabanı tablolarından bir xsd oluşturmak için bkz <xref:System.Data.DataSet.WriteXmlSchema%2A> . [Visual Studio 'Da veri kümeleri ile çalışma](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="bf472-179">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="bf472-180">Aşağıda, **Northwind** veritabanının **Customers** tablosunu, dahil edilen **siparişler** tablosuyla bir ilişki ile kullanıma sunan örnek bir açıklamalı şema verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bf472-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""
      xmlns:xs="http://www.w3.org/2001/XMLSchema"
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone" codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order" codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"                  codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter" codegen:nullValue="1980-01-01T00:00:00"
type="xs:dateTime" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Customers" />  
      <xs:field xpath="CustomerID" />  
    </xs:unique>  
    <xs:keyref name="CustOrders" refer="Constraint1"  
codegen:typedParent="Customer" codegen:typedChildren="GetOrders">  
      <xs:selector xpath=".//Orders" />  
      <xs:field xpath="CustomerID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="bf472-181">Aşağıdaki kod örneği, örnek şemadan oluşturulan kesin türü belirtilmiş bir **veri kümesini** kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf472-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="bf472-182">Bir tane, müşteriler tablosunu doldurmak için bir tane kullanır <xref:System.Data.SqlClient.SqlDataAdapter> ve **Customers** <xref:System.Data.SqlClient.SqlDataAdapter> **Orders** tablosunu doldurmak için bir diğeri.</span><span class="sxs-lookup"><span data-stu-id="bf472-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="bf472-183">Türü kesin belirlenmiş **veri kümesi** , **DataRelation**'ı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf472-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
```vb  
' Assumes a valid SqlConnection object named connection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT CustomerID, CompanyName, Phone FROM Customers", &  
    connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders", &  
    connection)  
  
' Populate a strongly typed DataSet.  
connection.Open()  
Dim customers As CustomerDataSet = New CustomerDataSet()  
customerAdapter.Fill(customers, "Customers")  
orderAdapter.Fill(customers, "Orders")  
connection.Close()  
  
' Add a strongly typed event.  
AddHandler customers.Customers.CustomerChanged, &  
    New CustomerDataSet.CustomerChangeEventHandler( _  
    AddressOf OnCustomerChanged)  
  
' Add a strongly typed DataRow.  
Dim newCustomer As CustomerDataSet.Customer = _  
    customers.Customers.NewCustomer()  
newCustomer.CustomerID = "NEW01"  
newCustomer.CompanyName = "My New Company"  
customers.Customers.AddCustomer(newCustomer)  
  
' Navigate the child relation.  
Dim customer As CustomerDataSet.Customer  
Dim order As CustomerDataSet.Order  
  
For Each customer In customers.Customers  
  Console.WriteLine(customer.CustomerID)  
  For Each order In customer.GetOrders()  
    Console.WriteLine(vbTab & order.OrderID)  
  Next  
Next  
  
Private Shared Sub OnCustomerChanged( _  
    sender As Object, e As CustomerDataSet.CustomerChangeEvent)  
  
End Sub  
```  
  
```csharp  
// Assumes a valid SqlConnection object named connection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
    "SELECT CustomerID, CompanyName, Phone FROM Customers",  
    connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders",
    connection);  
  
// Populate a strongly typed DataSet.  
connection.Open();  
CustomerDataSet customers = new CustomerDataSet();  
customerAdapter.Fill(customers, "Customers");  
orderAdapter.Fill(customers, "Orders");  
connection.Close();  
  
// Add a strongly typed event.  
customers.Customers.CustomerChanged += new
  CustomerDataSet.CustomerChangeEventHandler(OnCustomerChanged);  
  
// Add a strongly typed DataRow.  
CustomerDataSet.Customer newCustomer =
    customers.Customers.NewCustomer();  
newCustomer.CustomerID = "NEW01";  
newCustomer.CompanyName = "My New Company";  
customers.Customers.AddCustomer(newCustomer);  
  
// Navigate the child relation.  
foreach(CustomerDataSet.Customer customer in customers.Customers)  
{  
  Console.WriteLine(customer.CustomerID);  
  foreach(CustomerDataSet.Order order in customer.GetOrders())  
    Console.WriteLine("\t" + order.OrderID);  
}  
  
protected static void OnCustomerChanged(object sender, CustomerDataSet.CustomerChangeEvent e)  
    {  
  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf472-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf472-184">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="bf472-185">Türü Belirtilmiş DataSets</span><span class="sxs-lookup"><span data-stu-id="bf472-185">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="bf472-186">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="bf472-186">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="bf472-187">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bf472-187">ADO.NET Overview</span></span>](../ado-net-overview.md)
