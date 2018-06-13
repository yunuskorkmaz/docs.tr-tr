---
title: Nesne karşılaştırma kullanarak XmlNameTable
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09f717cb4c09c1e35b9472b7b549f1d3edf0dd15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569284"
---
# <a name="object-comparison-using-xmlnametable"></a><span data-ttu-id="a2c94-102">Nesne karşılaştırma kullanarak XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="a2c94-102">Object Comparison Using XmlNameTable</span></span>
<span data-ttu-id="a2c94-103">**XML belgelerine uymasıdır**, oluşturduğunuzda, bu belge için özel olarak oluşturulan bir ad tablo sahip.</span><span class="sxs-lookup"><span data-stu-id="a2c94-103">**XmlDocuments**, when created, have a name table created specifically for that document.</span></span> <span data-ttu-id="a2c94-104">XML belgeye yüklenen ya da yeni öğe veya öznitelik oluşturulur özniteliği ve öğesi adları içine konur **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="a2c94-104">When XML is loaded into the document, or new elements or attributes are created, the attribute and element names are put into the **XmlNameTable**.</span></span> <span data-ttu-id="a2c94-105">Ayrıca bir **XmlDocument** varolan kullanarak **ad tablosu** başka bir belgeden.</span><span class="sxs-lookup"><span data-stu-id="a2c94-105">You can also create an **XmlDocument** using an existing **NameTable** from another document.</span></span> <span data-ttu-id="a2c94-106">Zaman **XML belgelerine uymasıdır** alan Oluşturucu ile oluşturulmuş bir **XmlNameTable** parametresi, belge sahip düğüm adları, ad alanlarını ve önekleri zaten depolanmış erişim  **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="a2c94-106">When **XmlDocuments** are created with the constructor that takes an **XmlNameTable** parameter, the document has access to the node names, namespaces, and prefixes already stored in the **XmlNameTable**.</span></span> <span data-ttu-id="a2c94-107">Adları tabloda depolandıktan sonra ne olursa olsun ad tablosunu nasıl yüklenir, adlara sahip adları nesne karşılaştırma dize karşılaştırma yerine hızlı bir şekilde kullanarak karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a2c94-107">Regardless of how the name table is loaded with names, once the names are stored in the table, names can be compared quickly using object comparison instead of string comparison.</span></span> <span data-ttu-id="a2c94-108">Dizeleri de eklenebilir adını kullanarak tablo <xref:System.Xml.NameTable.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2c94-108">Strings can also be added to the name table using the <xref:System.Xml.NameTable.Add%2A>.</span></span> <span data-ttu-id="a2c94-109">Aşağıdaki kod örneği oluşturulan bir ad tablosunu ve dize gösterir **MyString** tabloya eklenen.</span><span class="sxs-lookup"><span data-stu-id="a2c94-109">The following code sample shows a name table being created and the string **MyString** being added to the table.</span></span> <span data-ttu-id="a2c94-110">Bundan sonra bir **XmlDocument** bu tabloyu ve öğe ve öznitelik adları kullanılarak oluşturulan **Myfile.xml** var olan ad tabloya eklenir.</span><span class="sxs-lookup"><span data-stu-id="a2c94-110">After that, an **XmlDocument** is created using that table, and the element and attribute names in **Myfile.xml** are added to the existing name table.</span></span>  
  
```vb  
Dim nt As New NameTable()  
nt.Add("MyString")  
Dim doc As New XmlDocument(nt)  
doc.Load("Myfile.xml")  
```  
  
```csharp  
NameTable nt = new NameTable();  
nt.Add("MyString");  
XmlDocument doc = new XmlDocument(nt);  
doc.Load("Myfile.xml");  
```  
  
 <span data-ttu-id="a2c94-111">Aşağıdaki kod örneği bir belge oluşturulmasını Ayrıca belge adı tablosu ve nesne karşılaştırma adları ekler belgeye eklenmekte olan iki yeni öğeler gösterilir.</span><span class="sxs-lookup"><span data-stu-id="a2c94-111">The following code example shows the creation of a document, two new elements being added to the document, which also adds them to the document name table, and the object comparison on the names.</span></span>  
  
```vb  
Dim doc1 As XmlDocument = imp.CreateDocument()  
Dim node1 As XmlElement = doc.CreateElement("node1")  
Dim doc2 As XmlDocument = imp.CreateDocument()  
Dim node2 As XmlElement = doc.CreateElement("node2")  
if (CType(node1.Name, object) = CType(node2.Name, object))  
```  
  
```csharp  
XmlDocument doc1 = imp.CreateDocument();  
node1 = doc1.CreateElement ("node1");  
XmlDocument doc2 = imp.CreateDocument();  
node2 = doc2.CreateElement ("node1");  
if (((object)node1.Name) == ((object)node2.Name))  
{ ...  
```  
  
 <span data-ttu-id="a2c94-112">Belge aynı türde sürekli olarak, bir XML Şeması Tanım Dili (XSD) şema veya belge türü için uygun bir e-ticaret sitesinde sipariş belgeler gibi işlenirken Yukarıdaki iki belgeler arasında geçirilen ad tablonun tipik bir senaryodur tanımı (DTD) ve aynı dizeleri yinelenir.</span><span class="sxs-lookup"><span data-stu-id="a2c94-112">The above scenario of a name table passed between two documents is typical when the same type of document is being processed repeatedly, such as order documents at an ecommerce site, which conform to an XML Schema definition language (XSD) schema or document type definition (DTD) and the same strings are repeated.</span></span> <span data-ttu-id="a2c94-113">Birden çok belgelerde aynı öğe adı gerçekleştiği sırada aynı adı tablosunu kullanarak performans geliştirmesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2c94-113">Using the same name table gives a performance improvement, as the same element name occurs in multiple documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2c94-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2c94-114">See Also</span></span>  
 [<span data-ttu-id="a2c94-115">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="a2c94-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
