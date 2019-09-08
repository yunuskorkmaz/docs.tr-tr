---
title: XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: d15aa02b41b9a34b00298aeb32d2e3998de8feba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786337"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="e0132-102">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="e0132-102">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>
<span data-ttu-id="e0132-103">Bu bölüm bir XML şeması tanım dili (xsd) şema belgesinden `DataSet` bir öğesinin ilişkisel şemasının nasıl oluşturulduğunu gösteren bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0132-103">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="e0132-104">Genel olarak, bir şema `complexType` öğesinin her alt öğesi için `DataSet`içinde bir tablo oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e0132-104">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="e0132-105">Tablo yapısı, karmaşık türün tanımına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e0132-105">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="e0132-106">Tablolar, `DataSet` şemadaki en üst düzey öğelerde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e0132-106">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="e0132-107">Ancak, bir `complexType` tablo, `complexType` öğe başka `complexType` bir öğenin içinde iç içe olduğunda yalnızca üst düzey öğe için oluşturulur, bu durumda `DataSet`iç içe `complexType` öğe içinde bir `DataTable` ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="e0132-107">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="e0132-108">XSD hakkında daha fazla bilgi için bkz. World Wide Web Konsorsiyumu (W3C) [XML Şeması bölümü 0: Öncü öneri](https://www.w3.org/TR/xmlschema-0/) [, XML şeması Bölüm 1: Yapılar önerisi](https://www.w3.org/TR/xmlschema-1/) [ve XML şeması Bölüm 2: Veri türleri](https://www.w3.org/TR/xmlschema-2/)önerisi.</span><span class="sxs-lookup"><span data-stu-id="e0132-108">For more information about the XSD, see the World Wide Web Consortium (W3C) [XML Schema Part 0: Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), the [XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/), and the [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>  
  
 <span data-ttu-id="e0132-109">Aşağıdaki örnek, bir **veri kümesi** öğesi olan `customers` `MyDataSet` öğesinin alt öğesi olan bir XML şemasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0132-109">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
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
  
 <span data-ttu-id="e0132-110">Önceki örnekte, öğesi `customers` karmaşık bir tür öğesidir.</span><span class="sxs-lookup"><span data-stu-id="e0132-110">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="e0132-111">Bu nedenle, karmaşık tür tanımı ayrıştırılır ve eşleme işlemi aşağıdaki tabloyu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0132-111">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 <span data-ttu-id="e0132-112">Tablodaki her sütunun veri türü, karşılık gelen öğenin veya özniteliğin XML şema türünden türetilir.</span><span class="sxs-lookup"><span data-stu-id="e0132-112">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0132-113">Öğesi `customers` **tamsayı**gibi basit bir XML şeması veri türünde ise hiçbir tablo oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="e0132-113">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="e0132-114">Tablolar yalnızca karmaşık türler olan en üst düzey öğeler için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e0132-114">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="e0132-115">Aşağıdaki XML şemasında, **şema** öğesi iki öğe alt `InStateCustomers` öğesine sahiptir ve. `OutOfStateCustomers`</span><span class="sxs-lookup"><span data-stu-id="e0132-115">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
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
  
 <span data-ttu-id="e0132-116">`InStateCustomers` Hem`customerType`hem de altöğelerikarmaşıktür`OutOfStateCustomers` öğeleridir ().</span><span class="sxs-lookup"><span data-stu-id="e0132-116">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="e0132-117">Bu nedenle, eşleme işlemi içinde `DataSet`aşağıdaki iki özdeş tabloyu üretir.</span><span class="sxs-lookup"><span data-stu-id="e0132-117">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="e0132-118">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e0132-118">In This Section</span></span>  
 [<span data-ttu-id="e0132-119">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="e0132-119">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="e0132-120">Bir `DataSet`içinde benzersiz ve yabancı anahtar kısıtlamaları oluşturmak Için kullanılan xml şema öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e0132-120">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="e0132-121">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0132-121">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="e0132-122">İçindeki tablo sütunları arasında ilişki oluşturmak için kullanılan XML şema öğelerini açıklar `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="e0132-122">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="e0132-123">XML Şema Kısıtlamaları ve İlişkileri</span><span class="sxs-lookup"><span data-stu-id="e0132-123">XML Schema Constraints and Relationships</span></span>](xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="e0132-124">Bir `DataSet`içinde kısıtlamalar oluşturmak için XML şema öğeleri kullanıldığında ilişkilerin örtük olarak nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="e0132-124">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e0132-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e0132-125">Related Sections</span></span>  
 [<span data-ttu-id="e0132-126">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="e0132-126">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="e0132-127">Bir `DataSet` as XML verilerinde ilişkisel yapının ve verilerin nasıl yükleneceğini ve kalıcı yapılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e0132-127">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0132-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0132-128">See also</span></span>

- [<span data-ttu-id="e0132-129">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e0132-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
