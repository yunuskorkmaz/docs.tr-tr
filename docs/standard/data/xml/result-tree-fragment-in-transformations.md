---
title: Dönüşümlerdeki sonuç ağacı parçası
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2c64baef3037cdb7b45ede3febacdbc1e76304c0
ms.sourcegitcommit: e8dc507cfdaad504fc9d4c83d28d24569dcef91c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "33574705"
---
# <a name="result-tree-fragment-in-transformations"></a><span data-ttu-id="eb863-102">Dönüşümlerdeki sonuç ağacı parçası</span><span class="sxs-lookup"><span data-stu-id="eb863-102">Result Tree Fragment in Transformations</span></span>
> [!NOTE]
>  <span data-ttu-id="eb863-103"><xref:System.Xml.Xsl.XslTransform> Sınıftır eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb863-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="eb863-104">Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="eb863-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="eb863-105">Bkz: [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="eb863-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="eb863-106">Sonucu ağacı parçalarını sonucu ağacı parçalarını olarak da bilinir, düğüm kümesi özel bir tür başka bir şey var.</span><span class="sxs-lookup"><span data-stu-id="eb863-106">Result tree fragments, also known as result tree fragments, are nothing more than a special type of node set.</span></span> <span data-ttu-id="eb863-107">Bir düğüm kümesi üzerinde gerçekleştirilebilen bunlar üzerinde herhangi bir işlev gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb863-107">You can perform any function on them that can be performed on a node set.</span></span> <span data-ttu-id="eb863-108">Ya da sonuç ağacı parçası kullanılarak ayarlanan bir düğüme dönüştürebilirsiniz `node-set()` işlev ve sonradan herhangi yerleştirileceği bir düğüm kümesi kullanılabilir kullanın.</span><span class="sxs-lookup"><span data-stu-id="eb863-108">Or, you can also convert a result tree fragment to a node set using the `node-set()` function and subsequently use it any place that a node set can be used.</span></span>  
  
 <span data-ttu-id="eb863-109">Sonuç ağacı parçası kullanarak sonucu olarak oluşturulan bir `<xsl:variable>` veya `<xsl:param>` belirli bir şekilde bir stil sayfası öğesinde.</span><span class="sxs-lookup"><span data-stu-id="eb863-109">A result tree fragment is created as a result of using an `<xsl:variable>` or `<xsl:param>` element in a specific manner in a style sheet.</span></span> <span data-ttu-id="eb863-110">Sözdizimi `variable` ve `parameter` öğeleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="eb863-110">The syntax for the `variable` and `parameter` elements is as follows:</span></span>  
  
```xml  
<xsl:param name=Qname select= XPath Expression >  
    template body  
</xsl:param>  
  
<xsl:variable name=Qname select=XPath Expression >  
    template body  
</xsl:variable>  
```  
  
 <span data-ttu-id="eb863-111">İçin `parameter` öğesi, değerin tam adı için atanır (`Qname`) çeşitli şekillerde.</span><span class="sxs-lookup"><span data-stu-id="eb863-111">For the `parameter` element, the value is assigned to the qualified name (`Qname`) in several ways.</span></span> <span data-ttu-id="eb863-112">XML Path Language (XPath) ifade gelen içerik döndürerek parametre bir varsayılan değer atayabilirsiniz `select` özniteliği veya şablon gövdesi içeriğini göre atama.</span><span class="sxs-lookup"><span data-stu-id="eb863-112">You can assign a default value to the parameter by returning content from the XML Path Language (XPath) expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>  
  
 <span data-ttu-id="eb863-113">İçin `variable` öğesi değeri de atandığı çeşitli yollarla.</span><span class="sxs-lookup"><span data-stu-id="eb863-113">For the `variable` element, the value is also assigned in several ways.</span></span> <span data-ttu-id="eb863-114">XPath ifadesinden içerik döndürerek atayabilirsiniz `select` özniteliği veya şablon gövdesi içeriğini göre atama.</span><span class="sxs-lookup"><span data-stu-id="eb863-114">You can assign it by returning content from the XPath expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>  
  
 <span data-ttu-id="eb863-115">Her ikisi için de `parameter` ve `variable` öğeleri XPath ifadesi tarafından atanmış bir değer ise ardından dört temel XPath türlerinden biri döndürülür: Boolean, dize, sayı veya düğüm kümesi.</span><span class="sxs-lookup"><span data-stu-id="eb863-115">For both the `parameter` and `variable` elements, if a value is assigned by the XPath expression, then one of the four basic XPath types will be returned: Boolean, string, number, or node set.</span></span> <span data-ttu-id="eb863-116">Boş şablon gövdesi kullanarak değeri belirtildiğinde, ardından döndürülen bir XPath olmayan veri türü ve bir sonuç ağacı parçası olacak.</span><span class="sxs-lookup"><span data-stu-id="eb863-116">When the value is given by using a non-empty template body, then a non-XPath data type is returned, and that will be a result tree fragment.</span></span>  
  
 <span data-ttu-id="eb863-117">Bir değişken dört temel XPath veri türlerinden biri yerine bir sonuç ağacı parçası bağlandığında, bu yalnızca bir kez olan bir XPath sorgusu dört XPath nesne türlerinden biri değil bir tür döndürür.</span><span class="sxs-lookup"><span data-stu-id="eb863-117">When a variable is bound to a result tree fragment instead of one of the four basic XPath data types, this is the only time that an XPath query returns a type that is not one of the four XPath object types.</span></span> <span data-ttu-id="eb863-118">World Wide Web Consortium (W3C) belirtimi www.w3.org/XSLT, Bölüm 11.1 sonucu ağacı parçalarını Bölüm 11.6 geçirme parametreleri şablonları aracılığıyla, sonucu ağacı parçalarını ve davranışları ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="eb863-118">Result tree fragments and their behavior are discussed in the World Wide Web Consortium (W3C) specification at www.w3.org/XSLT, section 11.1 Result Tree Fragments through section 11.6 Passing Parameters to Templates.</span></span> <span data-ttu-id="eb863-119">Ayrıca, 1 giriş nasıl şablonları döndürür ya da sonuç ağacı parçalarını oluşturan XSLT ad alanından öğeler içerebilir ele alınmaktadır. bölümü.</span><span class="sxs-lookup"><span data-stu-id="eb863-119">Also, section 1 Introduction discusses how templates can contain elements from the XSLT namespace that return or create result tree fragments.</span></span>  
  
 <span data-ttu-id="eb863-120">Bir sonuç ağacı parçası, kavram, bir düğüm ile tek bir kök düğümde başka bir şey kümesi gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="eb863-120">A result tree fragment, in concept, behaves like a node set with nothing more than a single root node.</span></span> <span data-ttu-id="eb863-121">Ancak, rest döndürülen düğümlerinin alt düğümleri uygulanır.</span><span class="sxs-lookup"><span data-stu-id="eb863-121">However, the rest of the nodes returned are child nodes.</span></span> <span data-ttu-id="eb863-122">Program aracılığıyla alt düğümleri görmek için sonuç ağacı parçası sonucu ağacı kullanarak kopyalama `<xsl:copy-of>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="eb863-122">To programmatically see the child nodes, copy the result tree fragment to the result tree using the `<xsl:copy-of>` element.</span></span> <span data-ttu-id="eb863-123">Kopyalama, gerçekleştirildiğinde, tüm alt düğümleri de sırayla sonucu ağacına kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="eb863-123">When the copy-of is performed, all the child nodes are also copied to the result tree in sequence.</span></span> <span data-ttu-id="eb863-124">Kadar bir `copy` veya `copy-of` olan kullanıldığında, bir sonuç ağacı parçası sonucu ağacı veya dönüştürme çıktısını bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="eb863-124">Until a `copy` or `copy-of` is used, a result tree fragment is not part of the result tree or the output from the transformation.</span></span>  
  
 <span data-ttu-id="eb863-125">Sonuç ağacı parçası döndürülen düğümler yineleme yapmak için bir <xref:System.Xml.XPath.XPathNavigator> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb863-125">To iterate over the returned nodes of a result tree fragment, an <xref:System.Xml.XPath.XPathNavigator> is used.</span></span> <span data-ttu-id="eb863-126">Aşağıdaki kod örneği, bir parametre ile işlevini çağırarak bir stil sayfası içinde bir sonuç ağacı parçası oluşturma işlemi gösterilmektedir `fragment`, XML içeriyor.</span><span class="sxs-lookup"><span data-stu-id="eb863-126">The following code sample shows how to create a result tree fragment within a style sheet by calling the function with a parameter `fragment`, which contains XML.</span></span>  
  
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
  
 <span data-ttu-id="eb863-127">Zengin metin biçimi (RTF) olan bir değişken gösteren başka bir örneği aşağıdadır ve bu nedenle, bir düğüme dönüştürülmedi sonuç ağacı parçası, bir tür ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eb863-127">Here is another sample showing a variable, which is in Rich Text Format (RTF), and hence, a type of result tree fragment, that is not converted to a node set.</span></span> <span data-ttu-id="eb863-128">Bunun yerine, bir komut dosyası işleve geçirilir ve <xref:System.Xml.XPath.XPathNavigator> düğümleri üzerinde gezinmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb863-128">Instead, it is passed to a script function, and the <xref:System.Xml.XPath.XPathNavigator> is used to navigate over the nodes.</span></span>  
  
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
  
 <span data-ttu-id="eb863-129">Bu stil sayfası ile herhangi bir XML dönüştürme sonucu aşağıdaki çıktıda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="eb863-129">The result of transforming any XML with this style sheet is shown in the following output.</span></span>  
  
## <a name="output"></a><span data-ttu-id="eb863-130">Çıkış</span><span class="sxs-lookup"><span data-stu-id="eb863-130">Output</span></span>  
  
```xml  
<first_book xmlns:user="urn:books">Book1</first_book>  
```  
  
 <span data-ttu-id="eb863-131">Yukarıda belirtildiği gibi `node-set` işlevi bir sonuç ağacı parçası düğümünü kümeyi dönüştürmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb863-131">As stated above, the `node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="eb863-132">Sonuç olarak oluşan düğüm her zaman kök düğüm ağacı tek bir düğüm içerir.</span><span class="sxs-lookup"><span data-stu-id="eb863-132">The resulting node always contains a single node that is the root node of the tree.</span></span> <span data-ttu-id="eb863-133">Bir düğüme bir sonuç ağacı parçası dönüştürürseniz ayarlayın, sonra da bunu bir normal bir düğüm kümesi kullanılır, her yerde kullanabilirsiniz gibi için-her bir deyim olduğu gibi veya değeri bir `select` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="eb863-133">If you convert a result tree fragment to a node set, then you can use it anywhere a regular node set is used, such as in a for-each statement or in the value of a `select` attribute.</span></span> <span data-ttu-id="eb863-134">Aşağıdaki kod satırlarını ayarlayın ve bir düğüm kümesi kullanılan bir düğüme dönüştürülen parça göster:</span><span class="sxs-lookup"><span data-stu-id="eb863-134">The following lines of code show the fragment being converted to a node set and used as a node set:</span></span>  
  
 `<xsl:for-each select="msxsl:node-set($node-fragment)">`  
  
 `<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`  
  
 <span data-ttu-id="eb863-135">Bir parça için bir düğüm kümesi dönüştürülür, artık kullanmadığınız <xref:System.Xml.XPath.XPathNavigator> üzerine gidin.</span><span class="sxs-lookup"><span data-stu-id="eb863-135">When a fragment is converted to a node set, you no longer use the <xref:System.Xml.XPath.XPathNavigator> to navigate over it.</span></span> <span data-ttu-id="eb863-136">Bir düğüm kümesi için kullandığınız <xref:System.Xml.XPath.XPathNodeIterator> yerine.</span><span class="sxs-lookup"><span data-stu-id="eb863-136">For a node set, you use the <xref:System.Xml.XPath.XPathNodeIterator> instead.</span></span>  
  
 <span data-ttu-id="eb863-137">Aşağıdaki örnekte, `$var` stil sayfası düğümü ağacında bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="eb863-137">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="eb863-138">For-each ifadesinin Sunucusu'yla birlikte `node-set` işlevi, bir düğüm kümesi olarak bu ağaç gezinilen izin verir.</span><span class="sxs-lookup"><span data-stu-id="eb863-138">The for-each statement, combined with the `node-set` function, allows the user to iterate over this tree as a node set.</span></span>  
  
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
  
 <span data-ttu-id="eb863-139">RTF biçiminde olan bir değişkeni başka bir örnek aşağıda verilmiştir ve bu nedenle türü sonuç ağacı parçası, düğüm kümesi bir betik işlevi XPathNodeIterator iletilmeden önce dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="eb863-139">Here is another example of a variable that is in RTF, and hence of type result tree fragment, that is converted to a node set before being passed to a script function as XPathNodeIterator.</span></span>  
  
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
  
 <span data-ttu-id="eb863-140">Bu stil sayfası ile XML dönüştürme sonucunu verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="eb863-140">The following is the result of transforming XML with this style sheet:</span></span>  
  
```xml  
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb863-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eb863-141">See Also</span></span>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 [<span data-ttu-id="eb863-142">XslTransform Sınıfı ile XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="eb863-142">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="eb863-143">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="eb863-143">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
