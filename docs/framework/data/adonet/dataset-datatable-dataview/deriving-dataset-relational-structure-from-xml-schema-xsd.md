---
title: XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 549579fca0179994191987097c12b6085ee91756
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119697"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="8f7c1-102">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="8f7c1-102">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>
<span data-ttu-id="8f7c1-103">Bu bölümde bir bakış sunulmaktadır ilişkisel şemasını bir `DataSet` bir XML Şeması Tanım Dili (XSD) şeması belgesinden oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="8f7c1-103">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="8f7c1-104">Genel olarak, her biri için `complexType` şema öğesi alt öğesi, bir tablo üretilir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="8f7c1-104">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="8f7c1-105">Tablo yapısı, karmaşık tür tanımına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="8f7c1-105">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="8f7c1-106">Tablolar oluşturulur `DataSet` şemanın en üst düzey öğeleri için.</span><span class="sxs-lookup"><span data-stu-id="8f7c1-106">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="8f7c1-107">Ancak, bir tablo yalnızca bir üst düzey için oluşturulur `complexType` öğesi olduğunda `complexType` öğesi iç içe başka içinde `complexType` öğesi, iç içe case `complexType` öğesi eşlenmiş durumda bir `DataTable` içinde `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="8f7c1-107">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="8f7c1-108">World Wide Web Consortium (W3C) XSD hakkında daha fazla bilgi için bkz [XML şema bölüm 0: İlk öneri](https://www.w3.org/TR/xmlschema-0/), [XML Şeması Kısım 1: Yapıları öneri](https://www.w3.org/TR/xmlschema-1/)ve [XML şema bölümü 2: Veri türleri öneri](https://www.w3.org/TR/xmlschema-2/).</span><span class="sxs-lookup"><span data-stu-id="8f7c1-108">For more information about the XSD, see the World Wide Web Consortium (W3C) [XML Schema Part 0: Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), the [XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/), and the [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>  
  
 <span data-ttu-id="8f7c1-109">Aşağıdaki örnek, bir XML şeması gösterir. burada `customers` bir alt öğesidir `MyDataSet` olan öğenin bir **veri kümesi** öğesi.</span><span class="sxs-lookup"><span data-stu-id="8f7c1-109">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >   
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"   
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"   
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 <span data-ttu-id="8f7c1-110">Yukarıdaki örnekte, öğe `customers` bir karmaşık tür öğedir.</span><span class="sxs-lookup"><span data-stu-id="8f7c1-110">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="8f7c1-111">Bu nedenle, karmaşık tür tanımı ayrıştırılır ve aşağıdaki tabloda eşleme işlemi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f7c1-111">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 <span data-ttu-id="8f7c1-112">Tablodaki her bir sütunun veri türü, karşılık gelen öğe veya öznitelik belirtilen XML Şeması türünden türetilir.</span><span class="sxs-lookup"><span data-stu-id="8f7c1-112">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f7c1-113">Öğe `customers` basit XML şema veri türünde olduğu gibi **tamsayı**, hiçbir tablo oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8f7c1-113">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="8f7c1-114">Tablolar, yalnızca karmaşık türler için üst düzey öğeleri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8f7c1-114">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="8f7c1-115">Aşağıdaki XML şema **şema** öğeye sahip iki alt öğesi `InStateCustomers` ve `OutOfStateCustomers`.</span><span class="sxs-lookup"><span data-stu-id="8f7c1-115">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 <span data-ttu-id="8f7c1-116">Hem `InStateCustomers` ve `OutOfStateCustomers` alt öğeleri, karmaşık tür öğe (`customerType`).</span><span class="sxs-lookup"><span data-stu-id="8f7c1-116">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="8f7c1-117">Bu nedenle, aşağıdaki iki özdeş tablolarda eşleme işlemi oluşturur `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="8f7c1-117">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="8f7c1-118">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8f7c1-118">In This Section</span></span>  
 [<span data-ttu-id="8f7c1-119">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="8f7c1-119">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="8f7c1-120">Benzersiz ve yabancı anahtar kısıtlamalarını oluşturmak için kullanılan XML Şeması öğeleri açıklar bir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="8f7c1-120">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="8f7c1-121">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8f7c1-121">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="8f7c1-122">Tablo sütunlarını arasındaki ilişkileri oluşturmak için kullanılan XML Şeması öğeleri açıklar bir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="8f7c1-122">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="8f7c1-123">XML Şema Kısıtlamaları ve İlişkileri</span><span class="sxs-lookup"><span data-stu-id="8f7c1-123">XML Schema Constraints and Relationships</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="8f7c1-124">Açıklayan nasıl ilişkileri örtük olarak kısıtlamalarını oluşturmak için XML Şeması öğeleri kullanılarak oluşturulur bir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="8f7c1-124">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8f7c1-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8f7c1-125">Related Sections</span></span>  
 [<span data-ttu-id="8f7c1-126">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="8f7c1-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="8f7c1-127">Yük ve ilişkisel yapısını ve verileri kalıcı hale açıklar bir `DataSet` XML verileri olarak.</span><span class="sxs-lookup"><span data-stu-id="8f7c1-127">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f7c1-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f7c1-128">See also</span></span>

- [<span data-ttu-id="8f7c1-129">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="8f7c1-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
