---
title: XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f2be5881a7f663b13dd13ffc0e0faf88afd7efc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647970"
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a>XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme
<xref:System.Xml.XPath.XPathNavigator> İçinde ilk belirlenen bulunan sınıf iki Gezinti yöntemler kümesi sağlar, [kullanarak düğüm kümesi Gezinti XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) konuya gitmek için kullanılan *düğüm kümeleri* içinde bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesne. Bu konuda, açıklanan ikinci küme gezinmek için kullanılan *öznitelik ve ad alanı düğümleri* içinde bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesne.  
  
## <a name="attribute-node-navigation"></a>Öznitelik düğümü Gezinti  
 Öznitelik, bir öğenin bir öğenin alt öğeleri özelliklerdir. Bu ayrım yöntemlerini nedeniyle önemlidir <xref:System.Xml.XPath.XPathNavigator> eşdüzey, üst ve alt düğümleri gezinmek için kullanılan sınıf.  
  
 Örneğin, <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> yöntemleri öğeden bir özniteliği veya öznitelikleri arasında gezinmek için kullanılmaz. Bunun yerine, öznitelikleri Gezinti farklı yöntemleri vardır.  
  
 Öznitelik gezinme yöntemlerinden biri aşağıda verilmiştir <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 Geçerli düğüm bir öğe olduğunda kullanabileceğiniz <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> öğeyle ilişkili herhangi bir özniteliği olup olmadığını görmek için özellik. Bilinen bir öğe öznitelikleri sonra özniteliklere erişim için birden fazla yöntem vardır. Tek bir öznitelik öğe alınacağını kullanın <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A> yöntemi. Taşımak <xref:System.Xml.XPath.XPathNavigator> belirli bir özniteliği kullanın <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A> yöntemi. Kullanarak her öğenin özniteliğini yineleyebilirsiniz <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A> yöntemi, birden çok çağrı ardından <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A> yöntemi.  
  
> [!NOTE]
>  Zaman <xref:System.Xml.XPath.XPathNavigator> nesne bir öznitelik veya ad alanı düğümünde konumlandırılmış <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> yöntemleri her zaman dönüş `false`, ve konumu üzerinde hiçbir etkisi <xref:System.Xml.XPath.XPathNavigator>. Özel durumlar <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, ve <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> yöntemleri.  
  
## <a name="namespace-node-navigation"></a>Namespace düğümünde gezinme  
 Her öğe ad alanı URI öğesi için kapsamdaki bağlı her ayrı ad alanı öneki için bir ad alanı düğümleri ilişkili bir ayarlanmış (XML öneki bağlı dahil olmak üzere `http://www.w3.org/XML/1998/namespace` her XML belgesinde örtük olarak bildirilen ad alanı) ve öğesi için kapsamdaki ise varsayılan ad alanı için bir tane. Bu ad alanı düğümler üst öğedir; Ancak, bir ad alanı düğümü alt öğesi üst öğesi değil.  
  
 Özniteliklerle olduğu gibi <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> yöntemleri öğeden bir ad alanı düğümü veya ad alanı düğümleri arasında gezinmek için kullanılmaz. Bunun yerine, ad alanı düğümleri Gezinti farklı yöntemleri vardır.  
  
 Ad alanı gezinme yöntemlerinden biri aşağıda verilmiştir <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 Yok her zaman en az bir ad alanı düğümü, XML belgesinde herhangi bir öğe için kapsama girer. Bu ad alanı öneki ile düğümüdür `xml` ve ad alanı URI `http://www.w3.org/XML/1998/namespace`. Ad alanı URI belirli bir önek belirtilen kapsamda almak için kullanın <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A> yöntemi. Taşımak <xref:System.Xml.XPath.XPathNavigator> belirli ad alanı düğümü, kullanım nesnesine <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A> yöntemi. Ayrıca her bir öğe için kapsamdaki ad alanı düğümü üzerinden kullanarak yineleyebilirsiniz <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> yöntemi izleyen birden çok çağrı tarafından <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemi.  
  
> [!NOTE]
>  Zaman <xref:System.Xml.XPath.XPathNavigator> nesne bir öznitelik veya ad alanı düğümünde konumlandırılmış <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> yöntemleri her zaman dönüş `false`, ve konumu üzerinde hiçbir etkisi <xref:System.Xml.XPath.XPathNavigator>. Özel durumlar <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, ve <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> yöntemleri.  
  
### <a name="the-xpathnamespacescope-enumeration"></a>XPathNamespaceScope numaralandırması  
 Ad alanı düğümleri gezinirken <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemleri ile çağrılabilir bir <xref:System.Xml.XPath.XPathNamespaceScope> parametresi. Bu yöntemler karşılıkları parametresiz olarak adlandırılan farklı davranır. <xref:System.Xml.XPath.XPathNamespaceScope> Sabit listesi değerlerinin sahip <xref:System.Xml.XPath.XPathNamespaceScope.All>, <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>, veya <xref:System.Xml.XPath.XPathNamespaceScope.Local>.  
  
 Aşağıdaki örnekler ad alanları tarafından getirilen <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntem ele çeşitli kapsamları bir XML belgesi.  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 Ad alanı dizisi (ad alanı <xref:System.Xml.XPath.XPathNavigator> bağlı çağırdıktan sonra konumlandırılmış <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> yöntemi, bir dizi çağrıda arkasından <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemi) aşağıdaki gibidir.  
  
- Üzerinde getirildiğinde `element2`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, ve `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- Üzerinde getirildiğinde `element1`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, ve `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- Üzerinde getirildiğinde `root`: `xmlns:xml="http://www.w3.org/XML/1998/namespace".`  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator> Sınıf ad alanı düğümleri belge ters sırada döndürür. Bu nedenle, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> temelde ad alanı düğümü geçerli kapsamda son taşır.  
  
 Aşağıdaki örnekler ad alanları tarafından getirilen <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemleriyle <xref:System.Xml.XPath.XPathNamespaceScope> numaralandırması bir XML belgesi çeşitli kapsamları belirtilebilir.  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 Üzerinde getirildiğinde `child2`, ad alanı dizisi (ad alanı <xref:System.Xml.XPath.XPathNavigator> bağlı çağırdıktan sonra konumlandırılmış <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> yöntemi, bir dizi çağrıda arkasından <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemi) aşağıdaki gibidir.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.All>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, `xmlns="http://www.contoso.com"`, ve `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, ve `xmlns="http://www.contoso.com"`.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator> Sınıf ad alanı düğümleri belge ters sırada döndürür. Bu nedenle, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> temelde ad alanı düğümü geçerli kapsamda son taşır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak Düğüm Kümesinde Gezinme](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Ayıklama](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
