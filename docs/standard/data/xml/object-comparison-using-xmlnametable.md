---
title: "Nesne karşılaştırma kullanarak XmlNameTable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f6c65581437bfb22cf771d66716b3dbb62dbafae
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="object-comparison-using-xmlnametable"></a>Nesne karşılaştırma kullanarak XmlNameTable
**XML belgelerine uymasıdır**, oluşturduğunuzda, bu belge için özel olarak oluşturulan bir ad tablo sahip. XML belgeye yüklenen ya da yeni öğe veya öznitelik oluşturulur özniteliği ve öğesi adları içine konur **XmlNameTable**. Ayrıca bir **XmlDocument** varolan kullanarak **ad tablosu** başka bir belgeden. Zaman **XML belgelerine uymasıdır** alan Oluşturucu ile oluşturulmuş bir **XmlNameTable** parametresi, belge sahip düğüm adları, ad alanlarını ve önekleri zaten depolanmış erişim  **XmlNameTable**. Adları tabloda depolandıktan sonra ne olursa olsun ad tablosunu nasıl yüklenir, adlara sahip adları nesne karşılaştırma dize karşılaştırma yerine hızlı bir şekilde kullanarak karşılaştırılabilir. Dizeleri de eklenebilir adını kullanarak tablo <xref:System.Xml.NameTable.Add%2A>. Aşağıdaki kod örneği oluşturulan bir ad tablosunu ve dize gösterir **MyString** tabloya eklenen. Bundan sonra bir **XmlDocument** bu tabloyu ve öğe ve öznitelik adları kullanılarak oluşturulan **Myfile.xml** var olan ad tabloya eklenir.  
  
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
  
 Aşağıdaki kod örneği bir belge oluşturulmasını Ayrıca belge adı tablosu ve nesne karşılaştırma adları ekler belgeye eklenmekte olan iki yeni öğeler gösterilir.  
  
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
  
 Belge aynı türde sürekli olarak, bir XML Şeması Tanım Dili (XSD) şema veya belge türü için uygun bir e-ticaret sitesinde sipariş belgeler gibi işlenirken Yukarıdaki iki belgeler arasında geçirilen ad tablonun tipik bir senaryodur tanımı (DTD) ve aynı dizeleri yinelenir. Birden çok belgelerde aynı öğe adı gerçekleştiği sırada aynı adı tablosunu kullanarak performans geliştirmesi sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
