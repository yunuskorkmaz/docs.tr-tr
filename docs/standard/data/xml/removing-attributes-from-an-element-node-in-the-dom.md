---
title: DOM’da Bir Öğe Düğümünden Öznitelikleri Kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
ms.openlocfilehash: 0ac8528d52ef09aab99c76aea9378c0188fa66d4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292026"
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a>DOM’da Bir Öğe Düğümünden Öznitelikleri Kaldırma
Öznitelikleri kaldırmanın birçok yolu vardır. Bir teknik, öznitelik koleksiyonundan kaldırmektir. Bunu yapmak için aşağıdaki adımlar gerçekleştirilir:  
  
1. Öğesini kullanarak öğesinden öznitelik koleksiyonunu alın `XmlAttributeCollection attrs = elem.Attributes;` .  
  
2. Öznitelik koleksiyonundan özniteliği, üç yöntemden birini kullanarak kaldırın:  
  
    - <xref:System.Xml.XmlAttributeCollection.Remove%2A>Belirli bir özniteliği kaldırmak için kullanın.  
  
    - <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A>Koleksiyondan tüm öznitelikleri kaldırmak ve öğeyi hiçbir öznitelik olmadan bırakmak için kullanın.  
  
    - Öznitelik <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> koleksiyonundan özniteliği Dizin numarasını kullanarak kaldırmak için kullanın.  
  
 Aşağıdaki yöntemler öğe düğümünden öznitelikleri kaldırır.  
  
- <xref:System.Xml.XmlElement.RemoveAllAttributes%2A>Öznitelik koleksiyonunu kaldırmak için kullanın.  
  
- <xref:System.Xml.XmlElement.RemoveAttribute%2A>Koleksiyondan ada göre tek bir özniteliği kaldırmak için kullanın.  
  
- <xref:System.Xml.XmlElement.RemoveAttributeAt%2A>Koleksiyondan dizin numarasına göre tek bir özniteliği kaldırmak için kullanın.  
  
 Diğer bir seçenek de öğeyi almak, öznitelik koleksiyonundan özniteliği almak ve öznitelik düğümünü doğrudan kaldırkullanmaktır. Öznitelik koleksiyonundan özniteliği almak için bir ad, `XmlAttribute attr = attrs["attr_name"];` , Dizin `XmlAttribute attr = attrs[0];` veya ad alanıyla tam olarak niteleyerek adı kullanabilirsiniz `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]` .  
  
 Öznitelikleri kaldırmak için kullanılan yöntemden bağımsız olarak, belge türü tanımında (DTD) varsayılan öznitelikler olarak tanımlanan öznitelikleri kaldırmaya ilişkin özel sınırlamalar vardır. Ait oldukları öğe kaldırılmadığı takdirde varsayılan öznitelikler kaldırılamaz. Varsayılan öznitelikler, varsayılan özniteliklerin bildirildiği öğeler için her zaman vardır. Varsayılan bir özniteliği bir <xref:System.Xml.XmlAttributeCollection> veya ' den, <xref:System.Xml.XmlElement> öğesinin öğesine eklenen bir değiştirme özniteliğinde, <xref:System.Xml.XmlAttributeCollection> belirtilen varsayılan değere başlatıldığında kaldırır. Olarak tanımlanmış bir öğeye sahipseniz `<book att1="1" att2="2" att3="3"></book>` , `book` üç varsayılan özniteliğin bildirildiği bir öğeye sahip olursunuz. XML Belge Nesne Modeli (DOM) uygulama, bu öğe olduğu sürece, `book` ve ' nin bu üç varsayılan özniteliğine sahiptir `att1` `att2` `att3` .  
  
 İle çağrıldığında yöntemi, bir <xref:System.Xml.XmlAttribute> <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> öznitelik değer olmadan mevcut olamaz, özniteliği String. Empty olarak ayarlanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
