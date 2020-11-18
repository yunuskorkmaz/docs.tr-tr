---
title: Dönüşümlerdeki Sonuç Ağacı Parçası
ms.date: 03/30/2017
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
ms.openlocfilehash: e5ca285c0b5d6c32d15647508c611a47ed97ee03
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823569"
---
# <a name="result-tree-fragment-in-transformations"></a>Dönüşümlerdeki Sonuç Ağacı Parçası

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor. Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> . Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .

 Sonuç ağacı parçaları olarak da bilinen sonuç ağacı parçaları, özel bir düğüm kümesi türünden başka hiçbir şey değildir. Bir düğüm kümesinde gerçekleştirilebilecek her türlü işlevi gerçekleştirebilirsiniz. Ayrıca, işlevi kullanarak bir sonuç ağacı parçasını bir düğüm kümesine dönüştürebilir `node-set()` ve ardından bunu bir düğüm kümesinin kullanılabileceği herhangi bir yerde kullanabilirsiniz.

 Bir sonuç ağacı parçası, bir `<xsl:variable>` veya `<xsl:param>` öğesini bir stil sayfasında belirli bir biçimde kullanmanın sonucu olarak oluşturulur. Ve öğeleri için sözdizimi `variable` `parameter` aşağıdaki gibidir:

```xml
<xsl:param name=Qname select= XPath Expression >
    template body
</xsl:param>

<xsl:variable name=Qname select=XPath Expression >
    template body
</xsl:variable>
```

Öğesi için `parameter` , değer nitelenmiş ada ( `Qname` ) birkaç şekilde atanır. Öznitelik içindeki XML Path Language (XPath) ifadesinden içerik döndürerek `select` veya şablon gövdesinin içeriğini atayarak parametreye varsayılan bir değer atayabilirsiniz.

Öğesi için `variable` , değer de çeşitli yollarla atanır. Özniteliği özniteliğinde XPath ifadesinden içerik döndürerek `select` veya şablon gövdesinin içeriğini atayarak atayabilirsiniz.

Hem hem de `parameter` `variable` öğeleri Için, XPath ifadesi tarafından bir değer atanırsa, dört temel XPath türünden biri döndürülür: Boolean, dize, sayı veya düğüm kümesi. Değer boş olmayan bir şablon gövdesi kullanılarak verildiğinde, bir XPath olmayan veri türü döndürülür ve sonuç ağacı parçası olur.

Bir değişken dört temel XPath veri türünden biri yerine bir sonuç ağacı parçasına bağlandığında, bu bir XPath sorgusunun dört XPath nesne türünden biri olmayan bir tür döndürdüğü tek zaman olur. Sonuç ağacı parçaları ve davranışları, [World Wide Web Konsorsiyumu (W3C) belirtiminde](https://www.w3.org/TR/xslt-10/), Bölüm 11,1 ' de, Bölüm ' deki [sonuç ağacı 11,6 parçalarında](https://www.w3.org/TR/xslt-10/#section-Result-Tree-Fragments) , [parametrelere parametreler geçirilerek](https://www.w3.org/TR/xslt-10/#section-Passing-Parameters-to-Templates)ele alınmıştır. Ayrıca, [Bölüm 1 giriş](https://www.w3.org/TR/xslt-10/#section-Introduction) , şablonların, sonuç ağacı parçaları döndüren veya oluşturan XSLT ad alanından nasıl öğe içerebileceğini açıklar.

Kavramdaki bir sonuç ağacı parçası, tek bir kök düğümden daha fazla şey olmayan bir düğüm kümesi gibi davranır. Ancak, döndürülen düğümlerin geri kalanı alt düğümlerdir. Alt düğümleri programlı bir şekilde görmek için, sonuç ağacı parçasını öğesini kullanarak sonuç ağacına kopyalayın `<xsl:copy-of>` . Kopya gerçekleştirildiğinde, tüm alt düğümler de sıradaki sonuç ağacına kopyalanır. `copy`Veya `copy-of` kullanılana kadar, sonuç ağacı parçası sonuç ağacının bir parçası veya dönüşümden çıktı değildir.

Sonuç ağacı parçasının döndürülen düğümlerini yinelemek için, <xref:System.Xml.XPath.XPathNavigator> kullanılır. Aşağıdaki kod örneği, XML içeren bir parametre ile işlevi çağırarak bir stil sayfası içinde bir sonuç ağacı parçasının nasıl oluşturulacağını gösterir `fragment` .

```xml
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"
                xmlns:user="http://www.adventure-works.com"
                version="1.0">
    <xsl:var name="fragment">
        <node1>
            <node2/>
        </node1>
    <xsl:var>

  <msxsl:script language="C#" implements-prefix="user">
    function NodeFragment(XPathNavigator nav)
    {
      if (nav.HasSelection == false)
        XPathNavigator.MoveToNext();
      return;
    }
  </msxsl:script>

    <xsl:template match="/">
            <xsl:value-of select="user:NodeFragment(msxml:node-set($fragment))"/>
    </xsl:template>
</xsl:stylesheet>
```

Burada, zengin metin biçimi (RTF) ve bu nedenle bir düğüm kümesine Dönüştürülmeyen bir sonuç ağacı parçası olan bir değişken gösteren başka bir örnek verilmiştir. Bunun yerine, bir betik işlevine geçirilir ve <xref:System.Xml.XPath.XPathNavigator> düğümler üzerinde gezinmek için kullanılır.

```xml
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
        xmlns:msxsl="urn:schemas-microsoft-com:xslt"
        xmlns:user="urn:books"
        exclude-result-prefixes="msxsl">

<xsl:output method="xml" indent="yes" omit-xml-declaration="yes"/>

<xsl:variable name="node-fragment">
    <book>Book1</book>
    <book>Book2</book>
    <book>Book3</book>
    <book>Book4</book>
</xsl:variable>

<msxsl:script implements-prefix="user" language="c#">

<![CDATA[
    string func(XPathNavigator nav)
    {
        bool b = nav.MoveToFirstChild();
        if (b)
            return nav.Value;
        else
            return "Does not exist";
    }

]]>

</msxsl:script>

<xsl:template match="/">
    <first_book>
        <xsl:value-of select="user:func($node-fragment)"/>
    </first_book>
</xsl:template>

</xsl:stylesheet>
```

Bu stil sayfasıyla herhangi bir XML dönüştürmenin sonucu aşağıdaki çıktıda gösterilmektedir.

## <a name="output"></a>Çıkış

```xml
<first_book xmlns:user="urn:books">Book1</first_book>
```

Yukarıda belirtildiği gibi, `node-set` işlevi bir sonuç ağacı parçasını bir düğüm kümesine dönüştürmenize olanak sağlar. Elde edilen düğüm, her zaman ağacın kök düğümü olan tek bir düğüm içerir. Bir sonuç ağacı parçasını bir düğüm kümesine dönüştürürseniz, for-each ifadesinde veya bir öznitelik değerinde olduğu gibi normal bir düğüm kümesinin kullanıldığı her yerde kullanabilirsiniz `select` . Aşağıdaki kod satırları bir düğüm kümesine dönüştürülmekte olan ve düğüm kümesi olarak kullanılan parçayı gösterir:

`<xsl:for-each select="msxsl:node-set($node-fragment)">`

`<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`

Bir parça bir düğüm kümesine dönüştürüldüğünde, <xref:System.Xml.XPath.XPathNavigator> üzerinde gezinmek için artık kullanamazsınız. Bir düğüm kümesi için, <xref:System.Xml.XPath.XPathNodeIterator> bunun yerine kullanın.

Aşağıdaki örnekte, `$var` stil sayfasındaki düğüm ağacı olan bir değişkendir. İşleviyle birlikte, for-each deyimleri, `node-set` kullanıcının bu ağacı üzerinde bir düğüm kümesi olarak yinemasına olanak tanır.

```xml
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"
                xmlns:user="http://www.adventure-works.com"
                version="1.0">
    <xsl:variable name="states">
        <node1>AL</node1>
        <node1>CA</node1>
        <node1>CO</node1>
        <node1>WA</node1>
    </xsl:variable>

    <xsl:template match="/">
            <xsl:for-each select="msxsl:node-set($states)"/>
    </xsl:template>
</xsl:stylesheet>
```

Burada, RTF 'deki bir değişkene ait başka bir örnek ve bu nedenle, bir komut dosyası işlevine XPathNodeIterator olarak geçirilmeden önce bir düğüm kümesine dönüştürülecek olan sonuç ağacı parçası türü bir örnektir.

```xml
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
        xmlns:msxsl="urn:schemas-microsoft-com:xslt"
        xmlns:user="urn:books"
        exclude-result-prefixes="msxsl">

<xsl:output method="xml" indent="yes" omit-xml-declaration="yes"/>

<xsl:variable name="node-fragment">
    <book>Book1</book>
    <book>Book2</book>
    <book>Book3</book>
    <book>Book4</book>
</xsl:variable>

<msxsl:script implements-prefix="user" language="c#">

<![CDATA[
    string func(XPathNodeIterator it)
    {
        it.MoveNext();
        return it.Current.Value;
        //it.Current returns XPathNavigator positioned on the current node
    }

]]>

</msxsl:script>
<xsl:template match="/">
    <books>
        <xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>
    </books>
</xsl:template>

</xsl:stylesheet>
```

XML 'nin bu stil sayfasıyla dönüştürülmesi sonucu aşağıda verilmiştir:

```xml
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XPath.XPathNodeIterator>
- [XslTransform Sınıfı ile XSLT Dönüşümleri](xslt-transformations-with-the-xsltransform-class.md)
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](xsltransform-class-implements-the-xslt-processor.md)
