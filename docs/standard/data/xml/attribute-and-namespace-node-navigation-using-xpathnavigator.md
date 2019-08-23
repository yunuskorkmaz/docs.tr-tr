---
title: XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4188896fb36d8535f86b245c3b1942f5a058da9b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936829"
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a>XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme
<xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> [](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) Sınıfı, bir veya nesnesi içindeki düğüm kümelerinde gezinmek için kullanılan ilk küme, bir veya nesne içindeki düğüm kümelerine gitmek için kullanılır. <xref:System.Xml.XPath.XPathNavigator> Bu konuda açıklanan ikinci küme, <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesne içindeki *öznitelik ve ad alanı düğümlerine* gezinmek için kullanılır.  
  
## <a name="attribute-node-navigation"></a>Öznitelik düğümü gezintisi  
 Öznitelikler bir öğenin alt öğeleri değil, bir öğenin özellikleridir. Bu ayrım, eşdüzey, üst ve alt düğümlerde gezinmek için <xref:System.Xml.XPath.XPathNavigator> kullanılan sınıfının yöntemleri nedeniyle önemlidir.  
  
 Örneğin, <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> yöntemleri bir öğeden bir özniteliğe veya öznitelikler arasında gezinmek için kullanılmaz. Bunun yerine, özniteliklerin farklı gezinti yöntemleri vardır.  
  
 Aşağıda, <xref:System.Xml.XPath.XPathNavigator> sınıfının öznitelik gezinti yöntemleri verilmiştir.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 Geçerli düğüm bir öğe olduğunda, öğesiyle ilişkili herhangi bir öznitelik olup <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> olmadığını görmek için özelliğini kullanabilirsiniz. Bir öğenin öznitelikleri olduğunu bilindikten sonra özniteliklere erişmek için birden çok yöntem vardır. Öğesinden tek bir özniteliği almak için <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A> yöntemini kullanın. Öğesini belirli bir <xref:System.Xml.XPath.XPathNavigator> özniteliğe taşımak için <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A> yöntemini kullanın. Ayrıca, yöntemini kullanarak <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A> bir öğenin her özniteliği üzerinde yineleyebilir ve ardından <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A> yöntemine birden çok çağrı yapabilirsiniz.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A> Nesnebir<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>öznitelik veya ad alanı <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> `false`düğümüne yerleştirilse,,,,, veyöntemleriherzamandöndürülür,<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A> <xref:System.Xml.XPath.XPathNavigator> ve konumunu <xref:System.Xml.XPath.XPathNavigator>etkilemez. Özel durumlar <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>ve <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> yöntemlerdir.  
  
## <a name="namespace-node-navigation"></a>Ad alanı düğümü gezintisi  
 Her bir öğe, öğe için kapsam içindeki bir ad alanı URI 'sine bağlanan her ayrı ad alanı öneki için bir tane olan ilişkili bir ad alanı düğümü kümesine sahiptir (her bir XML belgesinde örtülü `http://www.w3.org/XML/1998/namespace` olarak belirtilen XML ön eki de dahil olmak üzere) diğeri ise varsayılan ad alanı için bir öğe kapsamındadır. Bu ad alanı düğümler üst öğedir; Ancak, bir ad alanı düğümü alt öğesi üst öğesi değil.  
  
 Özniteliklerde <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> olduğu gibi, ve <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> yöntemleri bir öğeden bir ad alanı düğümüne veya ad alanı düğümleri arasında gezinmek için kullanılmaz. Bunun yerine, ad alanı düğümlerinin farklı gezinme yöntemleri vardır.  
  
 Aşağıda, <xref:System.Xml.XPath.XPathNavigator> sınıfının ad alanı gezinti yöntemleri verilmiştir.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 Bir XML belgesindeki her öğe için kapsamda her zaman en az bir ad alanı düğümü vardır. Bu, önek `xml` ve ad alanı URI 'si `http://www.w3.org/XML/1998/namespace`olan ad alanı düğümüdür. Belirli bir önek verilen kapsamdaki bir ad alanı URI 'sini almak için <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A> yöntemini kullanın. <xref:System.Xml.XPath.XPathNavigator> Nesneyi belirli bir ad alanı düğümüne taşımak için <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A> yöntemini kullanın. Ayrıca, yöntemini kullanarak <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> bir öğenin kapsamındaki her bir ad alanı düğümünü yineleyebilirsiniz ve sonra <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemi için birden çok çağrı yapabilirsiniz.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A> Nesnebir<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>öznitelik veya ad alanı <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> `false`düğümüne yerleştirilse,,,,, veyöntemleriherzamandöndürülür,<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A> <xref:System.Xml.XPath.XPathNavigator> ve konumunu <xref:System.Xml.XPath.XPathNavigator>etkilemez. Özel durumlar <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>ve <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> yöntemlerdir.  
  
### <a name="the-xpathnamespacescope-enumeration"></a>XPathNamespaceScope numaralandırması  
 Ad alanı düğümlerine gezinirken <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> , <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> ve yöntemleri <xref:System.Xml.XPath.XPathNamespaceScope> parametresiyle çağrılabilir. Bu yöntemler, hiçbir parametre olmadan çağrılan karşılıklarından farklı davranır. Numaralandırmada <xref:System.Xml.XPath.XPathNamespaceScope.All> ,<xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>veya değerleri<xref:System.Xml.XPath.XPathNamespaceScope.Local>vardır. <xref:System.Xml.XPath.XPathNamespaceScope>  
  
 Aşağıdaki örneklerde, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemleri tarafından bir XML belgesindeki çeşitli kapsamlardaki hangi ad alanlarının döndürüldüğü gösterilmektedir.  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 Ad alanı dizisi (, <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> yöntemi çağrıldıktan sonra, ve <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemine bir dizi çağrı bir dizi çağrı yapıldıktan sonra konumlandırılır) aşağıdaki gibidir.  
  
- Üzerine `element2`getirildiğinde: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`ve. `xmlns:xml="http://www.w3.org/XML/1998/namespace"`  
  
- Üzerine `element1`getirildiğinde: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`ve. `xmlns:xml="http://www.w3.org/XML/1998/namespace"`  
  
- Şu konuma yerleştirilme `root`:`xmlns:xml="http://www.w3.org/XML/1998/namespace".`  
  
> [!NOTE]
> Sınıfı <xref:System.Xml.XPath.XPathNavigator> , ters belge düzeninde ad alanı düğümleri döndürür. Bu nedenle <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> , temelde geçerli kapsamdaki son ad alanı düğümüne gider.  
  
 Aşağıdaki örneklerde, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemleri <xref:System.Xml.XPath.XPathNamespaceScope> tarafından bir XML belgesindeki çeşitli kapsamlar için belirtilen Numaralandırmadaki hangi ad alanlarının döndürüldüğü gösterilmektedir.  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 Üzerinde `child2`konumlandırıldığında, ad alanı sırası ( <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> yöntemi çağrıldıktan sonra <xref:System.Xml.XPath.XPathNavigator> , ve <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemine bir dizi çağrı bir dizi çağrı yapıldıktan sonra) aşağıdaki gibidir.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.All>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, ,,`xmlns:b="http://www.contoso.com/b"`, ,`xmlns="http://www.contoso.com"`ve .`xmlns:xml="http://www.w3.org/XML/1998/namespace"` `xmlns=""` `xmlns:a="http://www.contoso.com/a"`  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, ,`xmlns=""` ,`xmlns:a="http://www.contoso.com/a"`ve. `xmlns:b="http://www.contoso.com/b"` `xmlns="http://www.contoso.com"`  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
> Sınıfı <xref:System.Xml.XPath.XPathNavigator> , ters belge düzeninde ad alanı düğümleri döndürür. Bu nedenle <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> , temelde geçerli kapsamdaki son ad alanı düğümüne gider.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak Düğüm Kümesinde Gezinme](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Ayıklama](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
