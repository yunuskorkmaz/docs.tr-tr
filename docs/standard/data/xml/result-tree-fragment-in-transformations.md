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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 04e23f39f522fca7f69aa86be7036320a5698a60
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="result-tree-fragment-in-transformations"></a><span data-ttu-id="a13d6-102">Sonuç ağaç parçadaki dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="a13d6-102">Result Tree Fragment in Transformations</span></span>
> [!NOTE]
>  <span data-ttu-id="a13d6-103"><xref:System.Xml.Xsl.XslTransform> Sınıftır'te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a13d6-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="a13d6-104">Genişletilebilir Stil sayfası dili kullanarak Dönüşümleri (XSLT) dönüştürmeleri için gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a13d6-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="a13d6-105">Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="a13d6-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="a13d6-106">Sonuç ağaç parçaları, sonuç ağaç parçaları olarak da bilinen, özel türde bir düğüm kümesi'den fazla bir şey var.</span><span class="sxs-lookup"><span data-stu-id="a13d6-106">Result tree fragments, also known as result tree fragments, are nothing more than a special type of node set.</span></span> <span data-ttu-id="a13d6-107">Bir düğüm kümesi üzerinde gerçekleştirilebilir onlar üzerinde herhangi bir işlev gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a13d6-107">You can perform any function on them that can be performed on a node set.</span></span> <span data-ttu-id="a13d6-108">Veya, bir sonuç ağacı parçası kullanılarak ayarlanan bir düğüme dönüştürebilirsiniz `node-set()` işlev ve daha sonra herhangi bir yerleştirin bir düğüm kümesi kullanılabilir kullanın.</span><span class="sxs-lookup"><span data-stu-id="a13d6-108">Or, you can also convert a result tree fragment to a node set using the `node-set()` function and subsequently use it any place that a node set can be used.</span></span>  
  
 <span data-ttu-id="a13d6-109">Sonuç ağacı parçası kullanılarak sonucu olarak oluşturulan bir `<xsl:variable>` veya `<xsl:param>` bir stil sayfası belirli bir şekilde öğe.</span><span class="sxs-lookup"><span data-stu-id="a13d6-109">A result tree fragment is created as a result of using an `<xsl:variable>` or `<xsl:param>` element in a specific manner in a style sheet.</span></span> <span data-ttu-id="a13d6-110">Sözdizimi `variable` ve `parameter` öğeleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="a13d6-110">The syntax for the `variable` and `parameter` elements is as follows:</span></span>  
  
```xml  
<xsl:param name=Qname select= XPath Expression >  
    template body  
</xsl:param>  
  
<xsl:variable name=Qname select=XPath Expression >  
    template body  
</xsl:variable>  
```  
  
 <span data-ttu-id="a13d6-111">İçin `parameter` öğesi, değerin tam adı atandığı (`Qname`) çeşitli şekillerde.</span><span class="sxs-lookup"><span data-stu-id="a13d6-111">For the `parameter` element, the value is assigned to the qualified name (`Qname`) in several ways.</span></span> <span data-ttu-id="a13d6-112">XML Path dili (XPath) ifadesinden içerik döndürerek parametresi için varsayılan değer atayabilirsiniz `select` özniteliği veya göre şablon gövdesi içeriğini atama.</span><span class="sxs-lookup"><span data-stu-id="a13d6-112">You can assign a default value to the parameter by returning content from the XML Path Language (XPath) expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>  
  
 <span data-ttu-id="a13d6-113">İçin `variable` öğesi, değer de atanmış çeşitli yollarla.</span><span class="sxs-lookup"><span data-stu-id="a13d6-113">For the `variable` element, the value is also assigned in several ways.</span></span> <span data-ttu-id="a13d6-114">XPath ifadesinden içerik döndürerek atayabilirsiniz `select` özniteliği veya göre şablon gövdesi içeriğini atama.</span><span class="sxs-lookup"><span data-stu-id="a13d6-114">You can assign it by returning content from the XPath expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>  
  
 <span data-ttu-id="a13d6-115">Her ikisi için de `parameter` ve `variable` öğeleri, bir değer XPath ifadesi tarafından atanmışsa sonra dört temel XPath türlerinden birini döndürülecek: Boolean, dize, sayı veya düğüm kümesi.</span><span class="sxs-lookup"><span data-stu-id="a13d6-115">For both the `parameter` and `variable` elements, if a value is assigned by the XPath expression, then one of the four basic XPath types will be returned: Boolean, string, number, or node set.</span></span> <span data-ttu-id="a13d6-116">Değer boş şablon gövde kullanarak verildiğinde bir XPath olmayan veri türü sonra döndürülür ve sonuç ağacı parçası olur.</span><span class="sxs-lookup"><span data-stu-id="a13d6-116">When the value is given by using a non-empty template body, then a non-XPath data type is returned, and that will be a result tree fragment.</span></span>  
  
 <span data-ttu-id="a13d6-117">Bir değişken sonuç ağacı parçası dört temel XPath veri türlerinden birini yerine bağlandığında, bu yalnızca bir kez gösterilecektir bir XPath sorgusu dört XPath nesne türlerinden birini olmayan bir tür döndürür.</span><span class="sxs-lookup"><span data-stu-id="a13d6-117">When a variable is bound to a result tree fragment instead of one of the four basic XPath data types, this is the only time that an XPath query returns a type that is not one of the four XPath object types.</span></span> <span data-ttu-id="a13d6-118">World Wide Web Konsorsiyumu (W3C) belirtimi www.w3.org/XSLT, Bölüm 11.1 sonuç ağaç parçaları Bölüm 11.6 geçirme parametreleri şablonlarına üzerinden, sonuç ağaç parçaları ve davranışları ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="a13d6-118">Result tree fragments and their behavior are discussed in the World Wide Web Consortium (W3C) specification at www.w3.org/XSLT, section 11.1 Result Tree Fragments through section 11.6 Passing Parameters to Templates.</span></span> <span data-ttu-id="a13d6-119">Ayrıca, şablonları XSLT ad alanından dönün veya ağaç parçaları sonuç oluşturduğunuz öğeler nasıl içerebilir 1 giriş anlatılmaktadır bölümü.</span><span class="sxs-lookup"><span data-stu-id="a13d6-119">Also, section 1 Introduction discusses how templates can contain elements from the XSLT namespace that return or create result tree fragments.</span></span>  
  
 <span data-ttu-id="a13d6-120">Bir sonuç ağaç parçadaki kavram, bir düğüm ile tek bir kök düğümde fazlasını kümesi gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="a13d6-120">A result tree fragment, in concept, behaves like a node set with nothing more than a single root node.</span></span> <span data-ttu-id="a13d6-121">Ancak, döndürülen düğümleri geri kalanı, alt düğümleri değildir.</span><span class="sxs-lookup"><span data-stu-id="a13d6-121">However, the rest of the nodes returned are child nodes.</span></span> <span data-ttu-id="a13d6-122">Program aracılığıyla alt düğümleri görmek için sonuç kullanarak ağaç sonuç ağacı parçası kopyalama `<xsl:copy-of>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a13d6-122">To programmatically see the child nodes, copy the result tree fragment to the result tree using the `<xsl:copy-of>` element.</span></span> <span data-ttu-id="a13d6-123">Kopyalama, gerçekleştirildiğinde, tüm alt düğümler de sırayla sonuç ağacına kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="a13d6-123">When the copy-of is performed, all the child nodes are also copied to the result tree in sequence.</span></span> <span data-ttu-id="a13d6-124">Kadar bir `copy` veya `copy-of` olan kullanıldığında, sonuç ağacı parçası sonuç ağaç veya dönüşümün çıktısını parçası değil.</span><span class="sxs-lookup"><span data-stu-id="a13d6-124">Until a `copy` or `copy-of` is used, a result tree fragment is not part of the result tree or the output from the transformation.</span></span>  
  
 <span data-ttu-id="a13d6-125">Sonuç ağacı parçası, döndürülen düğümleri üzerinde döngüyle gezinmek üzere bir <xref:System.Xml.XPath.XPathNavigator> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a13d6-125">To iterate over the returned nodes of a result tree fragment, an <xref:System.Xml.XPath.XPathNavigator> is used.</span></span> <span data-ttu-id="a13d6-126">Aşağıdaki kod örneği bir parametresiyle işlevini çağırarak bir stil sayfası içinden sonuç ağacı parçası oluşturulacağını gösterir `fragment`, XML içeriyor.</span><span class="sxs-lookup"><span data-stu-id="a13d6-126">The following code sample shows how to create a result tree fragment within a style sheet by calling the function with a parameter `fragment`, which contains XML.</span></span>  
  
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
  
 <span data-ttu-id="a13d6-127">Zengin metin biçimi (RTF) olan bir değişken gösteren başka bir örnek şudur ve bu nedenle, bir düğüme dönüştürülmedi sonuç ağacı parçası, türünü ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a13d6-127">Here is another sample showing a variable, which is in Rich Text Format (RTF), and hence, a type of result tree fragment, that is not converted to a node set.</span></span> <span data-ttu-id="a13d6-128">Bunun yerine, bir komut dosyası işlevine geçirilen ve <xref:System.Xml.XPath.XPathNavigator> düğümleri üzerinde gitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a13d6-128">Instead, it is passed to a script function, and the <xref:System.Xml.XPath.XPathNavigator> is used to navigate over the nodes.</span></span>  
  
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
  
 <span data-ttu-id="a13d6-129">Bu stil sayfası ile herhangi bir XML dönüştürme sonuç aşağıdaki çıktı gösterilir.</span><span class="sxs-lookup"><span data-stu-id="a13d6-129">The result of transforming any XML with this style sheet is shown in the following output.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a13d6-130">Çıkış</span><span class="sxs-lookup"><span data-stu-id="a13d6-130">Output</span></span>  
  
```xml  
<first_book xmlns:user="urn:books">Book1</first_book>  
```  
  
 <span data-ttu-id="a13d6-131">Yukarıda belirtildiği gibi `node-set` işlevi bir düğüm kümesine sonuç ağacı parçası dönüştürmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a13d6-131">As stated above, the `node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="a13d6-132">Sonuçta elde edilen düğümü, her zaman ağacı kök düğümü tek bir düğüm içerir.</span><span class="sxs-lookup"><span data-stu-id="a13d6-132">The resulting node always contains a single node that is the root node of the tree.</span></span> <span data-ttu-id="a13d6-133">Bir düğüme sonuç ağacı parçası dönüştürürseniz ayarlanırsa, her yerden normal düğüm kümesi kullanılır, kullanabileceğiniz sonra gibi için-each deyimi olduğu gibi veya değeri bir `select` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a13d6-133">If you convert a result tree fragment to a node set, then you can use it anywhere a regular node set is used, such as in a for-each statement or in the value of a `select` attribute.</span></span> <span data-ttu-id="a13d6-134">Aşağıdaki kod satırlarını ayarlayın ve bir düğüm kümesi kullanılan bir düğüme dönüştürülen parça göster:</span><span class="sxs-lookup"><span data-stu-id="a13d6-134">The following lines of code show the fragment being converted to a node set and used as a node set:</span></span>  
  
 `<xsl:for-each select="msxsl:node-set($node-fragment)">`  
  
 `<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`  
  
 <span data-ttu-id="a13d6-135">Bir parça düğüm kümesi dönüştürüldüğünde, artık kullanmadığınız <xref:System.Xml.XPath.XPathNavigator> üzerine gidin.</span><span class="sxs-lookup"><span data-stu-id="a13d6-135">When a fragment is converted to a node set, you no longer use the <xref:System.Xml.XPath.XPathNavigator> to navigate over it.</span></span> <span data-ttu-id="a13d6-136">Bir düğüm kümesi için kullandığınız <xref:System.Xml.XPath.XPathNodeIterator> yerine.</span><span class="sxs-lookup"><span data-stu-id="a13d6-136">For a node set, you use the <xref:System.Xml.XPath.XPathNodeIterator> instead.</span></span>  
  
 <span data-ttu-id="a13d6-137">Aşağıdaki örnekte, `$var` stil sayfası düğümü ağaçtaki bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="a13d6-137">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="a13d6-138">İçin-each deyimi birlikte `node-set` işlev, bu ağaç düğümü kümesi olarak üzerinden yineleme olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a13d6-138">The for-each statement, combined with the `node-set` function, allows the user to iterate over this tree as a node set.</span></span>  
  
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
  
 <span data-ttu-id="a13d6-139">RTF biçiminde olan bir değişken başka bir örneği burada verilmiştir ve bu nedenle türü sonucu ağaç parçasında, düğüm, bir komut dosyası işlevi XPathNodeIterator olarak iletilmeden önce kümesi dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="a13d6-139">Here is another example of a variable that is in RTF, and hence of type result tree fragment, that is converted to a node set before being passed to a script function as XPathNodeIterator.</span></span>  
  
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
  
 <span data-ttu-id="a13d6-140">Bu stil sayfası ile XML dönüştürme sonucu verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a13d6-140">The following is the result of transforming XML with this style sheet:</span></span>  
  
```xml  
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a13d6-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a13d6-141">See Also</span></span>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 [<span data-ttu-id="a13d6-142">XslTransform Sınıfı ile XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="a13d6-142">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="a13d6-143">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="a13d6-143">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
