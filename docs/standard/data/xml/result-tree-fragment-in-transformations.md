---
title: "Sonuç ağaç parçadaki dönüşümleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1a4b585fe34a841061f8e5bab7cb18a58f53cfe8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="result-tree-fragment-in-transformations"></a>Sonuç ağaç parçadaki dönüşümleri
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır'te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil sayfası dili kullanarak Dönüşümleri (XSLT) dönüştürmeleri için gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 Sonuç ağaç parçaları, sonuç ağaç parçaları olarak da bilinen, özel türde bir düğüm kümesi'den fazla bir şey var. Bir düğüm kümesi üzerinde gerçekleştirilebilir onlar üzerinde herhangi bir işlev gerçekleştirebilirsiniz. Veya, bir sonuç ağacı parçası kullanılarak ayarlanan bir düğüme dönüştürebilirsiniz `node-set()` işlev ve daha sonra herhangi bir yerleştirin bir düğüm kümesi kullanılabilir kullanın.  
  
 Sonuç ağacı parçası kullanılarak sonucu olarak oluşturulan bir `<xsl:variable>` veya `<xsl:param>` bir stil sayfası belirli bir şekilde öğe. Sözdizimi `variable` ve `parameter` öğeleri aşağıdaki gibidir:  
  
```xml  
<xsl:param name=Qname select= XPath Expression >  
    template body  
</xsl:param>  
  
<xsl:variable name=Qname select=XPath Expression >  
    template body  
</xsl:variable>  
```  
  
 İçin `parameter` öğesi, değerin tam adı atandığı (`Qname`) çeşitli şekillerde. XML Path dili (XPath) ifadesinden içerik döndürerek parametresi için varsayılan değer atayabilirsiniz `select` özniteliği veya göre şablon gövdesi içeriğini atama.  
  
 İçin `variable` öğesi, değer de atanmış çeşitli yollarla. XPath ifadesinden içerik döndürerek atayabilirsiniz `select` özniteliği veya göre şablon gövdesi içeriğini atama.  
  
 Her ikisi için de `parameter` ve `variable` öğeleri, bir değer XPath ifadesi tarafından atanmışsa sonra dört temel XPath türlerinden birini döndürülecek: Boolean, dize, sayı veya düğüm kümesi. Değer boş şablon gövde kullanarak verildiğinde bir XPath olmayan veri türü sonra döndürülür ve sonuç ağacı parçası olur.  
  
 Bir değişken sonuç ağacı parçası dört temel XPath veri türlerinden birini yerine bağlandığında, bu yalnızca bir kez gösterilecektir bir XPath sorgusu dört XPath nesne türlerinden birini olmayan bir tür döndürür. World Wide Web Konsorsiyumu (W3C) belirtimi www.w3.org/XSLT, Bölüm 11.1 sonuç ağaç parçaları Bölüm 11.6 geçirme parametreleri şablonlarına üzerinden, sonuç ağaç parçaları ve davranışları ele alınmıştır. Ayrıca, şablonları XSLT ad alanından dönün veya ağaç parçaları sonuç oluşturduğunuz öğeler nasıl içerebilir 1 giriş anlatılmaktadır bölümü.  
  
 Bir sonuç ağaç parçadaki kavram, bir düğüm ile tek bir kök düğümde fazlasını kümesi gibi davranır. Ancak, döndürülen düğümleri geri kalanı, alt düğümleri değildir. Program aracılığıyla alt düğümleri görmek için sonuç kullanarak ağaç sonuç ağacı parçası kopyalama `<xsl:copy-of>` öğesi. Kopyalama, gerçekleştirildiğinde, tüm alt düğümler de sırayla sonuç ağacına kopyalanır. Kadar bir `copy` veya `copy-of` olan kullanıldığında, sonuç ağacı parçası sonuç ağaç veya dönüşümün çıktısını parçası değil.  
  
 Sonuç ağacı parçası, döndürülen düğümleri üzerinde döngüyle gezinmek üzere bir <xref:System.Xml.XPath.XPathNavigator> kullanılır. Aşağıdaki kod örneği bir parametresiyle işlevini çağırarak bir stil sayfası içinden sonuç ağacı parçası oluşturulacağını gösterir `fragment`, XML içeriyor.  
  
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
  
 Zengin metin biçimi (RTF) olan bir değişken gösteren başka bir örnek şudur ve bu nedenle, bir düğüme dönüştürülmedi sonuç ağacı parçası, türünü ayarlayın. Bunun yerine, bir komut dosyası işlevine geçirilen ve <xref:System.Xml.XPath.XPathNavigator> düğümleri üzerinde gitmek için kullanılır.  
  
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
  
 Bu stil sayfası ile herhangi bir XML dönüştürme sonuç aşağıdaki çıktı gösterilir.  
  
## <a name="output"></a>Çıkış  
  
```xml  
<first_book xmlns:user="urn:books">Book1</first_book>  
```  
  
 Yukarıda belirtildiği gibi `node-set` işlevi bir düğüm kümesine sonuç ağacı parçası dönüştürmenize olanak sağlar. Sonuçta elde edilen düğümü, her zaman ağacı kök düğümü tek bir düğüm içerir. Bir düğüme sonuç ağacı parçası dönüştürürseniz ayarlanırsa, her yerden normal düğüm kümesi kullanılır, kullanabileceğiniz sonra gibi için-each deyimi olduğu gibi veya değeri bir `select` özniteliği. Aşağıdaki kod satırlarını ayarlayın ve bir düğüm kümesi kullanılan bir düğüme dönüştürülen parça göster:  
  
 `<xsl:for-each select="msxsl:node-set($node-fragment)">`  
  
 `<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`  
  
 Bir parça düğüm kümesi dönüştürüldüğünde, artık kullanmadığınız <xref:System.Xml.XPath.XPathNavigator> üzerine gidin. Bir düğüm kümesi için kullandığınız <xref:System.Xml.XPath.XPathNodeIterator> yerine.  
  
 Aşağıdaki örnekte, `$var` stil sayfası düğümü ağaçtaki bir değişkendir. İçin-each deyimi birlikte `node-set` işlev, bu ağaç düğümü kümesi olarak üzerinden yineleme olanak tanır.  
  
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
  
 RTF biçiminde olan bir değişken başka bir örneği burada verilmiştir ve bu nedenle türü sonucu ağaç parçasında, düğüm, bir komut dosyası işlevi XPathNodeIterator olarak iletilmeden önce kümesi dönüştürülür.  
  
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
  
 Bu stil sayfası ile XML dönüştürme sonucu verilmiştir:  
  
```xml  
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 [Çok sınıfı ile XSLT dönüştürmeler](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [XSLT işlemci çok sınıfı uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
