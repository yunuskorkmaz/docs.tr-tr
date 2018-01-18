---
title: "Yazılan veri kümeleri yorumlama"
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
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cc09f3f9b43b70b7f9b302d7a9d75428b5a0e6c7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="884df-102">Yazılan veri kümeleri yorumlama</span><span class="sxs-lookup"><span data-stu-id="884df-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="884df-103">Ek açıklamalar, yazılı öğeleri adlarını değiştirmek etkinleştirme <xref:System.Data.DataSet> temel şeması değiştirmeden.</span><span class="sxs-lookup"><span data-stu-id="884df-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="884df-104">Temel alınan şemanızı öğeleri adları değiştirilmesi neden yazılı **DataSet** değil veri kaynağında mevcut yanı sıra veri kaynağında mevcut nesneleri başvuru kaybetmek nesneleri başvurmak için.</span><span class="sxs-lookup"><span data-stu-id="884df-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="884df-105">Ek açıklamalarını kullanma, nesnelerin adlarını, yazılı özelleştirebileceğiniz **DataSet** daha anlamlı adlarıyla kodunu daha okunabilir ve, yazılan hale **DataSet** bırakarak kullanmak istemcileri için daha kolay temel alınan şema kalır.</span><span class="sxs-lookup"><span data-stu-id="884df-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="884df-106">Örneğin, aşağıdaki schema öğesi için **müşteriler** tablosu **Northwind** veritabanı sonuçlanacak bir **DataRow** nesne adını  **CustomersRow** ve <xref:System.Data.DataRowCollection> adlı **müşteriler**.</span><span class="sxs-lookup"><span data-stu-id="884df-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="884df-107">A **DataRowCollection** adını **müşteriler** istemci kodda anlamlı ancak **DataRow** adını **CustomersRow** yanıltıcıdır tek bir nesne olduğundan.</span><span class="sxs-lookup"><span data-stu-id="884df-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="884df-108">Ayrıca, ortak senaryolar, nesne için olmadan başvurulabilir **satır** tanımlayıcısı ve bunun yerine yalnızca olarak adlandırılan bir **müşteri** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="884df-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="884df-109">Şema açıklama eklemek ve yeni adlarını tanımlamak için çözümdür **DataRow** ve **DataRowCollection** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="884df-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="884df-110">Aşağıdaki önceki şema açıklamalı sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="884df-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="884df-111">Belirten bir **typedName** değerini **müşteri** sonuçlanır bir **DataRow** nesne adını **müşteri**.</span><span class="sxs-lookup"><span data-stu-id="884df-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="884df-112">Belirten bir **typedPlural** değerini **müşteriler** korur **DataRowCollection** adını **müşteriler**.</span><span class="sxs-lookup"><span data-stu-id="884df-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="884df-113">Aşağıdaki tabloda kullanılabilir ek açıklamaları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="884df-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="884df-114">Ek Açıklama</span><span class="sxs-lookup"><span data-stu-id="884df-114">Annotation</span></span>|<span data-ttu-id="884df-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="884df-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="884df-116">**typedName**</span><span class="sxs-lookup"><span data-stu-id="884df-116">**typedName**</span></span>|<span data-ttu-id="884df-117">Nesnenin adı.</span><span class="sxs-lookup"><span data-stu-id="884df-117">Name of the object.</span></span>|  
|<span data-ttu-id="884df-118">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="884df-118">**typedPlural**</span></span>|<span data-ttu-id="884df-119">Nesne koleksiyonu adı.</span><span class="sxs-lookup"><span data-stu-id="884df-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="884df-120">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="884df-120">**typedParent**</span></span>|<span data-ttu-id="884df-121">Bir üst ilişkisinde başvurulan zaman nesnesinin adı.</span><span class="sxs-lookup"><span data-stu-id="884df-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="884df-122">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="884df-122">**typedChildren**</span></span>|<span data-ttu-id="884df-123">Alt ilişkisi nesneleri döndürmek için yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="884df-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="884df-124">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="884df-124">**nullValue**</span></span>|<span data-ttu-id="884df-125">Temel alınan değer ise değer **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="884df-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="884df-126">İçin aşağıdaki tabloya bakın **nullValue** ek açıklamaları.</span><span class="sxs-lookup"><span data-stu-id="884df-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="884df-127">Varsayılan değer **_throw**.</span><span class="sxs-lookup"><span data-stu-id="884df-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="884df-128">İçin belirtilen değerler aşağıdaki tabloda gösterilmektedir **nullValue** ek açıklama.</span><span class="sxs-lookup"><span data-stu-id="884df-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="884df-129">nullValue değeri</span><span class="sxs-lookup"><span data-stu-id="884df-129">nullValue Value</span></span>|<span data-ttu-id="884df-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="884df-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="884df-131">*Değiştirme değeri*</span><span class="sxs-lookup"><span data-stu-id="884df-131">*Replacement Value*</span></span>|<span data-ttu-id="884df-132">Döndürülecek bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="884df-132">Specify a value to be returned.</span></span> <span data-ttu-id="884df-133">Döndürülen değerin öğe türü eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="884df-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="884df-134">Örneğin, `nullValue="0"` null tamsayı alanlar için 0 dönün.</span><span class="sxs-lookup"><span data-stu-id="884df-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="884df-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="884df-135">**_throw**</span></span>|<span data-ttu-id="884df-136">Bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="884df-136">Throw an exception.</span></span> <span data-ttu-id="884df-137">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="884df-137">This is the default.</span></span>|  
|<span data-ttu-id="884df-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="884df-138">**_null**</span></span>|<span data-ttu-id="884df-139">Bir null başvuru dönün veya basit tür karşılaşılırsa, bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="884df-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="884df-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="884df-140">**_empty**</span></span>|<span data-ttu-id="884df-141">Dizeler için iade **String.Empty**, aksi takdirde boş oluşturucudan oluşturulan bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="884df-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="884df-142">Basit tür karşılaşılırsa, bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="884df-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="884df-143">Aşağıdaki tabloda nesneler için varsayılan değerleri yazılmış bir gösterilmektedir **DataSet** ve kullanılabilir ek açıklamaları.</span><span class="sxs-lookup"><span data-stu-id="884df-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="884df-144">Yöntem/nesnesi/olayı</span><span class="sxs-lookup"><span data-stu-id="884df-144">Object/Method/Event</span></span>|<span data-ttu-id="884df-145">Varsayılan</span><span class="sxs-lookup"><span data-stu-id="884df-145">Default</span></span>|<span data-ttu-id="884df-146">Ek Açıklama</span><span class="sxs-lookup"><span data-stu-id="884df-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="884df-147">**DataTable**</span><span class="sxs-lookup"><span data-stu-id="884df-147">**DataTable**</span></span>|<span data-ttu-id="884df-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="884df-148">TableNameDataTable</span></span>|<span data-ttu-id="884df-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="884df-149">typedPlural</span></span>|  
|<span data-ttu-id="884df-150">**DataTable** yöntemleri</span><span class="sxs-lookup"><span data-stu-id="884df-150">**DataTable** Methods</span></span>|<span data-ttu-id="884df-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="884df-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="884df-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="884df-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="884df-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="884df-153">DeleteTableNameRow</span></span>|<span data-ttu-id="884df-154">typedName</span><span class="sxs-lookup"><span data-stu-id="884df-154">typedName</span></span>|  
|<span data-ttu-id="884df-155">**DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="884df-155">**DataRowCollection**</span></span>|<span data-ttu-id="884df-156">TableName</span><span class="sxs-lookup"><span data-stu-id="884df-156">TableName</span></span>|<span data-ttu-id="884df-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="884df-157">typedPlural</span></span>|  
|<span data-ttu-id="884df-158">**DataRow**</span><span class="sxs-lookup"><span data-stu-id="884df-158">**DataRow**</span></span>|<span data-ttu-id="884df-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="884df-159">TableNameRow</span></span>|<span data-ttu-id="884df-160">typedName</span><span class="sxs-lookup"><span data-stu-id="884df-160">typedName</span></span>|  
|<span data-ttu-id="884df-161">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="884df-161">**DataColumn**</span></span>|<span data-ttu-id="884df-162">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="884df-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="884df-163">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="884df-163">DataRow.ColumnName</span></span>|<span data-ttu-id="884df-164">typedName</span><span class="sxs-lookup"><span data-stu-id="884df-164">typedName</span></span>|  
|<span data-ttu-id="884df-165">**Özelliği**</span><span class="sxs-lookup"><span data-stu-id="884df-165">**Property**</span></span>|<span data-ttu-id="884df-166">ÖzellikAdı</span><span class="sxs-lookup"><span data-stu-id="884df-166">PropertyName</span></span>|<span data-ttu-id="884df-167">typedName</span><span class="sxs-lookup"><span data-stu-id="884df-167">typedName</span></span>|  
|<span data-ttu-id="884df-168">**Alt** erişimcisi</span><span class="sxs-lookup"><span data-stu-id="884df-168">**Child** Accessor</span></span>|<span data-ttu-id="884df-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="884df-169">GetChildTableNameRows</span></span>|<span data-ttu-id="884df-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="884df-170">typedChildren</span></span>|  
|<span data-ttu-id="884df-171">**Üst** erişimcisi</span><span class="sxs-lookup"><span data-stu-id="884df-171">**Parent** Accessor</span></span>|<span data-ttu-id="884df-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="884df-172">TableNameRow</span></span>|<span data-ttu-id="884df-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="884df-173">typedParent</span></span>|  
|<span data-ttu-id="884df-174">**Veri kümesi** olayları</span><span class="sxs-lookup"><span data-stu-id="884df-174">**DataSet** Events</span></span>|<span data-ttu-id="884df-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="884df-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="884df-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="884df-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="884df-177">typedName</span><span class="sxs-lookup"><span data-stu-id="884df-177">typedName</span></span>|  
  
 <span data-ttu-id="884df-178">Kullanmak için yazılan **DataSet** ek açıklamalar, aşağıdaki içermelidir **xmlns** XML Şeması Tanım Dili (XSD) şeması başvurusu.</span><span class="sxs-lookup"><span data-stu-id="884df-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="884df-179">(Bir xsd veritabanı tablolarından oluşturmak için bkz: <xref:System.Data.DataSet.WriteXmlSchema%2A> veya [Visual Studio'da veri kümeleriyle çalışma](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span><span class="sxs-lookup"><span data-stu-id="884df-179">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span></span>  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="884df-180">Gösteren bir örnek açıklamalı şeması aşağıdadır **müşteriler** tablosu **Northwind** bir ilişkisine sahip veritabanı **siparişleri** dahil tablo.</span><span class="sxs-lookup"><span data-stu-id="884df-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
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
  
 <span data-ttu-id="884df-181">Aşağıdaki kod örneğinde kesin türü belirtilmiş kullanan **DataSet** örnek şemadan oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="884df-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="884df-182">Bir kullanan <xref:System.Data.SqlClient.SqlDataAdapter> doldurmak için **müşteriler** tablo ve başka <xref:System.Data.SqlClient.SqlDataAdapter> doldurmak için **siparişleri** tablo.</span><span class="sxs-lookup"><span data-stu-id="884df-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="884df-183">Kesin türü belirtilmiş **DataSet** tanımlar **DataRelations**.</span><span class="sxs-lookup"><span data-stu-id="884df-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
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
    customers.Customers.NewCustomeromer()  
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
    customers.Customers.NewCustomeromer();  
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
  
## <a name="see-also"></a><span data-ttu-id="884df-184">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="884df-184">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="884df-185">Türü Belirtilmiş DataSets</span><span class="sxs-lookup"><span data-stu-id="884df-185">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="884df-186">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="884df-186">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="884df-187">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="884df-187">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
