---
title: XML Belgesi Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b76140fb7d79b1e191c0451cd7556963130d224a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959061"
---
# <a name="xml-document-creation"></a>XML Belgesi Oluşturma
Bir XML belgesi oluşturmak için iki yolu vardır. Oluşturmak için bir yolu olan bir **XmlDocument** parametre olmadan. Oluşturmak için diğer yol ise bir **XmlDocument** ve parametre olarak bir XmlNameTable geçirin. Aşağıdaki örnek, yeni, boş oluşturma işlemi gösterilmektedir **XmlDocument** hiçbir parametreleri kullanarak.  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 Bir belge oluşturulduktan sonra bu verileri bir dizeden ile yükleyebilirsiniz akış URL'si, metin okuyucuyu ya da bir **XmlReader** sınıfını kullanarak türetilmiş **yük** yöntemi. Ayrıca başka bir yükleme yöntemi vardır **LoadXML** yöntemi XML bir dizeden okur. Çeşitli hakkında daha fazla bilgi için **yük** yöntemleri bkz [DOM'da XML belgesi okuma](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).  
  
 Adlı bir sınıf yok **XmlNameTable**. Bu sınıf, parçalara ayrılmış bir dize nesnesi bir tablodur. Bu tabloda tüm yinelenen öğe ve öznitelik adları bir XML belgesi için aynı dize nesnesi kullanılacak XML Ayrıştırıcı için etkili bir yol sağlar. Bir **XmlNameTable** belge yukarıda da gösterildiği gibi oluşturulduğunda ve öğeyi ve öznitelik adları ile yüklenen belge yüklendiğinde otomatik olarak oluşturulur. Ad tablosu sahip bir belge zaten varsa ve bu başka bir belgede yararlı olacak adlardır, kullanarak yeni bir belge oluşturabilirsiniz **yük** gereken yöntemini bir **XmlNameTable** bir parametre olarak. Belgenin bu yöntemle oluşturulduğunda, varolan kullanır **XmlNameTable** tüm öznitelikleri ve öğeleri içine diğer belgeden zaten yüklü. Öğe ve öznitelik adları verimli bir şekilde karşılaştırmak için kullanılabilir. Daha fazla bilgi için **XmlNameTable**, bkz: [XmlNameTable kullanarak nesne karşılaştırma](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md). Başvuru için bkz: <xref:System.Xml.XmlNameTable>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
