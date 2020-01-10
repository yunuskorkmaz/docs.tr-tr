---
title: XML Belgesi Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
ms.openlocfilehash: a12555a02b45a964ff7efcbe00e0d2cb8637474a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709991"
---
# <a name="xml-document-creation"></a>XML Belgesi Oluşturma
XML belgesi oluşturmanın iki yolu vardır. Bir yol, parametresiz bir **XmlDocument** oluşturmaktır. Diğer bir deyişle, bir **XmlDocument** oluşturmak ve bunu bir XmlNameTable parametresi olarak iletmektir. Aşağıdaki örnek, parametresiz yeni, boş bir **XmlDocument** oluşturmayı gösterir.  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 Bir belge oluşturulduktan sonra, **Load** metodunu kullanarak bir dize, AKıŞ, URL, metin okuyucusu veya bir **XmlReader** türetilmiş sınıftan verilerle yükleyebilirsiniz. Ayrıca, bir dizeden XML okuyan bir Load yöntemi olan **LoadXml** yöntemi de vardır. Çeşitli **yükleme** yöntemleri hakkında daha fazla bilgi için bkz. [Dom 'Da XML belgesi okuma](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).  
  
 **XmlNameTable**adlı bir sınıf vardır. Bu sınıf, atomlanmış dize nesnelerinin bir tablosudur. Bu tablo, XML ayrıştırıcısının bir XML belgesindeki tüm yinelenen öğe ve öznitelik adları için aynı dize nesnesini kullanması için etkili bir yol sağlar. Bir belge, yukarıda gösterildiği gibi oluşturulduğunda ve belge yüklendiğinde öznitelik ve öğe adlarıyla yüklendiğinde, otomatik olarak bir **XmlNameTable** oluşturulur. Zaten bir ad tablosu olan bir belgeniz varsa ve bu adlar başka bir belgede yararlı olacaksa, parametre olarak **XmlNameTable** alan **Load** metodunu kullanarak yeni bir belge oluşturabilirsiniz. Belge bu yöntemle oluşturulduğunda, var olan **XmlNameTable** , diğer belgeden daha önce yüklenmiş olan tüm öznitelikleri ve öğeleri kullanır. Öğe ve öznitelik adlarını verimli bir şekilde karşılaştırmak için kullanılabilir. **XmlNameTable**hakkında daha fazla bilgi için bkz. [XmlNameTable kullanılarak nesne karşılaştırması](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md). Başvuru için bkz. <xref:System.Xml.XmlNameTable>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
