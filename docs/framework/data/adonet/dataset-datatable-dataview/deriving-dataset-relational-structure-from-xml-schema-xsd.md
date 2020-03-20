---
title: XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: d32b5cb86bc5a138f9a5f438629d8e231be4ba94
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151175"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="baa99-102">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="baa99-102">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>
<span data-ttu-id="baa99-103">Bu bölümde, bir XML Şema tanım `DataSet` dili (XSD) şema belgesinden bir ilişkin şema nasıl oluşturulmuş bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="baa99-103">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="baa99-104">Genel olarak, `complexType` şema öğesinin her alt öğesi için, `DataSet`bir tablo oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="baa99-104">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="baa99-105">Tablo yapısı karmaşık türün tanımına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="baa99-105">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="baa99-106">Tablolar şemada `DataSet` üst düzey öğeler için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="baa99-106">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="baa99-107">Ancak, bir tablo yalnızca bir üst `complexType` düzey `complexType` öğe için, öğe `complexType` başka bir öğenin `complexType` içine iç içe geçtiğinde `DataTable` oluşturulur `DataSet`ve bu durumda iç içe olan öğe bir öğenin içinde eşlenir.</span><span class="sxs-lookup"><span data-stu-id="baa99-107">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="baa99-108">XSD hakkında daha fazla bilgi için, World Wide Web Konsorsiyumu (W3C) [XML Şema Bölüm 0: Primer Önerisi,](https://www.w3.org/TR/xmlschema-0/) [XML Şema Bölüm 1: Yapılar Önerisi](https://www.w3.org/TR/xmlschema-1/)ve [XML Şema Bölüm 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="baa99-108">For more information about the XSD, see the World Wide Web Consortium (W3C) [XML Schema Part 0: Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), the [XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/), and the [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>  
  
 <span data-ttu-id="baa99-109">Aşağıdaki örnek, bir **DataSet** öğesi `customers` olan `MyDataSet` öğenin alt öğesi nin nerede olduğunu bir XML Şeması gösterir.</span><span class="sxs-lookup"><span data-stu-id="baa99-109">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
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
  
 <span data-ttu-id="baa99-110">Önceki örnekte, öğe `customers` karmaşık bir tür öğesidir.</span><span class="sxs-lookup"><span data-stu-id="baa99-110">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="baa99-111">Bu nedenle, karmaşık tür tanımı ayrıştırılır ve eşleme işlemi aşağıdaki tabloyu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="baa99-111">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="baa99-112">Tablodaki her sütunun veri türü, belirtilen ilgili öğenin veya özniteliğin XML Şema türünden türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="baa99-112">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="baa99-113">Eleman `customers` **tamsayı**gibi basit bir XML Şema veri türüne aitse, tablo oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="baa99-113">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="baa99-114">Tablolar yalnızca karmaşık türleri olan üst düzey öğeler için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="baa99-114">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="baa99-115">Aşağıdaki XML Şeması'nda **Şema** öğesiiki öğe li `InStateCustomers` ve `OutOfStateCustomers`.</span><span class="sxs-lookup"><span data-stu-id="baa99-115">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
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
  
 <span data-ttu-id="baa99-116">Hem `InStateCustomers` alt `OutOfStateCustomers` öğeler hem de alt`customerType`öğeler karmaşık tür elemanlarıdır ( ).</span><span class="sxs-lookup"><span data-stu-id="baa99-116">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="baa99-117">Bu nedenle, eşleme işlemi aşağıdaki iki `DataSet`özdeş tablolar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="baa99-117">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="baa99-118">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="baa99-118">In This Section</span></span>  
 [<span data-ttu-id="baa99-119">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="baa99-119">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="baa99-120">Bir 'de benzersiz ve yabancı anahtar kısıtlamaları oluşturmak için `DataSet`kullanılan XML Şema öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="baa99-120">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="baa99-121">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="baa99-121">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="baa99-122">Tablo sütunları arasında ilişki oluşturmak için kullanılan XML `DataSet`Şema öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="baa99-122">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="baa99-123">XML Şema Kısıtlamaları ve İlişkileri</span><span class="sxs-lookup"><span data-stu-id="baa99-123">XML Schema Constraints and Relationships</span></span>](xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="baa99-124">Bir 'de kısıtlamalar oluşturmak için XML Şema öğelerini kullanırken ilişkilerin nasıl örtülü olarak oluşturulduğunu `DataSet`açıklar.</span><span class="sxs-lookup"><span data-stu-id="baa99-124">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="baa99-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="baa99-125">Related Sections</span></span>  
 [<span data-ttu-id="baa99-126">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="baa99-126">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="baa99-127">XML `DataSet` verisi olarak ilişkisel yapının ve verilerin nasıl yüklenir ve devam edin.</span><span class="sxs-lookup"><span data-stu-id="baa99-127">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baa99-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="baa99-128">See also</span></span>

- [<span data-ttu-id="baa99-129">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="baa99-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
