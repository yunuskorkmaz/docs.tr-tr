---
description: 'Hakkında daha fazla bilgi edinin: XmlNameTable kullanarak nesne karşılaştırması'
title: XmlNameTable Kullanarak Nesne Karşılaştırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
ms.openlocfilehash: 7be93741b9eeb353e4e3a2135f975f9031557d6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783319"
---
# <a name="object-comparison-using-xmlnametable"></a><span data-ttu-id="39f01-103">XmlNameTable Kullanarak Nesne Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="39f01-103">Object Comparison Using XmlNameTable</span></span>

<span data-ttu-id="39f01-104">Oluşturulan **XMLDocuments**, bu belge için özel olarak oluşturulan bir ad tablosuna sahiptir.</span><span class="sxs-lookup"><span data-stu-id="39f01-104">**XmlDocuments**, when created, have a name table created specifically for that document.</span></span> <span data-ttu-id="39f01-105">XML belgeye yüklendiğinde veya yeni öğeler ya da öznitelikler oluşturulduğunda, öznitelik ve öğe adları **XmlNameTable** içine konur.</span><span class="sxs-lookup"><span data-stu-id="39f01-105">When XML is loaded into the document, or new elements or attributes are created, the attribute and element names are put into the **XmlNameTable**.</span></span> <span data-ttu-id="39f01-106">Ayrıca, başka bir belgedeki mevcut bir **NameTable** kullanarak bir **XmlDocument** oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39f01-106">You can also create an **XmlDocument** using an existing **NameTable** from another document.</span></span> <span data-ttu-id="39f01-107">**XMLDocuments** bir **XmlNameTable** parametresi alan Oluşturucu ile oluşturulduğunda, belge, **XmlNameTable** içinde depolanmış olan düğüm adlarına, ad alanlarına ve öneklere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="39f01-107">When **XmlDocuments** are created with the constructor that takes an **XmlNameTable** parameter, the document has access to the node names, namespaces, and prefixes already stored in the **XmlNameTable**.</span></span> <span data-ttu-id="39f01-108">Ad tablosunun adlarla nasıl yüklenediğine bakılmaksızın, adlar tabloda depolandıktan sonra, adlar dize karşılaştırması yerine nesne karşılaştırması kullanılarak hızlı bir şekilde karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="39f01-108">Regardless of how the name table is loaded with names, once the names are stored in the table, names can be compared quickly using object comparison instead of string comparison.</span></span> <span data-ttu-id="39f01-109">Dizeler, kullanılarak ad tablosuna da eklenebilir <xref:System.Xml.NameTable.Add%2A> .</span><span class="sxs-lookup"><span data-stu-id="39f01-109">Strings can also be added to the name table using the <xref:System.Xml.NameTable.Add%2A>.</span></span> <span data-ttu-id="39f01-110">Aşağıdaki kod örneği, oluşturulmakta olan bir ad tablosunu ve tabloya eklenen **MyString** dizesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="39f01-110">The following code sample shows a name table being created and the string **MyString** being added to the table.</span></span> <span data-ttu-id="39f01-111">Bundan sonra, bu tablo kullanılarak bir **XmlDocument** oluşturulur ve **Myfile.xml** öğe ve öznitelik adları var olan ad tablosuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="39f01-111">After that, an **XmlDocument** is created using that table, and the element and attribute names in **Myfile.xml** are added to the existing name table.</span></span>  
  
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
  
 <span data-ttu-id="39f01-112">Aşağıdaki kod örneğinde belge oluşturma, belgeye eklenen iki yeni öğe, ayrıca bunları belge adı tablosuna ve adlara göre nesne karşılaştırması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="39f01-112">The following code example shows the creation of a document, two new elements being added to the document, which also adds them to the document name table, and the object comparison on the names.</span></span>  
  
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
  
 <span data-ttu-id="39f01-113">İki belge arasında geçirilen bir ad tablosunun yukarıdaki senaryosu, bir XML şeması tanım dili (xsd) şeması veya belge türü tanımı (DTD) ile uyumlu olan ve aynı dizeler tekrarlandığı bir e-ticaret sitesinde sipariş belgeleri gibi, aynı belge türü her zaman sürekli işlendiğinde tipik bir addır.</span><span class="sxs-lookup"><span data-stu-id="39f01-113">The above scenario of a name table passed between two documents is typical when the same type of document is being processed repeatedly, such as order documents at an ecommerce site, which conform to an XML Schema definition language (XSD) schema or document type definition (DTD) and the same strings are repeated.</span></span> <span data-ttu-id="39f01-114">Aynı ad tablosunun kullanılması, birden çok belgede aynı öğe adı gerçekleştiği için bir performans geliştirmesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="39f01-114">Using the same name table gives a performance improvement, as the same element name occurs in multiple documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39f01-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39f01-115">See also</span></span>

- [<span data-ttu-id="39f01-116">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="39f01-116">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
