---
description: 'Hakkında daha fazla bilgi edinin: yazılan veri kümelerine açıklama ekleme'
title: Türü Belirtilmiş DataSets için Yorum Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 6f5838e94d88fd6c9b3a1991d4c8023d5892b784
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739709"
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="145a8-103">Türü Belirtilmiş DataSets için Yorum Ekleme</span><span class="sxs-lookup"><span data-stu-id="145a8-103">Annotating Typed DataSets</span></span>

<span data-ttu-id="145a8-104">Ek açıklamalar, temeldeki şemayı değiştirmeden, yazdığınız öğelerin adlarını değiştirmenize olanak sağlar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="145a8-104">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="145a8-105">Temel şemadaki öğelerin adlarını değiştirmek, yazılan veri **kümesinin** veri kaynağında mevcut olmayan nesnelere başvurmasına ve veri kaynağında var olan nesnelere yönelik bir başvuruyu kaybetmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="145a8-105">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="145a8-106">Ek açıklamaları kullanarak, yazılan **veri** kümenizdeki nesnelerin adlarını daha anlamlı adlarla özelleştirebilir, böylece kod daha okunabilir ve yazılan **Veri kümeniz** istemcilerin kullanması için daha kolay olur, temel şemayı bozulmadan bırakır.</span><span class="sxs-lookup"><span data-stu-id="145a8-106">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="145a8-107">Örneğin, **Northwind** veritabanının **Customers** tablosu için aşağıdaki şema öğesi, **CustomersRow** ve adlandırılmış müşterilerin bir **DataRow** nesne adı ile sonuçlanır <xref:System.Data.DataRowCollection> .</span><span class="sxs-lookup"><span data-stu-id="145a8-107">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="145a8-108">Müşterilerin **DataRowCollection** adı istemci  kodunda anlamlıdır, ancak tek bir nesne olduğundan **CustomersRow** **DataRow** adı yanıltıcı olur.</span><span class="sxs-lookup"><span data-stu-id="145a8-108">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="145a8-109">Ayrıca, yaygın senaryolarda nesne, **satır** tanımlayıcı olmadan, bunun yerine yalnızca bir **Müşteri** nesnesi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="145a8-109">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="145a8-110">Çözüm, şemaya açıklama eklemek ve **DataRow** ve **DataRowCollection** nesnelerinin yeni adlarını belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="145a8-110">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="145a8-111">Önceki şemanın açıklamalı sürümü aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="145a8-111">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="145a8-112">**Müşterinin** **typedName** değerini belirtmek, bir **DataRow** nesnesinin **Müşteri** adına neden olur.</span><span class="sxs-lookup"><span data-stu-id="145a8-112">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="145a8-113">**Müşteriler** Için **typedPlural** değeri belirtildiğinde **müşterilerin** **DataRowCollection** adı korunur.</span><span class="sxs-lookup"><span data-stu-id="145a8-113">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="145a8-114">Aşağıdaki tabloda kullanıma sunulan ek açıklamalar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="145a8-114">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="145a8-115">Ek Açıklama</span><span class="sxs-lookup"><span data-stu-id="145a8-115">Annotation</span></span>|<span data-ttu-id="145a8-116">Description</span><span class="sxs-lookup"><span data-stu-id="145a8-116">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="145a8-117">**typedName**</span><span class="sxs-lookup"><span data-stu-id="145a8-117">**typedName**</span></span>|<span data-ttu-id="145a8-118">Nesnenin adı.</span><span class="sxs-lookup"><span data-stu-id="145a8-118">Name of the object.</span></span>|  
|<span data-ttu-id="145a8-119">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="145a8-119">**typedPlural**</span></span>|<span data-ttu-id="145a8-120">Bir nesne koleksiyonunun adı.</span><span class="sxs-lookup"><span data-stu-id="145a8-120">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="145a8-121">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="145a8-121">**typedParent**</span></span>|<span data-ttu-id="145a8-122">Üst ilişkide başvurulduğu sırada nesnenin adı.</span><span class="sxs-lookup"><span data-stu-id="145a8-122">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="145a8-123">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="145a8-123">**typedChildren**</span></span>|<span data-ttu-id="145a8-124">Bir alt ilişkiden nesneleri döndürmek için yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="145a8-124">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="145a8-125">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="145a8-125">**nullValue**</span></span>|<span data-ttu-id="145a8-126">Temel değer **DBNull** ise değeri.</span><span class="sxs-lookup"><span data-stu-id="145a8-126">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="145a8-127">**NullValue** ek açıklamaları için aşağıdaki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="145a8-127">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="145a8-128">Varsayılan değer **_throw**.</span><span class="sxs-lookup"><span data-stu-id="145a8-128">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="145a8-129">Aşağıdaki tabloda, **NullValue** ek açıklaması için belirtime değerleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="145a8-129">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="145a8-130">nullValue değeri</span><span class="sxs-lookup"><span data-stu-id="145a8-130">nullValue Value</span></span>|<span data-ttu-id="145a8-131">Description</span><span class="sxs-lookup"><span data-stu-id="145a8-131">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="145a8-132">*Değiştirme değeri*</span><span class="sxs-lookup"><span data-stu-id="145a8-132">*Replacement Value*</span></span>|<span data-ttu-id="145a8-133">Döndürülecek bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="145a8-133">Specify a value to be returned.</span></span> <span data-ttu-id="145a8-134">Döndürülen değerin öğe türüyle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="145a8-134">The returned value must match the type of the element.</span></span> <span data-ttu-id="145a8-135">Örneğin, `nullValue="0"` null tamsayı alanları için 0 döndürmek üzere kullanın.</span><span class="sxs-lookup"><span data-stu-id="145a8-135">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="145a8-136">**_throw**</span><span class="sxs-lookup"><span data-stu-id="145a8-136">**_throw**</span></span>|<span data-ttu-id="145a8-137">Bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="145a8-137">Throw an exception.</span></span> <span data-ttu-id="145a8-138">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="145a8-138">This is the default.</span></span>|  
|<span data-ttu-id="145a8-139">**_null**</span><span class="sxs-lookup"><span data-stu-id="145a8-139">**_null**</span></span>|<span data-ttu-id="145a8-140">Bir temel tür ile karşılaşılırsa, null bir başvuru döndürün veya bir özel durum oluşturun.</span><span class="sxs-lookup"><span data-stu-id="145a8-140">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="145a8-141">**_empty**</span><span class="sxs-lookup"><span data-stu-id="145a8-141">**_empty**</span></span>|<span data-ttu-id="145a8-142">Dizeler için, **String. Empty** döndürün, aksi halde boş bir oluşturucudan oluşturulan nesneyi döndürün.</span><span class="sxs-lookup"><span data-stu-id="145a8-142">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="145a8-143">İlkel bir tür ile karşılaşılırsa bir özel durum oluşturun.</span><span class="sxs-lookup"><span data-stu-id="145a8-143">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="145a8-144">Aşağıdaki tabloda, türü belirtilmiş bir **veri kümesindeki** nesneler için varsayılan değerler ve kullanılabilir ek açıklamalar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="145a8-144">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="145a8-145">Nesne/yöntem/olay</span><span class="sxs-lookup"><span data-stu-id="145a8-145">Object/Method/Event</span></span>|<span data-ttu-id="145a8-146">Varsayılan</span><span class="sxs-lookup"><span data-stu-id="145a8-146">Default</span></span>|<span data-ttu-id="145a8-147">Ek Açıklama</span><span class="sxs-lookup"><span data-stu-id="145a8-147">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="145a8-148">**DataRow**</span><span class="sxs-lookup"><span data-stu-id="145a8-148">**DataTable**</span></span>|<span data-ttu-id="145a8-149">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="145a8-149">TableNameDataTable</span></span>|<span data-ttu-id="145a8-150">typedPlural</span><span class="sxs-lookup"><span data-stu-id="145a8-150">typedPlural</span></span>|  
|<span data-ttu-id="145a8-151">**DataTable** Yöntem</span><span class="sxs-lookup"><span data-stu-id="145a8-151">**DataTable** Methods</span></span>|<span data-ttu-id="145a8-152">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="145a8-152">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="145a8-153">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="145a8-153">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="145a8-154">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="145a8-154">DeleteTableNameRow</span></span>|<span data-ttu-id="145a8-155">typedName</span><span class="sxs-lookup"><span data-stu-id="145a8-155">typedName</span></span>|  
|<span data-ttu-id="145a8-156">**DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="145a8-156">**DataRowCollection**</span></span>|<span data-ttu-id="145a8-157">TableName</span><span class="sxs-lookup"><span data-stu-id="145a8-157">TableName</span></span>|<span data-ttu-id="145a8-158">typedPlural</span><span class="sxs-lookup"><span data-stu-id="145a8-158">typedPlural</span></span>|  
|<span data-ttu-id="145a8-159">**Nesnesinin**</span><span class="sxs-lookup"><span data-stu-id="145a8-159">**DataRow**</span></span>|<span data-ttu-id="145a8-160">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="145a8-160">TableNameRow</span></span>|<span data-ttu-id="145a8-161">typedName</span><span class="sxs-lookup"><span data-stu-id="145a8-161">typedName</span></span>|  
|<span data-ttu-id="145a8-162">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="145a8-162">**DataColumn**</span></span>|<span data-ttu-id="145a8-163">DataTable. ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="145a8-163">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="145a8-164">DataRow. ColumnName</span><span class="sxs-lookup"><span data-stu-id="145a8-164">DataRow.ColumnName</span></span>|<span data-ttu-id="145a8-165">typedName</span><span class="sxs-lookup"><span data-stu-id="145a8-165">typedName</span></span>|  
|<span data-ttu-id="145a8-166">**Özellik**</span><span class="sxs-lookup"><span data-stu-id="145a8-166">**Property**</span></span>|<span data-ttu-id="145a8-167">ÖzellikAdı</span><span class="sxs-lookup"><span data-stu-id="145a8-167">PropertyName</span></span>|<span data-ttu-id="145a8-168">typedName</span><span class="sxs-lookup"><span data-stu-id="145a8-168">typedName</span></span>|  
|<span data-ttu-id="145a8-169">**Alt öğe** Erişimci</span><span class="sxs-lookup"><span data-stu-id="145a8-169">**Child** Accessor</span></span>|<span data-ttu-id="145a8-170">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="145a8-170">GetChildTableNameRows</span></span>|<span data-ttu-id="145a8-171">typedChildren</span><span class="sxs-lookup"><span data-stu-id="145a8-171">typedChildren</span></span>|  
|<span data-ttu-id="145a8-172">**Üst öğe** Erişimci</span><span class="sxs-lookup"><span data-stu-id="145a8-172">**Parent** Accessor</span></span>|<span data-ttu-id="145a8-173">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="145a8-173">TableNameRow</span></span>|<span data-ttu-id="145a8-174">typedParent</span><span class="sxs-lookup"><span data-stu-id="145a8-174">typedParent</span></span>|  
|<span data-ttu-id="145a8-175">**Veri kümesi** Olayları</span><span class="sxs-lookup"><span data-stu-id="145a8-175">**DataSet** Events</span></span>|<span data-ttu-id="145a8-176">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="145a8-176">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="145a8-177">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="145a8-177">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="145a8-178">typedName</span><span class="sxs-lookup"><span data-stu-id="145a8-178">typedName</span></span>|  
  
 <span data-ttu-id="145a8-179">Türü belirtilmiş **veri kümesi** ek açıklamalarını kullanmak Için XML şeması tanım DILI (xsd) şemanıza aşağıdaki **xmlns** başvurusunu eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="145a8-179">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="145a8-180">Veritabanı tablolarından bir xsd oluşturmak için bkz <xref:System.Data.DataSet.WriteXmlSchema%2A> . [Visual Studio 'Da veri kümeleri ile çalışma](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="145a8-180">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="145a8-181">Aşağıda, **Northwind** veritabanının **Customers** tablosunu, dahil edilen **siparişler** tablosuyla bir ilişki ile kullanıma sunan örnek bir açıklamalı şema verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="145a8-181">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
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
  
 <span data-ttu-id="145a8-182">Aşağıdaki kod örneği, örnek şemadan oluşturulan kesin türü belirtilmiş bir **veri kümesini** kullanır.</span><span class="sxs-lookup"><span data-stu-id="145a8-182">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="145a8-183">Bir tane, müşteriler tablosunu doldurmak için bir tane kullanır <xref:System.Data.SqlClient.SqlDataAdapter> ve  <xref:System.Data.SqlClient.SqlDataAdapter> **Orders** tablosunu doldurmak için bir diğeri.</span><span class="sxs-lookup"><span data-stu-id="145a8-183">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="145a8-184">Türü kesin belirlenmiş **veri kümesi** , **DataRelation**'ı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="145a8-184">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="145a8-185">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="145a8-185">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="145a8-186">Türü Belirtilmiş DataSets</span><span class="sxs-lookup"><span data-stu-id="145a8-186">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="145a8-187">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="145a8-187">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="145a8-188">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="145a8-188">ADO.NET Overview</span></span>](../ado-net-overview.md)
