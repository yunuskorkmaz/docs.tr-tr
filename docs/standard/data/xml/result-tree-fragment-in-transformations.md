---
title: Dönüşümlerdeki sonuç ağacı parçası
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 10449867a37863798a0da2df9111bcd7addfc6ef
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44269182"
---
# <a name="result-tree-fragment-in-transformations"></a>Dönüşümlerdeki sonuç ağacı parçası

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Sınıftır eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](migrating-from-the-xsltransform-class.md) daha fazla bilgi için.

 Sonucu ağacı parçalarını sonucu ağacı parçalarını olarak da bilinir, düğüm kümesi özel bir tür başka bir şey var. Bir düğüm kümesi üzerinde gerçekleştirilebilen bunlar üzerinde herhangi bir işlev gerçekleştirebilirsiniz. Ya da sonuç ağacı parçası kullanılarak ayarlanan bir düğüme dönüştürebilirsiniz `node-set()` işlev ve sonradan herhangi yerleştirileceği bir düğüm kümesi kullanılabilir kullanın.

 Sonuç ağacı parçası kullanarak sonucu olarak oluşturulan bir `<xsl:variable>` veya `<xsl:param>` belirli bir şekilde bir stil sayfası öğesinde. Sözdizimi `variable` ve `parameter` öğeleri aşağıdaki gibidir:

```xml
<xsl:param name=Qname select= XPath Expression >
    template body
</xsl:param>

<xsl:variable name=Qname select=XPath Expression >
    template body
</xsl:variable>
```

İçin `parameter` öğesi, değerin tam adı için atanır (`Qname`) çeşitli şekillerde. XML Path Language (XPath) ifade gelen içerik döndürerek parametre bir varsayılan değer atayabilirsiniz `select` özniteliği veya şablon gövdesi içeriğini göre atama.

İçin `variable` öğesi değeri de atandığı çeşitli yollarla. XPath ifadesinden içerik döndürerek atayabilirsiniz `select` özniteliği veya şablon gövdesi içeriğini göre atama.

Her ikisi için de `parameter` ve `variable` öğeleri XPath ifadesi tarafından atanmış bir değer ise ardından dört temel XPath türlerinden biri döndürülür: Boolean, dize, sayı veya düğüm kümesi. Boş şablon gövdesi kullanarak değeri belirtildiğinde, ardından döndürülen bir XPath olmayan veri türü ve bir sonuç ağacı parçası olacak.

Bir değişken dört temel XPath veri türlerinden biri yerine bir sonuç ağacı parçası bağlandığında, bu yalnızca bir kez olan bir XPath sorgusu dört XPath nesne türlerinden biri değil bir tür döndürür. Sonucu ağacı parçalarını ve davranışları açıklanmıştır [World Wide Web Consortium (W3C) belirtimi](https://www.w3.org/TR/xslt-10/), [11.1 sonucu ağacı parçalarını bölümünde](https://www.w3.org/TR/xslt-10/#section-Result-Tree-Fragments) aracılığıyla [11.6 geçirme bölümü Şablon parametreleri](https://www.w3.org/TR/xslt-10/#section-Passing-Parameters-to-Templates). Ayrıca, [1 giriş bölümünde](https://www.w3.org/TR/xslt-10/#section-Introduction) nasıl şablonları döndürür ya da sonuç ağacı parçalarını oluşturan XSLT ad alanından öğeler içerebilir açıklanır.

Bir sonuç ağacı parçası, kavram, bir düğüm ile tek bir kök düğümde başka bir şey kümesi gibi davranır. Ancak, rest döndürülen düğümlerinin alt düğümleri uygulanır. Program aracılığıyla alt düğümleri görmek için sonuç ağacı parçası sonucu ağacı kullanarak kopyalama `<xsl:copy-of>` öğesi. Kopyalama, gerçekleştirildiğinde, tüm alt düğümleri de sırayla sonucu ağacına kopyalanır. Kadar bir `copy` veya `copy-of` olan kullanıldığında, bir sonuç ağacı parçası sonucu ağacı veya dönüştürme çıktısını bir parçası değil.

Sonuç ağacı parçası döndürülen düğümler yineleme yapmak için bir <xref:System.Xml.XPath.XPathNavigator> kullanılır. Aşağıdaki kod örneği, bir parametre ile işlevini çağırarak bir stil sayfası içinde bir sonuç ağacı parçası oluşturma işlemi gösterilmektedir `fragment`, XML içeriyor.

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

Zengin metin biçimi (RTF) olan bir değişken gösteren başka bir örneği aşağıdadır ve bu nedenle, bir düğüme dönüştürülmedi sonuç ağacı parçası, bir tür ayarlayın. Bunun yerine, bir komut dosyası işleve geçirilir ve <xref:System.Xml.XPath.XPathNavigator> düğümleri üzerinde gezinmek için kullanılır.

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

Bu stil sayfası ile herhangi bir XML dönüştürme sonucu aşağıdaki çıktıda gösterilir.

## <a name="output"></a>Çıkış

```xml
<first_book xmlns:user="urn:books">Book1</first_book>
```

Yukarıda belirtildiği gibi `node-set` işlevi bir sonuç ağacı parçası düğümünü kümeyi dönüştürmek sağlar. Sonuç olarak oluşan düğüm her zaman kök düğüm ağacı tek bir düğüm içerir. Bir düğüme bir sonuç ağacı parçası dönüştürürseniz ayarlayın, sonra da bunu bir normal bir düğüm kümesi kullanılır, her yerde kullanabilirsiniz gibi için-her bir deyim olduğu gibi veya değeri bir `select` özniteliği. Aşağıdaki kod satırlarını ayarlayın ve bir düğüm kümesi kullanılan bir düğüme dönüştürülen parça göster:

`<xsl:for-each select="msxsl:node-set($node-fragment)">`

`<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`

Bir parça için bir düğüm kümesi dönüştürülür, artık kullanmadığınız <xref:System.Xml.XPath.XPathNavigator> üzerine gidin. Bir düğüm kümesi için kullandığınız <xref:System.Xml.XPath.XPathNodeIterator> yerine.

Aşağıdaki örnekte, `$var` stil sayfası düğümü ağacında bir değişkendir. For-each ifadesinin Sunucusu'yla birlikte `node-set` işlevi, bir düğüm kümesi olarak bu ağaç gezinilen izin verir.

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

RTF biçiminde olan bir değişkeni başka bir örnek aşağıda verilmiştir ve bu nedenle türü sonuç ağacı parçası, düğüm kümesi bir betik işlevi XPathNodeIterator iletilmeden önce dönüştürülür.

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

Bu stil sayfası ile XML dönüştürme sonucunu verilmiştir:

```xml
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XPath.XPathNodeIterator>  
- <xref:System.Xml.XPath.XPathNodeIterator>  
- [XslTransform Sınıfı ile XSLT Dönüşümleri](xslt-transformations-with-the-xsltransform-class.md)  
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](xsltransform-class-implements-the-xslt-processor.md)  
