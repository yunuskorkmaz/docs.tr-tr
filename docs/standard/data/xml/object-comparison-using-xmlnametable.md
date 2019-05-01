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
# <a name="object-comparison-using-xmlnametable"></a>XmlNameTable Kullanarak Nesne Karşılaştırma
**XML belgelerine uymasıdır**, oluşturulduktan sonra bu belge için özel olarak oluşturulan bir ad tablosu sahip. XML belgeye yüklendi veya yeni öğeler veya öznitelikleri oluşturulur, öğeyi ve öznitelik adları içine yerleştirilir **XmlNameTable**. Ayrıca oluşturabileceğiniz bir **XmlDocument** var olan bir **ad tablosu** başka bir belgeden. Zaman **XML belgelerine uymasıdır** alan Oluşturucu ile oluşturulan bir **XmlNameTable** parametresi, belge sahip düğüm adları, ad alanlarını ve önekleri zaten depolanmış erişim  **XmlNameTable**. Adları tabloda depolandıktan sonra ad tablosu nasıl yüklenir bakılmaksızın adları ile adlarının nesne karşılaştırma yerine dize karşılaştırma kullanarak hızlı bir şekilde karşılaştırılabilir. Dizeleri eklenebilir adı kullanarak tablo <xref:System.Xml.NameTable.Add%2A>. Aşağıdaki kod örneği oluşturulan bir ad tablosu ve dize gösterir **MyString** tabloya eklenmekte. Bundan sonra bir **XmlDocument** bu tabloyu ve içindeki öğe ve öznitelik adları kullanılarak oluşturulan **Myfile.xml** var olan ad tablosuna eklenir.  
  
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
  
 Aşağıdaki kod örneği, iki yeni öğe Ayrıca belge ad tablosu ve adları nesne karşılaştırma ekler belgeye eklenen bir belge oluşturulmasını gösterir.  
  
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
  
 Belge aynı türde tekrar tekrar gibi bir XML Şeması Tanım Dili (XSD) şeması veya belge türü için uygun sipariş belgeleriyle bir e-ticaret sitesinde işlenirken iki belgeler arasında geçirilen bir ad tablosu, yukarıdaki senaryo tipik tanımı (DTD'nin) ve aynı dizeler yinelenir. Aynı öğe adı içinde birden çok belge oluştuğu sırada aynı ad tablosu kullanarak bir performans geliştirmesi sunar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
