---
title: XmlNameTable Kullanarak Nesne Karşılaştırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 814f5434dd0473b3b1dd613a2eba14a828c464d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936714"
---
# <a name="object-comparison-using-xmlnametable"></a><span data-ttu-id="aec72-102">XmlNameTable Kullanarak Nesne Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="aec72-102">Object Comparison Using XmlNameTable</span></span>
<span data-ttu-id="aec72-103">**XML belgelerine uymasıdır**, oluşturulduktan sonra bu belge için özel olarak oluşturulan bir ad tablosu sahip.</span><span class="sxs-lookup"><span data-stu-id="aec72-103">**XmlDocuments**, when created, have a name table created specifically for that document.</span></span> <span data-ttu-id="aec72-104">XML belgeye yüklendi veya yeni öğeler veya öznitelikleri oluşturulur, öğeyi ve öznitelik adları içine yerleştirilir **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="aec72-104">When XML is loaded into the document, or new elements or attributes are created, the attribute and element names are put into the **XmlNameTable**.</span></span> <span data-ttu-id="aec72-105">Ayrıca oluşturabileceğiniz bir **XmlDocument** var olan bir **ad tablosu** başka bir belgeden.</span><span class="sxs-lookup"><span data-stu-id="aec72-105">You can also create an **XmlDocument** using an existing **NameTable** from another document.</span></span> <span data-ttu-id="aec72-106">Zaman **XML belgelerine uymasıdır** alan Oluşturucu ile oluşturulan bir **XmlNameTable** parametresi, belge sahip düğüm adları, ad alanlarını ve önekleri zaten depolanmış erişim  **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="aec72-106">When **XmlDocuments** are created with the constructor that takes an **XmlNameTable** parameter, the document has access to the node names, namespaces, and prefixes already stored in the **XmlNameTable**.</span></span> <span data-ttu-id="aec72-107">Adları tabloda depolandıktan sonra ad tablosu nasıl yüklenir bakılmaksızın adları ile adlarının nesne karşılaştırma yerine dize karşılaştırma kullanarak hızlı bir şekilde karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="aec72-107">Regardless of how the name table is loaded with names, once the names are stored in the table, names can be compared quickly using object comparison instead of string comparison.</span></span> <span data-ttu-id="aec72-108">Dizeleri eklenebilir adı kullanarak tablo <xref:System.Xml.NameTable.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="aec72-108">Strings can also be added to the name table using the <xref:System.Xml.NameTable.Add%2A>.</span></span> <span data-ttu-id="aec72-109">Aşağıdaki kod örneği oluşturulan bir ad tablosu ve dize gösterir **MyString** tabloya eklenmekte.</span><span class="sxs-lookup"><span data-stu-id="aec72-109">The following code sample shows a name table being created and the string **MyString** being added to the table.</span></span> <span data-ttu-id="aec72-110">Bundan sonra bir **XmlDocument** bu tabloyu ve içindeki öğe ve öznitelik adları kullanılarak oluşturulan **Myfile.xml** var olan ad tablosuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="aec72-110">After that, an **XmlDocument** is created using that table, and the element and attribute names in **Myfile.xml** are added to the existing name table.</span></span>  
  
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
  
 <span data-ttu-id="aec72-111">Aşağıdaki kod örneği, iki yeni öğe Ayrıca belge ad tablosu ve adları nesne karşılaştırma ekler belgeye eklenen bir belge oluşturulmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aec72-111">The following code example shows the creation of a document, two new elements being added to the document, which also adds them to the document name table, and the object comparison on the names.</span></span>  
  
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
  
 <span data-ttu-id="aec72-112">Belge aynı türde tekrar tekrar gibi bir XML Şeması Tanım Dili (XSD) şeması veya belge türü için uygun sipariş belgeleriyle bir e-ticaret sitesinde işlenirken iki belgeler arasında geçirilen bir ad tablosu, yukarıdaki senaryo tipik tanımı (DTD'nin) ve aynı dizeler yinelenir.</span><span class="sxs-lookup"><span data-stu-id="aec72-112">The above scenario of a name table passed between two documents is typical when the same type of document is being processed repeatedly, such as order documents at an ecommerce site, which conform to an XML Schema definition language (XSD) schema or document type definition (DTD) and the same strings are repeated.</span></span> <span data-ttu-id="aec72-113">Aynı öğe adı içinde birden çok belge oluştuğu sırada aynı ad tablosu kullanarak bir performans geliştirmesi sunar.</span><span class="sxs-lookup"><span data-stu-id="aec72-113">Using the same name table gives a performance improvement, as the same element name occurs in multiple documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aec72-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aec72-114">See also</span></span>

- [<span data-ttu-id="aec72-115">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="aec72-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
