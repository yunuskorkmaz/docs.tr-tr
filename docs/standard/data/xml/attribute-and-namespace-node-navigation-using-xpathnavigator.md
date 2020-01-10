---
title: XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
ms.openlocfilehash: 6809a2a47a9ca25a16a9be75a0a8a8b03f98a21d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711161"
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a>XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme
<xref:System.Xml.XPath.XPathNavigator> sınıfı, bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesne içindeki *düğüm kümelerinde* gezinmek için kullanılan, ilk küme, XPathNavigator ' yi [kullanarak düğüm kümesi gezinmede](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) bulunan iki gezinti yöntemi kümesi sağlar. Bu konuda açıklanan ikinci küme, bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesindeki *öznitelik ve ad alanı düğümlerine* gitmek için kullanılır.  
  
## <a name="attribute-node-navigation"></a>Öznitelik düğümü gezintisi  
 Öznitelikler bir öğenin alt öğeleri değil, bir öğenin özellikleridir. Bu ayrım, eşdüzey, üst ve alt düğümlerde gezinmek için kullanılan <xref:System.Xml.XPath.XPathNavigator> sınıfının yöntemleri nedeniyle önemlidir.  
  
 Örneğin, <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> yöntemleri bir öğeden bir özniteliğe veya öznitelikler arasında gezinmek için kullanılmaz. Bunun yerine, özniteliklerin farklı gezinti yöntemleri vardır.  
  
 <xref:System.Xml.XPath.XPathNavigator> sınıfının öznitelik gezinti yöntemleri aşağıda verilmiştir.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 Geçerli düğüm bir öğe olduğunda, öğesiyle ilişkili herhangi bir öznitelik olup olmadığını görmek için <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> özelliğini kullanabilirsiniz. Bir öğenin öznitelikleri olduğunu bilindikten sonra özniteliklere erişmek için birden çok yöntem vardır. Öğesinden tek bir özniteliği almak için <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A> yöntemini kullanın. <xref:System.Xml.XPath.XPathNavigator> belirli bir özniteliğe taşımak için <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A> yöntemini kullanın. Ayrıca, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A> yöntemini kullanarak bir öğenin her özniteliği üzerinde yineleyebilir ve ardından <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A> yöntemine birden çok çağrı yapabilirsiniz.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator> nesnesi bir öznitelik veya ad alanı düğümüne konumlandırıldığında, <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> yöntemleri her zaman `false`döndürür ve <xref:System.Xml.XPath.XPathNavigator>konumunu etkilemez. Özel durumlar <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>ve <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> yöntemleridir.  
  
## <a name="namespace-node-navigation"></a>Ad alanı düğümü gezintisi  
 Her bir öğe, öğe için kapsam içindeki bir ad alanı URI 'sine (`http://www.w3.org/XML/1998/namespace` ad alanına bağlanan XML öneki dahil) ve biri öğesi için kapsamında olan varsayılan ad alanı için olan her farklı ad alanı öneki için bir ilişkili ad alanı düğümleri kümesi içerir. Bu ad alanı düğümler üst öğedir; Ancak, bir ad alanı düğümü alt öğesi üst öğesi değil.  
  
 Özniteliklerde olduğu gibi, <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> yöntemleri bir öğeden bir ad alanı düğümüne veya ad alanı düğümleri arasında gezinmek için kullanılmaz. Bunun yerine, ad alanı düğümlerinin farklı gezinme yöntemleri vardır.  
  
 <xref:System.Xml.XPath.XPathNavigator> sınıfının ad alanı gezinti yöntemleri aşağıda verilmiştir.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 Bir XML belgesindeki her öğe için kapsamda her zaman en az bir ad alanı düğümü vardır. Bu, önek `xml` ve ad alanı URI 'SI `http://www.w3.org/XML/1998/namespace`olan ad alanı düğümüdür. Belirli bir önek verilen kapsamda bir ad alanı URI 'sini almak için <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A> yöntemini kullanın. <xref:System.Xml.XPath.XPathNavigator> nesnesini belirli bir ad alanı düğümüne taşımak için <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A> yöntemini kullanın. Ayrıca, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> yöntemini kullanarak ve sonra <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemine birden çok çağrı yaparak bir öğesi için kapsamdaki her bir ad alanı düğümünü yineleyebilirsiniz.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator> nesnesi bir öznitelik veya ad alanı düğümüne konumlandırıldığında, <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> yöntemleri her zaman `false`döndürür ve <xref:System.Xml.XPath.XPathNavigator>konumunu etkilemez. Özel durumlar <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>ve <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> yöntemleridir.  
  
### <a name="the-xpathnamespacescope-enumeration"></a>XPathNamespaceScope numaralandırması  
 Ad alanı düğümlerine gezinirken <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemleri bir <xref:System.Xml.XPath.XPathNamespaceScope> parametresiyle çağrılabilir. Bu yöntemler, hiçbir parametre olmadan çağrılan karşılıklarından farklı davranır. <xref:System.Xml.XPath.XPathNamespaceScope> numaralandırmasında <xref:System.Xml.XPath.XPathNamespaceScope.All>, <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>veya <xref:System.Xml.XPath.XPathNamespaceScope.Local>değerleri bulunur.  
  
 Aşağıdaki örneklerde, bir XML belgesindeki çeşitli kapsamlardaki <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemleri tarafından döndürülen ad alanları gösterilmektedir.  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 Ad alanı sırası (<xref:System.Xml.XPath.XPathNavigator> ad alanı, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> yöntemi çağrıldıktan sonra, ardından <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemine bir dizi çağrı yapıldıktan sonra) aşağıdaki gibidir.  
  
- `element2`konumlandırıldığında: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`ve `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- `element1`konumlandırıldığında: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`ve `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- `root`konumlandırıldığında: `xmlns:xml="http://www.w3.org/XML/1998/namespace".`  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator> sınıfı, ters belge düzeninde ad alanı düğümleri döndürür. Bu nedenle <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> temelde geçerli kapsamdaki son ad alanı düğümüne gider.  
  
 Aşağıdaki örneklerde, bir XML belgesindeki çeşitli kapsamlarda belirtilen <xref:System.Xml.XPath.XPathNamespaceScope> numaralandırmasında <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> ve <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemleri tarafından döndürülen ad alanları gösterilmektedir.  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 `child2`konumlandırıldığında, ad alanı sırası (<xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> yöntemi çağrıldıktan sonra <xref:System.Xml.XPath.XPathNavigator> ad alanı, ardından <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> yöntemine yapılan bir dizi çağrı) aşağıdaki gibidir.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.All>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, `xmlns="http://www.contoso.com"`ve `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`ve `xmlns="http://www.contoso.com"`.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator> sınıfı, ters belge düzeninde ad alanı düğümleri döndürür. Bu nedenle <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> temelde geçerli kapsamdaki son ad alanı düğümüne gider.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak Düğüm Kümesinde Gezinme](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Ayıklama](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
