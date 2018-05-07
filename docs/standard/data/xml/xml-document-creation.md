---
title: XML belgesi oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ab7632966cd2a0087a8bdc1d452d02543edbec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="xml-document-creation"></a>XML belgesi oluşturma
Bir XML belgesi oluşturmanın iki yolu vardır. Tek yönlü oluşturmaktır bir **XmlDocument** hiçbir parametre. Diğer bir yol oluşturmaktır bir **XmlDocument** ve bir XmlNameTable parametre olarak geçirin. Aşağıdaki örnek yeni bir boş oluşturulacağını gösterir **XmlDocument** hiçbir parametrelerini kullanarak.  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 Bir belge oluşturulduktan sonra onu bir dize verilerle yükleyebilirsiniz akış, URL, metin okuyucu veya bir **XmlReader** sınıfını kullanarak türetilmiş **yük** yöntemi. Ayrıca başka bir yükleme yöntemini olan **LoadXML** bir dizeden XML okur yöntemi. Çeşitli hakkında daha fazla bilgi için **yük** yöntemleri bkz [bir XML belgesi DOM okuma](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).  
  
 Adlı bir sınıf yok **XmlNameTable**. Bu sınıf, atomized dize nesnelerin bir tablodur. Bu tabloda tüm yinelenen öğe ve öznitelik adları bir XML belgesi aynı dize nesnesi kullanılmak üzere XML Ayrıştırıcı için verimli bir yol sağlar. Bir **XmlNameTable** bir belge yukarıda gösterildiği gibi oluşturulduğunda ve belge yüklendiğinde özniteliği ve öğesi adlarıyla yüklendi otomatik olarak oluşturulur. Bir belge adı tablosu ile zaten varsa ve bu adlardan başka bir belgede yararlı olacaktır, kullanarak yeni bir belge oluşturabilirsiniz **yük** yönteminin alan bir **XmlNameTable** bir parametre olarak. Belgenin bu yöntemle oluşturulduğunda, varolan kullanan **XmlNameTable** ile tüm öznitelikler ve öğeler içine diğer belgesinden zaten yüklü. Verimli bir şekilde öğe ve öznitelik adları karşılaştırmak için kullanılabilir. Daha fazla bilgi için **XmlNameTable**, bkz: [nesne karşılaştırma kullanarak XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md). Başvuru için bkz: <xref:System.Xml.XmlNameTable>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
