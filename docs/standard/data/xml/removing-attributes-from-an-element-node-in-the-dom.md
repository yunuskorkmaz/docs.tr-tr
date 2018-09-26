---
title: DOM'da bir öğe düğümünden öznitelikleri kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 65fd6d2baae29c72241350e4568faf09b9c71f39
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47114833"
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a>DOM'da bir öğe düğümünden öznitelikleri kaldırma
Öznitelikleri kaldırmak için birçok yolu vardır. Öznitelik koleksiyonundan kaldırabilirsiniz bir tekniktir. Bunu yapmak için aşağıdaki adımları gerçekleştirilir:  
  
1.  Öğesini kullanarak gelen öznitelik koleksiyonu alma `XmlAttributeCollection attrs = elem.Attributes;`.  
  
2.  Öznitelik, öznitelik koleksiyonundan üç yöntemden birini kullanarak kaldırın:  
  
    -   Kullanım <xref:System.Xml.XmlAttributeCollection.Remove%2A> belirli bir öznitelik kaldırmak için.  
  
    -   Kullanım <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> tüm öznitelikler koleksiyondan Kaldır ve özniteliklere bir öğe bırakın.  
  
    -   Kullanım <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> bir özniteliği öznitelik koleksiyonundan dizin numarası kullanarak kaldırmak için.  
  
 Aşağıdaki yöntemlerden öğe düğümünden öznitelikleri kaldırın.  
  
-   Kullanım <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> öznitelik koleksiyonundan kaldırılamadı.  
  
-   Kullanım <xref:System.Xml.XmlElement.RemoveAttribute%2A> tek bir öznitelik ada göre Koleksiyondan kaldırılacak.  
  
-   Kullanım <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> tek bir öznitelik koleksiyonundan dizin numarası ile kaldırmak için.  
  
 Öğesi, öznitelik koleksiyonundan öznitelik alma ve doğrudan öznitelik düğümü kaldırmak için bir daha fazla seçenek var. Öznitelik öznitelik koleksiyonundan almak için bir ad kullanabilirsiniz `XmlAttribute attr = attrs["attr_name"];`, dizin `XmlAttribute attr = attrs[0];`, veya ad alanı adıyla tam olarak uygun `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.  
  
 Öznitelikleri kaldırmak için kullanılan yöntem ne olursa olsun, varsayılan öznitelikler belge türü tanımı (DTD'nin) olarak tanımlanan öznitelikleri kaldırma hakkında özel sınırlamalar vardır. Ait oldukları öğesi kaldırılmadığı sürece, varsayılan öznitelikler kaldırılamaz. Her zaman, varsayılan öznitelikler bildirilmiş olan öğeler için varsayılan öznitelikleri yok. Varsayılan özniteliğinden kaldırma bir <xref:System.Xml.XmlAttributeCollection> veya <xref:System.Xml.XmlElement> değiştirme özniteliği sonuçlarında eklenen içine <xref:System.Xml.XmlAttributeCollection> bildirilen varsayılan değeri olarak başlatılan bir öğe. Olarak tanımlanan bir öğe varsa `<book att1="1" att2="2" att3="3"></book>`, sahip olduğunuz sonra bir `book` varsayılan öznitelikler üç öğeyle bildirilir. XML belge nesne modeli (DOM) uygulaması, garanti olduğu sürece bu `book` öğe varsa, bu üç varsayılan özniteliklerini sahip `att1`, `att2`, ve `att3`.  
  
 İle çağrıldığında bir <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> yöntemi gibi bir öznitelik, bir değer olmadan var olamaz bu özniteliğin değeri String.Empty için ayarlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
