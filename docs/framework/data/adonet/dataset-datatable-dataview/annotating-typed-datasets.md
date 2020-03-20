---
title: Türü Belirtilmiş DataSets için Yorum Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 757a87f92d8dc6049de1844fed892d95dc57c990
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151526"
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="99e9f-102">Türü Belirtilmiş DataSets için Yorum Ekleme</span><span class="sxs-lookup"><span data-stu-id="99e9f-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="99e9f-103">Ek açıklamalar, temel şemayı değiştirmeden yazdığınız <xref:System.Data.DataSet> öğelerin adlarını değiştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="99e9f-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="99e9f-104">Temel şemanızdaki öğelerin adlarını değiştirmek, yazılan **DataSet'in** veri kaynağında bulunmayan nesnelere başvurmasının yanı sıra veri kaynağında bulunan nesnelere başvuruda bulunmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="99e9f-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="99e9f-105">Ek açıklamaları kullanarak, yazdığınız **DataSet'teki** nesnelerin adlarını daha anlamlı adlarla özelleştirerek kodu daha okunabilir hale getirebilir ve dakti-skar lı **DataSet'inizi** istemcilerin kullanmasını kolaylaştırırken, altta yatan şemayı bozulmadan bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99e9f-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="99e9f-106">Örneğin, **Northwind** veritabanının **Müşteriler** tablosu için aşağıdaki şema **öğesi, CustomersRow'un** DataRow <xref:System.Data.DataRowCollection> nesne adı ve adlandırılmış **Müşteriler'in**bir **veritabanıyla** sonuçlanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="99e9f-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="99e9f-107">**Müşterilerin** **DataRowCollection** adı istemci kodunda anlamlıdır, ancak Tek bir nesne olduğu için **CustomersRow'un** **DataRow** adı yanıltıcıdır.</span><span class="sxs-lookup"><span data-stu-id="99e9f-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="99e9f-108">Ayrıca, yaygın senaryolarda, nesne **Satır** tanımlayıcısı olmadan başvurulur ve bunun yerine yalnızca **müşteri** nesnesi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="99e9f-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="99e9f-109">Çözüm şemayı açıklama yapmak ve DataRow ve **DataRowCollection** nesneleri **DataRowCollection** için yeni adlar tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="99e9f-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="99e9f-110">Aşağıda önceki şema açıklamalı sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="99e9f-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="99e9f-111">**Müşterinin** **daktibName** değerinin belirtilmesi, **Müşterinin** **DataRow** nesne adı ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="99e9f-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="99e9f-112">**Müşterilerin** **daktibÇoğul** değerini **belirtmek, Müşterilerin** **DataRowCollection** adını korur.</span><span class="sxs-lookup"><span data-stu-id="99e9f-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="99e9f-113">Aşağıdaki tabloda kullanılabilir ek açıklamalar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="99e9f-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="99e9f-114">Ek Açıklama</span><span class="sxs-lookup"><span data-stu-id="99e9f-114">Annotation</span></span>|<span data-ttu-id="99e9f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99e9f-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="99e9f-116">**typedName**</span><span class="sxs-lookup"><span data-stu-id="99e9f-116">**typedName**</span></span>|<span data-ttu-id="99e9f-117">Nesnenin adı.</span><span class="sxs-lookup"><span data-stu-id="99e9f-117">Name of the object.</span></span>|  
|<span data-ttu-id="99e9f-118">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="99e9f-118">**typedPlural**</span></span>|<span data-ttu-id="99e9f-119">Nesneler koleksiyonunun adı.</span><span class="sxs-lookup"><span data-stu-id="99e9f-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="99e9f-120">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="99e9f-120">**typedParent**</span></span>|<span data-ttu-id="99e9f-121">Üst ilişkide atıfta bulunulduğunda nesnenin adı.</span><span class="sxs-lookup"><span data-stu-id="99e9f-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="99e9f-122">**daktioÇocuklar**</span><span class="sxs-lookup"><span data-stu-id="99e9f-122">**typedChildren**</span></span>|<span data-ttu-id="99e9f-123">Alt ilişkiden nesneleri döndürmek için yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="99e9f-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="99e9f-124">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="99e9f-124">**nullValue**</span></span>|<span data-ttu-id="99e9f-125">Temel değer **DBNull**ise değer.</span><span class="sxs-lookup"><span data-stu-id="99e9f-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="99e9f-126">**NullValue** ek açıklamaları için aşağıdaki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="99e9f-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="99e9f-127">Varsayılan **_throw.**</span><span class="sxs-lookup"><span data-stu-id="99e9f-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="99e9f-128">Aşağıdaki **tablo, nullValue** ek açıklama için belirtilen değerleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="99e9f-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="99e9f-129">nullValue Değeri</span><span class="sxs-lookup"><span data-stu-id="99e9f-129">nullValue Value</span></span>|<span data-ttu-id="99e9f-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99e9f-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="99e9f-131">*Değiştirme Değeri*</span><span class="sxs-lookup"><span data-stu-id="99e9f-131">*Replacement Value*</span></span>|<span data-ttu-id="99e9f-132">Döndürülecek bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="99e9f-132">Specify a value to be returned.</span></span> <span data-ttu-id="99e9f-133">Döndürülen değer öğenin türüyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="99e9f-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="99e9f-134">Örneğin, null `nullValue="0"` integer alanları için 0 döndürmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="99e9f-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="99e9f-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="99e9f-135">**_throw**</span></span>|<span data-ttu-id="99e9f-136">Bir istisna at.</span><span class="sxs-lookup"><span data-stu-id="99e9f-136">Throw an exception.</span></span> <span data-ttu-id="99e9f-137">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="99e9f-137">This is the default.</span></span>|  
|<span data-ttu-id="99e9f-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="99e9f-138">**_null**</span></span>|<span data-ttu-id="99e9f-139">İlkel bir türle karşılaşılırsa, null başvurusu döndürün veya özel durum atın.</span><span class="sxs-lookup"><span data-stu-id="99e9f-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="99e9f-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="99e9f-140">**_empty**</span></span>|<span data-ttu-id="99e9f-141">Dizeleri için **String.Empty'ı**döndürün, aksi takdirde boş bir oluşturucudan oluşturulan bir nesneyi döndürün.</span><span class="sxs-lookup"><span data-stu-id="99e9f-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="99e9f-142">İlkel bir türle karşılaşılırsa, bir özel durum atın.</span><span class="sxs-lookup"><span data-stu-id="99e9f-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="99e9f-143">Aşağıdaki tablo, dakti-yazılı **DataSet'teki** nesneler ve kullanılabilir ek açıklamalar için varsayılan değerleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="99e9f-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="99e9f-144">Nesne/Yöntem/Olay</span><span class="sxs-lookup"><span data-stu-id="99e9f-144">Object/Method/Event</span></span>|<span data-ttu-id="99e9f-145">Varsayılan</span><span class="sxs-lookup"><span data-stu-id="99e9f-145">Default</span></span>|<span data-ttu-id="99e9f-146">Ek Açıklama</span><span class="sxs-lookup"><span data-stu-id="99e9f-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="99e9f-147">**Datatable**</span><span class="sxs-lookup"><span data-stu-id="99e9f-147">**DataTable**</span></span>|<span data-ttu-id="99e9f-148">Tablo AdıDataTable</span><span class="sxs-lookup"><span data-stu-id="99e9f-148">TableNameDataTable</span></span>|<span data-ttu-id="99e9f-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="99e9f-149">typedPlural</span></span>|  
|<span data-ttu-id="99e9f-150">**Veri Tablosu** Yöntemler</span><span class="sxs-lookup"><span data-stu-id="99e9f-150">**DataTable** Methods</span></span>|<span data-ttu-id="99e9f-151">YeniTableNameRow</span><span class="sxs-lookup"><span data-stu-id="99e9f-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="99e9f-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="99e9f-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="99e9f-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="99e9f-153">DeleteTableNameRow</span></span>|<span data-ttu-id="99e9f-154">typedName</span><span class="sxs-lookup"><span data-stu-id="99e9f-154">typedName</span></span>|  
|<span data-ttu-id="99e9f-155">**Datarowcollection**</span><span class="sxs-lookup"><span data-stu-id="99e9f-155">**DataRowCollection**</span></span>|<span data-ttu-id="99e9f-156">TableName</span><span class="sxs-lookup"><span data-stu-id="99e9f-156">TableName</span></span>|<span data-ttu-id="99e9f-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="99e9f-157">typedPlural</span></span>|  
|<span data-ttu-id="99e9f-158">**Datarow**</span><span class="sxs-lookup"><span data-stu-id="99e9f-158">**DataRow**</span></span>|<span data-ttu-id="99e9f-159">TabloNameSatırı</span><span class="sxs-lookup"><span data-stu-id="99e9f-159">TableNameRow</span></span>|<span data-ttu-id="99e9f-160">typedName</span><span class="sxs-lookup"><span data-stu-id="99e9f-160">typedName</span></span>|  
|<span data-ttu-id="99e9f-161">**Datacolumn**</span><span class="sxs-lookup"><span data-stu-id="99e9f-161">**DataColumn**</span></span>|<span data-ttu-id="99e9f-162">DataTable.ColumnName</span><span class="sxs-lookup"><span data-stu-id="99e9f-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="99e9f-163">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="99e9f-163">DataRow.ColumnName</span></span>|<span data-ttu-id="99e9f-164">typedName</span><span class="sxs-lookup"><span data-stu-id="99e9f-164">typedName</span></span>|  
|<span data-ttu-id="99e9f-165">**Özellik**</span><span class="sxs-lookup"><span data-stu-id="99e9f-165">**Property**</span></span>|<span data-ttu-id="99e9f-166">ÖzellikAdı</span><span class="sxs-lookup"><span data-stu-id="99e9f-166">PropertyName</span></span>|<span data-ttu-id="99e9f-167">typedName</span><span class="sxs-lookup"><span data-stu-id="99e9f-167">typedName</span></span>|  
|<span data-ttu-id="99e9f-168">**Çocuk** Erişeni</span><span class="sxs-lookup"><span data-stu-id="99e9f-168">**Child** Accessor</span></span>|<span data-ttu-id="99e9f-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="99e9f-169">GetChildTableNameRows</span></span>|<span data-ttu-id="99e9f-170">daktioÇocuklar</span><span class="sxs-lookup"><span data-stu-id="99e9f-170">typedChildren</span></span>|  
|<span data-ttu-id="99e9f-171">**Ebeveyn** Erişeni</span><span class="sxs-lookup"><span data-stu-id="99e9f-171">**Parent** Accessor</span></span>|<span data-ttu-id="99e9f-172">TabloNameSatırı</span><span class="sxs-lookup"><span data-stu-id="99e9f-172">TableNameRow</span></span>|<span data-ttu-id="99e9f-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="99e9f-173">typedParent</span></span>|  
|<span data-ttu-id="99e9f-174">**Veri Seti** Olay</span><span class="sxs-lookup"><span data-stu-id="99e9f-174">**DataSet** Events</span></span>|<span data-ttu-id="99e9f-175">TabloNameSatır Değiştirme Etkinliği</span><span class="sxs-lookup"><span data-stu-id="99e9f-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="99e9f-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="99e9f-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="99e9f-177">typedName</span><span class="sxs-lookup"><span data-stu-id="99e9f-177">typedName</span></span>|  
  
 <span data-ttu-id="99e9f-178">Yazılı **DataSet** ek açıklamalarını kullanmak için, XML Şema tanım dili (XSD) şemanıza aşağıdaki **xmlns** başvurularını eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="99e9f-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="99e9f-179">Veritabanı tablolarından bir xsd <xref:System.Data.DataSet.WriteXmlSchema%2A> oluşturmak için Visual Studio'da Datasets'e bakın veya [Veri Kümeleriyle Çalışma'ya bakın.](/visualstudio/data-tools/dataset-tools-in-visual-studio)</span><span class="sxs-lookup"><span data-stu-id="99e9f-179">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="99e9f-180">Aşağıda, **Northwind** veritabanının **Müşteriler** tablosunu **Siparişler** tablosuyla ilgili olarak ortaya çıkaran örnek açıklamalı şema yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="99e9f-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
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
  
 <span data-ttu-id="99e9f-181">Aşağıdaki kod örneği, örnek şemadan oluşturulan güçlü bir şekilde yazılan bir **DataSet** kullanır.</span><span class="sxs-lookup"><span data-stu-id="99e9f-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="99e9f-182"><xref:System.Data.SqlClient.SqlDataAdapter> Biri **Müşteriler** tablosunu doldurmak için, <xref:System.Data.SqlClient.SqlDataAdapter> diğeri de **Siparişler** tablosunu doldurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="99e9f-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="99e9f-183">Güçlü bir şekilde yazılan **DataSet,** **DataRelations'ı**tanımlar.</span><span class="sxs-lookup"><span data-stu-id="99e9f-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="99e9f-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99e9f-184">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="99e9f-185">Türü Belirtilmiş DataSets</span><span class="sxs-lookup"><span data-stu-id="99e9f-185">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="99e9f-186">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="99e9f-186">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="99e9f-187">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="99e9f-187">ADO.NET Overview</span></span>](../ado-net-overview.md)
