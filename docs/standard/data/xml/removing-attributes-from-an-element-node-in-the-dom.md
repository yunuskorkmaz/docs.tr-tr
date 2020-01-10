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
  
1. `XmlAttributeCollection attrs = elem.Attributes;`kullanarak öğeden öznitelik koleksiyonunu alın.  
  
2. Öznitelik koleksiyonundan özniteliği, üç yöntemden birini kullanarak kaldırın:  
  
    - Belirli bir özniteliği kaldırmak için <xref:System.Xml.XmlAttributeCollection.Remove%2A> kullanın.  
  
    - Koleksiyondan tüm öznitelikleri kaldırmak ve öğeyi hiçbir öznitelik olmadan bırakmak için <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> kullanın.  
  
    - Öznitelik koleksiyonundan bir özniteliği Dizin numarasını kullanarak kaldırmak için <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> kullanın.  
  
 Aşağıdaki yöntemler öğe düğümünden öznitelikleri kaldırır.  
  
- Öznitelik koleksiyonunu kaldırmak için <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> kullanın.  
  
- Koleksiyondan ada göre tek bir özniteliği kaldırmak için <xref:System.Xml.XmlElement.RemoveAttribute%2A> kullanın.  
  
- Koleksiyondan dizin numarasına göre tek bir özniteliği kaldırmak için <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> kullanın.  
  
 Diğer bir seçenek de öğeyi almak, öznitelik koleksiyonundan özniteliği almak ve öznitelik düğümünü doğrudan kaldırkullanmaktır. Öznitelik koleksiyonundan özniteliği almak için, bir ad, `XmlAttribute attr = attrs["attr_name"];`, Dizin `XmlAttribute attr = attrs[0];`veya ad alanı `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`ile tam olarak niteleyerek adı kullanabilirsiniz.  
  
 Öznitelikleri kaldırmak için kullanılan yöntemden bağımsız olarak, belge türü tanımında (DTD) varsayılan öznitelikler olarak tanımlanan öznitelikleri kaldırmaya ilişkin özel sınırlamalar vardır. Ait oldukları öğe kaldırılmadığı takdirde varsayılan öznitelikler kaldırılamaz. Varsayılan öznitelikler, varsayılan özniteliklerin bildirildiği öğeler için her zaman vardır. Varsayılan bir özniteliği bir <xref:System.Xml.XmlAttributeCollection> veya <xref:System.Xml.XmlElement> kaldırmak, öğesinin <xref:System.Xml.XmlAttributeCollection> eklenen ve varsayılan değere başlatılan bir değiştirme özniteliğiyle sonuçlanır. `<book att1="1" att2="2" att3="3"></book>`olarak tanımlanmış bir öğeye sahipseniz, üç varsayılan özniteliğe göre bildirildiği bir `book` öğesi vardır. XML Belge Nesne Modeli (DOM) uygulama, bu `book` öğesinin var olduğu sürece `att1`, `att2`ve `att3`bu üç varsayılan özniteliğe sahiptir.  
  
 Bir <xref:System.Xml.XmlAttribute>ile çağrıldığında <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> yöntemi öznitelik değerini String. Empty olarak ayarlar, çünkü bir öznitelik değer olmadan bulunamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
