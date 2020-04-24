---
title: DOM’da Bir Öğe Düğümünden Öznitelikleri Kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
ms.openlocfilehash: bb18e712d5ed2cd06c7ae0e867b19ca8a9ad2513
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710355"
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a>DOM’da Bir Öğe Düğümünden Öznitelikleri Kaldırma
Öznitelikleri kaldırmanın birçok yolu vardır. Bir teknik, öznitelik koleksiyonundan kaldırmektir. Bunu yapmak için aşağıdaki adımlar gerçekleştirilir:  
  
1. Öğesini kullanarak `XmlAttributeCollection attrs = elem.Attributes;`öğesinden öznitelik koleksiyonunu alın.  
  
2. Öznitelik koleksiyonundan özniteliği, üç yöntemden birini kullanarak kaldırın:  
  
    - Belirli <xref:System.Xml.XmlAttributeCollection.Remove%2A> bir özniteliği kaldırmak için kullanın.  
  
    - Koleksiyondan <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> tüm öznitelikleri kaldırmak ve öğeyi hiçbir öznitelik olmadan bırakmak için kullanın.  
  
    - Öznitelik <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> koleksiyonundan özniteliği Dizin numarasını kullanarak kaldırmak için kullanın.  
  
 Aşağıdaki yöntemler öğe düğümünden öznitelikleri kaldırır.  
  
- Öznitelik <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> koleksiyonunu kaldırmak için kullanın.  
  
- Koleksiyondan <xref:System.Xml.XmlElement.RemoveAttribute%2A> ada göre tek bir özniteliği kaldırmak için kullanın.  
  
- Koleksiyondan <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> dizin numarasına göre tek bir özniteliği kaldırmak için kullanın.  
  
 Diğer bir seçenek de öğeyi almak, öznitelik koleksiyonundan özniteliği almak ve öznitelik düğümünü doğrudan kaldırkullanmaktır. Öznitelik koleksiyonundan özniteliği almak için bir ad, `XmlAttribute attr = attrs["attr_name"];`, Dizin `XmlAttribute attr = attrs[0];`veya ad alanıyla `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`tam olarak niteleyerek adı kullanabilirsiniz.  
  
 Öznitelikleri kaldırmak için kullanılan yöntemden bağımsız olarak, belge türü tanımında (DTD) varsayılan öznitelikler olarak tanımlanan öznitelikleri kaldırmaya ilişkin özel sınırlamalar vardır. Ait oldukları öğe kaldırılmadığı takdirde varsayılan öznitelikler kaldırılamaz. Varsayılan öznitelikler, varsayılan özniteliklerin bildirildiği öğeler için her zaman vardır. Varsayılan bir özniteliği bir <xref:System.Xml.XmlAttributeCollection> veya <xref:System.Xml.XmlElement> ' den, öğesinin öğesine eklenen <xref:System.Xml.XmlAttributeCollection> bir değiştirme özniteliğinde, belirtilen varsayılan değere başlatıldığında kaldırır. Olarak `<book att1="1" att2="2" att3="3"></book>`tanımlanmış bir öğeye sahipseniz, üç varsayılan özniteliğin bildirildiği bir `book` öğeye sahip olursunuz. XML belge nesne modeli `book` (DOM) uygulama, bu öğe olduğu sürece, ve `att1` `att2` `att3`' nin bu üç varsayılan özniteliğine sahiptir.  
  
 İle <xref:System.Xml.XmlAttribute>çağrıldığında <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> yöntemi, bir öznitelik değer olmadan mevcut olamaz, özniteliği String. Empty olarak ayarlanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
