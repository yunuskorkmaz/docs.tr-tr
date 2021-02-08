---
description: 'Daha fazla bilgi edinin: dönüşümlerdeki sonuç ağacı parçası'
title: Dönüşümlerdeki Sonuç Ağacı Parçası
ms.date: 03/30/2017
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
ms.openlocfilehash: 6f3d0b561fcca57b81d154cfc21dcee05e866230
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783046"
---
# <a name="result-tree-fragment-in-transformations"></a><span data-ttu-id="4f679-103">Dönüşümlerdeki Sonuç Ağacı Parçası</span><span class="sxs-lookup"><span data-stu-id="4f679-103">Result Tree Fragment in Transformations</span></span>

> [!NOTE]
> <span data-ttu-id="4f679-104"><xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="4f679-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="4f679-105">Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="4f679-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="4f679-106">Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="4f679-106">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>

 <span data-ttu-id="4f679-107">Sonuç ağacı parçaları olarak da bilinen sonuç ağacı parçaları, özel bir düğüm kümesi türünden başka hiçbir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="4f679-107">Result tree fragments, also known as result tree fragments, are nothing more than a special type of node set.</span></span> <span data-ttu-id="4f679-108">Bir düğüm kümesinde gerçekleştirilebilecek her türlü işlevi gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f679-108">You can perform any function on them that can be performed on a node set.</span></span> <span data-ttu-id="4f679-109">Ayrıca, işlevi kullanarak bir sonuç ağacı parçasını bir düğüm kümesine dönüştürebilir `node-set()` ve ardından bunu bir düğüm kümesinin kullanılabileceği herhangi bir yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f679-109">Or, you can also convert a result tree fragment to a node set using the `node-set()` function and subsequently use it any place that a node set can be used.</span></span>

 <span data-ttu-id="4f679-110">Bir sonuç ağacı parçası, bir `<xsl:variable>` veya `<xsl:param>` öğesini bir stil sayfasında belirli bir biçimde kullanmanın sonucu olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4f679-110">A result tree fragment is created as a result of using an `<xsl:variable>` or `<xsl:param>` element in a specific manner in a style sheet.</span></span> <span data-ttu-id="4f679-111">Ve öğeleri için sözdizimi `variable` `parameter` aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="4f679-111">The syntax for the `variable` and `parameter` elements is as follows:</span></span>

```xml
<xsl:param name=Qname select= XPath Expression >
    template body
</xsl:param>

<xsl:variable name=Qname select=XPath Expression >
    template body
</xsl:variable>
```

<span data-ttu-id="4f679-112">Öğesi için `parameter` , değer nitelenmiş ada ( `Qname` ) birkaç şekilde atanır.</span><span class="sxs-lookup"><span data-stu-id="4f679-112">For the `parameter` element, the value is assigned to the qualified name (`Qname`) in several ways.</span></span> <span data-ttu-id="4f679-113">Öznitelik içindeki XML Path Language (XPath) ifadesinden içerik döndürerek `select` veya şablon gövdesinin içeriğini atayarak parametreye varsayılan bir değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f679-113">You can assign a default value to the parameter by returning content from the XML Path Language (XPath) expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>

<span data-ttu-id="4f679-114">Öğesi için `variable` , değer de çeşitli yollarla atanır.</span><span class="sxs-lookup"><span data-stu-id="4f679-114">For the `variable` element, the value is also assigned in several ways.</span></span> <span data-ttu-id="4f679-115">Özniteliği özniteliğinde XPath ifadesinden içerik döndürerek `select` veya şablon gövdesinin içeriğini atayarak atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f679-115">You can assign it by returning content from the XPath expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>

<span data-ttu-id="4f679-116">Hem hem de `parameter` `variable` öğeleri Için, XPath ifadesi tarafından bir değer atanırsa, dört temel XPath türünden biri döndürülür: Boolean, dize, sayı veya düğüm kümesi.</span><span class="sxs-lookup"><span data-stu-id="4f679-116">For both the `parameter` and `variable` elements, if a value is assigned by the XPath expression, then one of the four basic XPath types will be returned: Boolean, string, number, or node set.</span></span> <span data-ttu-id="4f679-117">Değer boş olmayan bir şablon gövdesi kullanılarak verildiğinde, bir XPath olmayan veri türü döndürülür ve sonuç ağacı parçası olur.</span><span class="sxs-lookup"><span data-stu-id="4f679-117">When the value is given by using a non-empty template body, then a non-XPath data type is returned, and that will be a result tree fragment.</span></span>

<span data-ttu-id="4f679-118">Bir değişken dört temel XPath veri türünden biri yerine bir sonuç ağacı parçasına bağlandığında, bu bir XPath sorgusunun dört XPath nesne türünden biri olmayan bir tür döndürdüğü tek zaman olur.</span><span class="sxs-lookup"><span data-stu-id="4f679-118">When a variable is bound to a result tree fragment instead of one of the four basic XPath data types, this is the only time that an XPath query returns a type that is not one of the four XPath object types.</span></span> <span data-ttu-id="4f679-119">Sonuç ağacı parçaları ve davranışları, [World Wide Web Konsorsiyumu (W3C) belirtiminde](https://www.w3.org/TR/xslt-10/), Bölüm 11,1 ' de, Bölüm ' deki [sonuç ağacı 11,6 parçalarında](https://www.w3.org/TR/xslt-10/#section-Result-Tree-Fragments) , [parametrelere parametreler geçirilerek](https://www.w3.org/TR/xslt-10/#section-Passing-Parameters-to-Templates)ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="4f679-119">Result tree fragments and their behavior are discussed in the [World Wide Web Consortium (W3C) specification](https://www.w3.org/TR/xslt-10/), [section 11.1 Result Tree Fragments](https://www.w3.org/TR/xslt-10/#section-Result-Tree-Fragments) through [section 11.6 Passing Parameters to Templates](https://www.w3.org/TR/xslt-10/#section-Passing-Parameters-to-Templates).</span></span> <span data-ttu-id="4f679-120">Ayrıca, [Bölüm 1 giriş](https://www.w3.org/TR/xslt-10/#section-Introduction) , şablonların, sonuç ağacı parçaları döndüren veya oluşturan XSLT ad alanından nasıl öğe içerebileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4f679-120">Also, [section 1 Introduction](https://www.w3.org/TR/xslt-10/#section-Introduction) discusses how templates can contain elements from the XSLT namespace that return or create result tree fragments.</span></span>

<span data-ttu-id="4f679-121">Kavramdaki bir sonuç ağacı parçası, tek bir kök düğümden daha fazla şey olmayan bir düğüm kümesi gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="4f679-121">A result tree fragment, in concept, behaves like a node set with nothing more than a single root node.</span></span> <span data-ttu-id="4f679-122">Ancak, döndürülen düğümlerin geri kalanı alt düğümlerdir.</span><span class="sxs-lookup"><span data-stu-id="4f679-122">However, the rest of the nodes returned are child nodes.</span></span> <span data-ttu-id="4f679-123">Alt düğümleri programlı bir şekilde görmek için, sonuç ağacı parçasını öğesini kullanarak sonuç ağacına kopyalayın `<xsl:copy-of>` .</span><span class="sxs-lookup"><span data-stu-id="4f679-123">To programmatically see the child nodes, copy the result tree fragment to the result tree using the `<xsl:copy-of>` element.</span></span> <span data-ttu-id="4f679-124">Kopya gerçekleştirildiğinde, tüm alt düğümler de sıradaki sonuç ağacına kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="4f679-124">When the copy-of is performed, all the child nodes are also copied to the result tree in sequence.</span></span> <span data-ttu-id="4f679-125">`copy`Veya `copy-of` kullanılana kadar, sonuç ağacı parçası sonuç ağacının bir parçası veya dönüşümden çıktı değildir.</span><span class="sxs-lookup"><span data-stu-id="4f679-125">Until a `copy` or `copy-of` is used, a result tree fragment is not part of the result tree or the output from the transformation.</span></span>

<span data-ttu-id="4f679-126">Sonuç ağacı parçasının döndürülen düğümlerini yinelemek için, <xref:System.Xml.XPath.XPathNavigator> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4f679-126">To iterate over the returned nodes of a result tree fragment, an <xref:System.Xml.XPath.XPathNavigator> is used.</span></span> <span data-ttu-id="4f679-127">Aşağıdaki kod örneği, XML içeren bir parametre ile işlevi çağırarak bir stil sayfası içinde bir sonuç ağacı parçasının nasıl oluşturulacağını gösterir `fragment` .</span><span class="sxs-lookup"><span data-stu-id="4f679-127">The following code sample shows how to create a result tree fragment within a style sheet by calling the function with a parameter `fragment`, which contains XML.</span></span>

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

<span data-ttu-id="4f679-128">Burada, zengin metin biçimi (RTF) ve bu nedenle bir düğüm kümesine Dönüştürülmeyen bir sonuç ağacı parçası olan bir değişken gösteren başka bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4f679-128">Here is another sample showing a variable, which is in Rich Text Format (RTF), and hence, a type of result tree fragment, that is not converted to a node set.</span></span> <span data-ttu-id="4f679-129">Bunun yerine, bir betik işlevine geçirilir ve <xref:System.Xml.XPath.XPathNavigator> düğümler üzerinde gezinmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4f679-129">Instead, it is passed to a script function, and the <xref:System.Xml.XPath.XPathNavigator> is used to navigate over the nodes.</span></span>

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

<span data-ttu-id="4f679-130">Bu stil sayfasıyla herhangi bir XML dönüştürmenin sonucu aşağıdaki çıktıda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4f679-130">The result of transforming any XML with this style sheet is shown in the following output.</span></span>

## <a name="output"></a><span data-ttu-id="4f679-131">Çıktı</span><span class="sxs-lookup"><span data-stu-id="4f679-131">Output</span></span>

```xml
<first_book xmlns:user="urn:books">Book1</first_book>
```

<span data-ttu-id="4f679-132">Yukarıda belirtildiği gibi, `node-set` işlevi bir sonuç ağacı parçasını bir düğüm kümesine dönüştürmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f679-132">As stated above, the `node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="4f679-133">Elde edilen düğüm, her zaman ağacın kök düğümü olan tek bir düğüm içerir.</span><span class="sxs-lookup"><span data-stu-id="4f679-133">The resulting node always contains a single node that is the root node of the tree.</span></span> <span data-ttu-id="4f679-134">Bir sonuç ağacı parçasını bir düğüm kümesine dönüştürürseniz, for-each ifadesinde veya bir öznitelik değerinde olduğu gibi normal bir düğüm kümesinin kullanıldığı her yerde kullanabilirsiniz `select` .</span><span class="sxs-lookup"><span data-stu-id="4f679-134">If you convert a result tree fragment to a node set, then you can use it anywhere a regular node set is used, such as in a for-each statement or in the value of a `select` attribute.</span></span> <span data-ttu-id="4f679-135">Aşağıdaki kod satırları bir düğüm kümesine dönüştürülmekte olan ve düğüm kümesi olarak kullanılan parçayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="4f679-135">The following lines of code show the fragment being converted to a node set and used as a node set:</span></span>

`<xsl:for-each select="msxsl:node-set($node-fragment)">`

`<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`

<span data-ttu-id="4f679-136">Bir parça bir düğüm kümesine dönüştürüldüğünde, <xref:System.Xml.XPath.XPathNavigator> üzerinde gezinmek için artık kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="4f679-136">When a fragment is converted to a node set, you no longer use the <xref:System.Xml.XPath.XPathNavigator> to navigate over it.</span></span> <span data-ttu-id="4f679-137">Bir düğüm kümesi için, <xref:System.Xml.XPath.XPathNodeIterator> bunun yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="4f679-137">For a node set, you use the <xref:System.Xml.XPath.XPathNodeIterator> instead.</span></span>

<span data-ttu-id="4f679-138">Aşağıdaki örnekte, `$var` stil sayfasındaki düğüm ağacı olan bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="4f679-138">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="4f679-139">İşleviyle birlikte, for-each deyimleri, `node-set` kullanıcının bu ağacı üzerinde bir düğüm kümesi olarak yinemasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4f679-139">The for-each statement, combined with the `node-set` function, allows the user to iterate over this tree as a node set.</span></span>

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

<span data-ttu-id="4f679-140">Burada, RTF 'deki bir değişkene ait başka bir örnek ve bu nedenle, bir komut dosyası işlevine XPathNodeIterator olarak geçirilmeden önce bir düğüm kümesine dönüştürülecek olan sonuç ağacı parçası türü bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="4f679-140">Here is another example of a variable that is in RTF, and hence of type result tree fragment, that is converted to a node set before being passed to a script function as XPathNodeIterator.</span></span>

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

<span data-ttu-id="4f679-141">XML 'nin bu stil sayfasıyla dönüştürülmesi sonucu aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4f679-141">The following is the result of transforming XML with this style sheet:</span></span>

```xml
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>
```

## <a name="see-also"></a><span data-ttu-id="4f679-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f679-142">See also</span></span>

- <xref:System.Xml.XPath.XPathNodeIterator>
- [<span data-ttu-id="4f679-143">XslTransform Sınıfı ile XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="4f679-143">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="4f679-144">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="4f679-144">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
