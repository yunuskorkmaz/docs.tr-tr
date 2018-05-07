---
title: DOM öğesi düğümünde öznitelikleri kaldırılıyor
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 758ce84390c9ba47e3eb56e1feb293a4cf0408a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a>DOM öğesi düğümünde öznitelikleri kaldırılıyor
Öznitelikleri kaldırmak için birçok yolu vardır. Bir öznitelik Koleksiyondan kaldırılacak tekniktir. Bunu yapmak için aşağıdaki adımlar gerçekleştirilir:  
  
1.  Öznitelik koleksiyonu öğesi kullanımından almak `XmlAttributeCollection attrs = elem.Attributes;`.  
  
2.  Öznitelik üç yöntemden birini kullanarak özniteliği koleksiyondan kaldırın:  
  
    -   Kullanım <xref:System.Xml.XmlAttributeCollection.Remove%2A> belirli bir özniteliği kaldırmak için.  
  
    -   Kullanım <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> tüm öznitelikleri koleksiyondan kaldırmak ve özniteliklere öğe bırakın.  
  
    -   Kullanım <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> dizin numarasını kullanarak bir özniteliği öznitelik Koleksiyondan kaldırılacak.  
  
 Aşağıdaki yöntemlerden öznitelikleri öğesi düğümünden kaldırın.  
  
-   Kullanım <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> öznitelik koleksiyonu kaldırmak için.  
  
-   Kullanım <xref:System.Xml.XmlElement.RemoveAttribute%2A> adıyla tek bir öznitelik Koleksiyondan kaldırılacak.  
  
-   Kullanım <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> tek bir öznitelik tarafından dizin numarasını Koleksiyondan kaldırılacak.  
  
 Bir daha fazla öğe almak, öznitelik öznitelik koleksiyonundan almak ve öznitelik düğümü doğrudan kaldırmak için alternatiftir. Öznitelik öznitelik koleksiyonundan almak için bir ad kullanabilirsiniz `XmlAttribute attr = attrs["attr_name"];`, bir dizin `XmlAttribute attr = attrs[0];`, veya ad alanı adıyla tam olarak niteleme `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.  
  
 Öznitelikleri kaldırmak için kullanılan yöntem bağımsız olarak, varsayılan öznitelikler belge türü tanımı (DTD) olarak tanımlanan öznitelikleri kaldırma özel sınırlamalar vardır. Ait oldukları öğesi kaldırılmadığı sürece varsayılan öznitelikleri kaldırılamaz. Varsayılan öznitelikleri her zaman için bildirilen varsayılan özniteliklere sahip öğeleri yok. Bir varsayılan özniteliğinden kaldırma bir <xref:System.Xml.XmlAttributeCollection> veya <xref:System.Xml.XmlElement> değiştirme özniteliği sonuçlarında eklenen içine <xref:System.Xml.XmlAttributeCollection> öğesinin varsayılan değerin bildirildi başlatıldı. Olarak tanımlanan bir öğe varsa `<book att1="1" att2="2" att3="3"></book>`, sahip olduğunuz sonra bir `book` üç varsayılan özniteliklerle öğesi bildirildi. XML belge nesne modeli (DOM) uygulama garanti sürece bu `book` öğesi var, bu üç varsayılan özniteliklerini sahip `att1`, `att2`, ve `att3`.  
  
 İle çağrıldığında bir <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> yöntemi bir özniteliği olmayan bir değer bulunduğundan bu özniteliğin değeri String.Empty için ayarlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
