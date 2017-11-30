---
title: "Özniteliği ve XPathNavigator kullanarak Namespace düğümü gezinme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 45e94954641e935597394b7cf04818c6c78ea675
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a>Özniteliği ve XPathNavigator kullanarak Namespace düğümü gezinme
<xref:System.Xml.XPath.XPathNavigator> İlk kümesi bulundu sınıfı iki Gezinti yöntemler kümesi sağlar, [düğüm kümesi Gezinti kullanarak XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) konu gezinmek için kullanılan *düğüm kümeleri* içinde bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesi. Bu konuda açıklanan ikinci küme gitmek için kullanılan *özniteliği ve ad alanı düğümleri* içinde bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesi.  
  
## <a name="attribute-node-navigation"></a>Öznitelik düğümü gezinme  
 Bir öğenin özelliklerini, bir öğenin alt öğeleri öznitelikleridir. Bu ayrım yöntemlerini nedeniyle önemlidir <xref:System.Xml.XPath.XPathNavigator> eşdüzey, üst ve alt düğümleri gitmek için kullanılan bir sınıftır.  
  
 Örneğin, <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> yöntemleri bir öğeyi bir öznitelik veya öznitelikler arasında gezinmek için kullanılmaz. Bunun yerine, gezinti farklı yöntemleri özniteliklere sahiptir.  
  
 Gezinti yöntemlerinin öznitelik verilmiştir <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 Geçerli düğüm öğenin olduğunda kullanabileceğiniz <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> öğeyle ilişkili öznitelikleri olup olmadığını görmek için özellik. Bilinen bir öğe öznitelikleri sonra özniteliklere erişme birden çok yöntemi vardır. Tek bir öznitelik öğesinden, almanızı <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A> yöntemi. Taşımak için <xref:System.Xml.XPath.XPathNavigator> , belirli bir öznitelik için kullanmak <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A> yöntemi. Kullanarak her bir öğe özniteliği yineleyebilirsiniz <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A> yöntemi, birden fazla çağrı arkasından <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A> yöntemi.  
  
> [!NOTE]
>  Zaman <xref:System.Xml.XPath.XPathNavigator> nesnesi, bir öznitelik veya ad alanı düğümde konumlandırılır <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> yöntemleri her zaman geri `false`, ve konumu üzerinde hiçbir etkisi <xref:System.Xml.XPath.XPathNavigator>. Özel durumlar <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, ve <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> yöntemleri.  
  
## <a name="namespace-node-navigation"></a>Namespace düğümü gezinme  
 Her öğe bir ad alanı URI'si öğesi kapsamına bağlı her farklı ad alanı öneki için bir ad alanı düğümleri kümesi vardır (XML önekini bağlı dahil olmak üzere `http://www.w3.org/XML/1998/namespace` her XML belgesinde örtülü olarak bildirilen ad alanı) ve öğe kapsamına ise varsayılan ad alanı için bir tane. Bu ad alanı düğümler üst öğedir; Ancak, bir ad alanı düğümü alt öğesi üst öğesi değil.  
  
 Özniteliklerle olduğu gibi <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> yöntemleri bir öğeyi bir ad alanı düğüme veya ad alanı düğümleri arasında gezinmek için kullanılmaz. Bunun yerine, ad alanı düğümlerin Gezinti farklı yöntemleri vardır.  
  
 Gezinti yöntemlerinin ad verilmiştir <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 Bulunmaktadır her zaman en az bir ad alanı düğümü kapsam için bir XML belgesi herhangi bir öğe. Bu ad alanı öneki ile düğümdür `xml` ve ad alanı URI'si `http://www.w3.org/XML/1998/namespace`. Ad alanı URI'si belirli bir önek verilen kapsam içinde almak kullanın <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A> yöntemi. Taşımak için <xref:System.Xml.XPath.XPathNavigator> kullanımı belirli ad alanı bir düğüme nesne <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A> yöntemi. Ayrıca bir öğe için kapsam içinde her ad alanı düğüm üzerinde kullanarak yineleyebilirsiniz <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> yöntemi için birden fazla çağrı tarafından izlenen <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemi.  
  
> [!NOTE]
>  Zaman <xref:System.Xml.XPath.XPathNavigator> nesnesi, bir öznitelik veya ad alanı düğümde konumlandırılır <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> yöntemleri her zaman geri `false`, ve konumu üzerinde hiçbir etkisi <xref:System.Xml.XPath.XPathNavigator>. Özel durumlar <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, ve <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> yöntemleri.  
  
### <a name="the-xpathnamespacescope-enumeration"></a>XPathNamespaceScope numaralandırması  
 Ad alanı düğümleri gezinirken <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemleri ile çağrılabilir bir <xref:System.Xml.XPath.XPathNamespaceScope> parametresi. Bu yöntemler dekiler parametresiz olarak adlandırılan farklı şekilde davranır. <xref:System.Xml.XPath.XPathNamespaceScope> Numaralandırma değerlerini sahip <xref:System.Xml.XPath.XPathNamespaceScope.All>, <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>, veya <xref:System.Xml.XPath.XPathNamespaceScope.Local>.  
  
 Aşağıdaki örnekler ne ad alanları tarafından döndürülen <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> bir XML belgesi çeşitli kapsamlarda adresindeki yöntemleri.  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 Ad alanı dizisi (ad alanı <xref:System.Xml.XPath.XPathNavigator> çağrıldıktan sonra üzerine yerleştirilmiş <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> çağrıları için bir dizi yöntem ve ardından <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemi) aşağıdaki gibidir.  
  
-   Üzerine getirildiğinde `element2`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, ve `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
-   Üzerine getirildiğinde `element1`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, ve `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
-   Üzerine getirildiğinde `root`:`xmlns:xml="http://www.w3.org/XML/1998/namespace".`  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator> Sınıfı ad alanı düğümleri ters belge sırada döndürür. Bu nedenle, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> temelde düğüm ad geçerli kapsamda son taşır.  
  
 Aşağıdaki örnekler ne ad alanları tarafından döndürülen <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemleriyle <xref:System.Xml.XPath.XPathNamespaceScope> bir XML belgesi çeşitli kapsamlarda konumunda belirtilen numaralandırması.  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 Üzerine getirildiğinde `child2`, ad alanı dizisi (ad alanı <xref:System.Xml.XPath.XPathNavigator> çağrıldıktan sonra üzerine yerleştirilmiş <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> çağrıları için bir dizi yöntem ve ardından <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemi) aşağıdaki gibidir.  
  
-   <xref:System.Xml.XPath.XPathNamespaceScope.All>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, `xmlns="http://www.contoso.com"`, ve `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
-   <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, ve `xmlns="http://www.contoso.com"`.  
  
-   <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator> Sınıfı ad alanı düğümleri ters belge sırada döndürür. Bu nedenle, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> temelde düğüm ad geçerli kapsamda son taşır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [XPath veri modelini kullanarak işlem XML verileri](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Düğüm kümesi Gezinti XPathNavigator kullanma](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 [XPathNavigator kullanarak XML veri ayıklamak](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 [XML verilerini XPathNavigator kullanarak yazılan kesinlikle erişme](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
