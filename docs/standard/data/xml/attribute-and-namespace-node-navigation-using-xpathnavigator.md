---
title: XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
ms.openlocfilehash: 90c8fe7450a6ca853aaea452e30a292dbdcd9d98
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291623"
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a>XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme
<xref:System.Xml.XPath.XPathNavigator>Sınıfı, bir veya nesnesi içindeki düğüm kümelerinde gezinmek için kullanılan ilk küme, bir veya nesne içindeki *düğüm kümelerine* gitmek için kullanılır [Node Set Navigation Using XPathNavigator](node-set-navigation-using-xpathnavigator.md) <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> . Bu konuda açıklanan ikinci küme, veya nesne içindeki *öznitelik ve ad alanı düğümlerine* gezinmek için kullanılır <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> .  
  
## <a name="attribute-node-navigation"></a>Öznitelik düğümü gezintisi  
 Öznitelikler bir öğenin alt öğeleri değil, bir öğenin özellikleridir. Bu ayrım, <xref:System.Xml.XPath.XPathNavigator> eşdüzey, üst ve alt düğümlerde gezinmek için kullanılan sınıfının yöntemleri nedeniyle önemlidir.  
  
 Örneğin, <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> yöntemleri bir öğeden bir özniteliğe veya öznitelikler arasında gezinmek için kullanılmaz. Bunun yerine, özniteliklerin farklı gezinti yöntemleri vardır.  
  
 Aşağıda, sınıfının öznitelik gezinti yöntemleri verilmiştir <xref:System.Xml.XPath.XPathNavigator> .  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 Geçerli düğüm bir öğe olduğunda, <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> öğesiyle ilişkili herhangi bir öznitelik olup olmadığını görmek için özelliğini kullanabilirsiniz. Bir öğenin öznitelikleri olduğunu bilindikten sonra özniteliklere erişmek için birden çok yöntem vardır. Öğesinden tek bir özniteliği almak için <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A> yöntemini kullanın. <xref:System.Xml.XPath.XPathNavigator>Öğesini belirli bir özniteliğe taşımak için <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A> yöntemini kullanın. Ayrıca, yöntemini kullanarak bir öğenin her özniteliği üzerinde yineleyebilir ve <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A> ardından yöntemine birden çok çağrı yapabilirsiniz <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A> .  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator>Nesne bir öznitelik veya ad alanı düğümüne yerleştirilse,,,, <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A> , <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> yöntemleri her zaman döndürülür `false` ve konumunu etkilemez <xref:System.Xml.XPath.XPathNavigator> . Özel durumlar <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> , <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> yöntemlerdir.  
  
## <a name="namespace-node-navigation"></a>Ad alanı düğümü gezintisi  
 Her bir öğe, öğe için kapsamdaki bir ad alanı URI 'sine (ad alanına bağlanan XML öneki dahil olmak üzere) bir tane olan bir ad alanı düğümü kümesine sahiptir (her bir `http://www.w3.org/XML/1998/namespace` XML belgesinde örtülü olarak bildirildiği) ve biri öğesi için kapsamdadır. Bu ad alanı düğümler üst öğedir; Ancak, bir ad alanı düğümü alt öğesi üst öğesi değil.  
  
 Özniteliklerde olduğu gibi, <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> yöntemleri bir öğeden bir ad alanı düğümüne veya ad alanı düğümleri arasında gezinmek için kullanılmaz. Bunun yerine, ad alanı düğümlerinin farklı gezinme yöntemleri vardır.  
  
 Aşağıda, sınıfının ad alanı gezinti yöntemleri verilmiştir <xref:System.Xml.XPath.XPathNavigator> .  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 Bir XML belgesindeki her öğe için kapsamda her zaman en az bir ad alanı düğümü vardır. Bu, önek `xml` ve ad alanı URI 'si olan ad alanı düğümüdür `http://www.w3.org/XML/1998/namespace` . Belirli bir önek verilen kapsamdaki bir ad alanı URI 'sini almak için yöntemini kullanın <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A> . <xref:System.Xml.XPath.XPathNavigator>Nesneyi belirli bir ad alanı düğümüne taşımak için <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A> yöntemini kullanın. Ayrıca, yöntemini kullanarak bir öğenin kapsamındaki her bir ad alanı düğümünü yineleyebilirsiniz ve <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> sonra yöntemi için birden çok çağrı yapabilirsiniz <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> .  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator>Nesne bir öznitelik veya ad alanı düğümüne yerleştirilse,,,, <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A> , <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> yöntemleri her zaman döndürülür `false` ve konumunu etkilemez <xref:System.Xml.XPath.XPathNavigator> . Özel durumlar <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> , <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> yöntemlerdir.  
  
### <a name="the-xpathnamespacescope-enumeration"></a>XPathNamespaceScope numaralandırması  
 Ad alanı düğümlerine gezinirken, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemleri <xref:System.Xml.XPath.XPathNamespaceScope> parametresiyle çağrılabilir. Bu yöntemler, hiçbir parametre olmadan çağrılan karşılıklarından farklı davranır. <xref:System.Xml.XPath.XPathNamespaceScope>Numaralandırmada <xref:System.Xml.XPath.XPathNamespaceScope.All> , veya değerleri vardır <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml> <xref:System.Xml.XPath.XPathNamespaceScope.Local> .  
  
 Aşağıdaki örneklerde, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemleri tarafından bir XML belgesindeki çeşitli kapsamlardaki hangi ad alanlarının döndürüldüğü gösterilmektedir.  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 Ad alanı dizisi (, <xref:System.Xml.XPath.XPathNavigator> yöntemi çağrıldıktan sonra, ve <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> yöntemine bir dizi çağrı bir dizi çağrı yapıldıktan sonra konumlandırılır <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> ) aşağıdaki gibidir.  
  
- Üzerine getirildiğinde `element2` : `xmlns:books="http://www.contoso.com/books"` , `xmlns="http://www.contoso.com"` ve `xmlns:xml="http://www.w3.org/XML/1998/namespace"` .  
  
- Üzerine getirildiğinde `element1` : `xmlns:books="http://www.contoso.com/books"` , `xmlns="http://www.contoso.com"` ve `xmlns:xml="http://www.w3.org/XML/1998/namespace"` .  
  
- Şu konuma yerleştirilme `root` :`xmlns:xml="http://www.w3.org/XML/1998/namespace".`  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator>Sınıfı, ters belge düzeninde ad alanı düğümleri döndürür. Bu nedenle, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> temelde geçerli kapsamdaki son ad alanı düğümüne gider.  
  
 Aşağıdaki örneklerde, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemleri tarafından <xref:System.Xml.XPath.XPathNamespaceScope> bir XML belgesindeki çeşitli kapsamlar için belirtilen Numaralandırmadaki hangi ad alanlarının döndürüldüğü gösterilmektedir.  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 Üzerinde konumlandırıldığında `child2` , ad alanı sırası ( <xref:System.Xml.XPath.XPathNavigator> yöntemi çağrıldıktan sonra, ve <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> yöntemine bir dizi çağrı bir dizi çağrı yapıldıktan sonra <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> ) aşağıdaki gibidir.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.All>: `xmlns:c="urn:c"` , `xmlns:a="urn:a"` , `xmlns=""` , `xmlns:b="http://www.contoso.com/b"` , `xmlns:a="http://www.contoso.com/a"` , `xmlns="http://www.contoso.com"` , ve `xmlns:xml="http://www.w3.org/XML/1998/namespace"` .  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>: `xmlns:c="urn:c"` , `xmlns:a="urn:a"` , `xmlns=""` , `xmlns:b="http://www.contoso.com/b"` , `xmlns:a="http://www.contoso.com/a"` ve `xmlns="http://www.contoso.com"` .  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator>Sınıfı, ters belge düzeninde ad alanı düğümleri döndürür. Bu nedenle, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> temelde geçerli kapsamdaki son ad alanı düğümüne gider.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak Düğüm Kümesinde Gezinme](node-set-navigation-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Ayıklama](extract-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme](accessing-strongly-typed-xml-data-using-xpathnavigator.md)
