---
description: 'Hakkında daha fazla bilgi edinin: XML şemasından (XSD) veri kümesi Ilişkisel yapısı türetme'
title: XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: c2d2dc8ab9c8a1cf77c79fbde38a06de6f120c82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652529"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="b3fe0-103">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="b3fe0-103">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>

<span data-ttu-id="b3fe0-104">Bu bölüm bir `DataSet` XML şeması tanım dili (xsd) şema belgesinden bir öğesinin ilişkisel şemasının nasıl oluşturulduğunu gösteren bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3fe0-104">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="b3fe0-105">Genel olarak, `complexType` bir şema öğesinin her alt öğesi için içinde bir tablo oluşturulur `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="b3fe0-105">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="b3fe0-106">Tablo yapısı, karmaşık türün tanımına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b3fe0-106">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="b3fe0-107">Tablolar, `DataSet` şemadaki en üst düzey öğelerde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b3fe0-107">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="b3fe0-108">Ancak, bir tablo, `complexType` öğe başka bir öğenin içinde iç içe olduğunda yalnızca üst düzey öğe için oluşturulur `complexType` `complexType` , bu durumda iç içe `complexType` öğe içinde bir ile eşlenir `DataTable` `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="b3fe0-108">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="b3fe0-109">XSD hakkında daha fazla bilgi için, bkz. World Wide Web Konsorsiyumu (W3C) [XML Şeması bölümü 0: öncü öneri](https://www.w3.org/TR/xmlschema-0/), [XML şeması Bölüm 1: yapılar önerisi](https://www.w3.org/TR/xmlschema-1/)ve [XML şeması Bölüm 2: veri türleri önerisi](https://www.w3.org/TR/xmlschema-2/).</span><span class="sxs-lookup"><span data-stu-id="b3fe0-109">For more information about the XSD, see the World Wide Web Consortium (W3C) [XML Schema Part 0: Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), the [XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/), and the [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>  
  
 <span data-ttu-id="b3fe0-110">Aşağıdaki örnek, `customers` `MyDataSet` bir **veri kümesi** öğesi olan öğesinin alt öğesi olan bir XML şemasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3fe0-110">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
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
  
 <span data-ttu-id="b3fe0-111">Önceki örnekte, öğesi `customers` karmaşık bir tür öğesidir.</span><span class="sxs-lookup"><span data-stu-id="b3fe0-111">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="b3fe0-112">Bu nedenle, karmaşık tür tanımı ayrıştırılır ve eşleme işlemi aşağıdaki tabloyu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b3fe0-112">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="b3fe0-113">Tablodaki her sütunun veri türü, karşılık gelen öğenin veya özniteliğin XML şema türünden türetilir.</span><span class="sxs-lookup"><span data-stu-id="b3fe0-113">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3fe0-114">Öğesi tamsayı gibi `customers` Basit BIR XML şeması veri türünde ise hiçbir tablo oluşturulmaz .</span><span class="sxs-lookup"><span data-stu-id="b3fe0-114">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="b3fe0-115">Tablolar yalnızca karmaşık türler olan en üst düzey öğeler için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b3fe0-115">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="b3fe0-116">Aşağıdaki XML şemasında, **şema** öğesi iki öğe alt öğesine sahiptir `InStateCustomers` ve `OutOfStateCustomers` .</span><span class="sxs-lookup"><span data-stu-id="b3fe0-116">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
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
  
 <span data-ttu-id="b3fe0-117">Hem `InStateCustomers` hem de `OutOfStateCustomers` alt öğeleri karmaşık tür öğeleridir ( `customerType` ).</span><span class="sxs-lookup"><span data-stu-id="b3fe0-117">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="b3fe0-118">Bu nedenle, eşleme işlemi içinde aşağıdaki iki özdeş tabloyu üretir `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="b3fe0-118">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="b3fe0-119">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b3fe0-119">In This Section</span></span>  

 [<span data-ttu-id="b3fe0-120">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="b3fe0-120">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="b3fe0-121">Bir içinde benzersiz ve yabancı anahtar kısıtlamaları oluşturmak için kullanılan XML şema öğelerini açıklar `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="b3fe0-121">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="b3fe0-122">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b3fe0-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="b3fe0-123">İçindeki tablo sütunları arasında ilişki oluşturmak için kullanılan XML şema öğelerini açıklar `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="b3fe0-123">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="b3fe0-124">XML Şema Kısıtlamaları ve İlişkileri</span><span class="sxs-lookup"><span data-stu-id="b3fe0-124">XML Schema Constraints and Relationships</span></span>](xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="b3fe0-125">Bir içinde kısıtlamalar oluşturmak için XML şema öğeleri kullanıldığında ilişkilerin örtük olarak nasıl oluşturulduğunu açıklar `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="b3fe0-125">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b3fe0-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b3fe0-126">Related Sections</span></span>  

 [<span data-ttu-id="b3fe0-127">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="b3fe0-127">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="b3fe0-128">Bir as XML verilerinde ilişkisel yapının ve verilerin nasıl yükleneceğini ve kalıcı yapılacağını açıklar `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="b3fe0-128">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3fe0-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3fe0-129">See also</span></span>

- [<span data-ttu-id="b3fe0-130">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b3fe0-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
