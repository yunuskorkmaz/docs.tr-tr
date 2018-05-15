---
title: Türetilen DataSet ilişkisel yapısından XML Şeması (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 7599577c4e0f485e336e7f79a6c3bd17f0f0c316
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="5e008-102">Türetilen DataSet ilişkisel yapısından XML Şeması (XSD)</span><span class="sxs-lookup"><span data-stu-id="5e008-102">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>
<span data-ttu-id="5e008-103">Bu bölüm, nasıl bir bakış sağlar ve ilişkisel şema bir `DataSet` XML Şeması Tanım Dili (XSD) şema belgesi yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="5e008-103">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="5e008-104">Genel olarak, her biri için `complexType` şema öğesinin alt öğesi, bir tablo üretilir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="5e008-104">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="5e008-105">Tablo yapısı karmaşık tür tanımı tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="5e008-105">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="5e008-106">Tabloları oluşturulan `DataSet` şemanın en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="5e008-106">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="5e008-107">Ancak, bir tablo yalnızca bir üst düzey için oluşturulan `complexType` öğesi zaman `complexType` öğesiyle başka içe `complexType` öğesi, iç içe durumda `complexType` öğesi eşleştirilir bir `DataTable` içinde `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="5e008-107">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="5e008-108">World Wide Web Konsorsiyumu (W3C) XML Şeması bölümü 0 XSD hakkında daha fazla bilgi için bkz: Primer öneri, XML Şeması Kısım 1: yapıları öneri ve XML Şeması Kısım 2: veri türleri öneri, konumunda bulunan [ http://www.w3.org/ ](http://www.w3.org/TR/).</span><span class="sxs-lookup"><span data-stu-id="5e008-108">For more information about the XSD, see the World Wide Web Consortium (W3C) XML Schema Part 0: Primer Recommendation, the XML Schema Part 1: Structures Recommendation, and the XML Schema Part 2: Datatypes Recommendation, located at [http://www.w3.org/](http://www.w3.org/TR/).</span></span>  
  
 <span data-ttu-id="5e008-109">Aşağıdaki örnek, bir XML şeması gösterir nerede `customers` alt öğenin `MyDataSet` olan öğenin bir **DataSet** öğesi.</span><span class="sxs-lookup"><span data-stu-id="5e008-109">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
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
  
 <span data-ttu-id="5e008-110">Önceki örnekte, öğe `customers` bir karmaşık tür öğedir.</span><span class="sxs-lookup"><span data-stu-id="5e008-110">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="5e008-111">Bu nedenle, karmaşık tür tanımı ayrıştırılır ve aşağıdaki tabloda eşleme işlemi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5e008-111">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 <span data-ttu-id="5e008-112">Tablodaki her sütun veri türü karşılık gelen öğe veya öznitelik belirtilen XML Şeması türünden türetilir.</span><span class="sxs-lookup"><span data-stu-id="5e008-112">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e008-113">Varsa öğe `customers` olduğu gibi basit bir XML Şeması veri türünü **tamsayı**, hiçbir tablo oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5e008-113">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="5e008-114">Tabloları yalnızca karmaşık türler için üst düzey öğeleri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5e008-114">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="5e008-115">Aşağıdaki XML şemasında **şema** öğeye sahip iki alt öğesi `InStateCustomers` ve `OutOfStateCustomers`.</span><span class="sxs-lookup"><span data-stu-id="5e008-115">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
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
  
 <span data-ttu-id="5e008-116">Hem `InStateCustomers` ve `OutOfStateCustomers` alt öğeleri olan karmaşık tür öğeleri (`customerType`).</span><span class="sxs-lookup"><span data-stu-id="5e008-116">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="5e008-117">Bu nedenle, aşağıdaki iki özdeş Tablo eşleme işlemi oluşturur `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="5e008-117">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="5e008-118">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5e008-118">In This Section</span></span>  
 [<span data-ttu-id="5e008-119">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="5e008-119">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="5e008-120">Benzersiz ve yabancı anahtar kısıtlamalarını oluşturmak için kullanılan XML şema öğeleri açıklayan bir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="5e008-120">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="5e008-121">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5e008-121">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="5e008-122">Tablo sütunları arasındaki ilişkileri oluşturmak için kullanılan XML Şeması öğelerini açıklar bir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="5e008-122">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="5e008-123">XML Şema Kısıtlamaları ve İlişkileri</span><span class="sxs-lookup"><span data-stu-id="5e008-123">XML Schema Constraints and Relationships</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="5e008-124">Nasıl ilişkileri örtük olarak XML şema öğeleri kısıtlamalar oluşturmak için kullanırken oluşturulduğunu açıklayan bir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="5e008-124">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5e008-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="5e008-125">Related Sections</span></span>  
 [<span data-ttu-id="5e008-126">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="5e008-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="5e008-127">Yük ve ilişkisel yapısı ve verilerde kalıcı açıklar bir `DataSet` XML verileri olarak.</span><span class="sxs-lookup"><span data-stu-id="5e008-127">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e008-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e008-128">See Also</span></span>  
 [<span data-ttu-id="5e008-129">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="5e008-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
