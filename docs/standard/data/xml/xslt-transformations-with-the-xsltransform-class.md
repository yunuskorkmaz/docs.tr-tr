---
description: Daha fazla bilgi için bkz. XslTransform sınıfıyla XSLT dönüşümleri
title: XslTransform Sınıfı ile XSLT Dönüşümleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 500335af-f9b5-413b-968a-e6d9a824478c
ms.openlocfilehash: f350bf8c27804afe769629bc1efdeb1bb51a2876
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731922"
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a><span data-ttu-id="0e0c8-103">XslTransform Sınıfı ile XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="0e0c8-103">XSLT Transformations with the XslTransform Class</span></span>

> [!NOTE]
> <span data-ttu-id="0e0c8-104"><xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="0e0c8-105">Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="0e0c8-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="0e0c8-106">Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="0e0c8-106">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>

<span data-ttu-id="0e0c8-107">XSLT 'nin amacı, bir kaynak XML belgesinin içeriğini biçim veya yapıda farklı bir belgeye dönüştürmektir (örneğin, XML 'i bir Web sitesinde kullanılmak üzere veya yalnızca bir uygulama tarafından gereken alanları içeren bir belgeye dönüştürmek için).</span><span class="sxs-lookup"><span data-stu-id="0e0c8-107">The goal of the XSLT is to transform the content of a source XML document into another document that is different in format or structure (for example, to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application).</span></span> <span data-ttu-id="0e0c8-108">Bu dönüştürme işlemi World Wide Web Konsorsiyumu (W3C)[XSLT sürüm 1,0 önerisi](https://www.w3.org/TR/1999/REC-xslt-19991116)tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-108">This transformation process is specified by the World Wide Web Consortium (W3C)[XSLT version 1.0 recommendation](https://www.w3.org/TR/1999/REC-xslt-19991116).</span></span> <span data-ttu-id="0e0c8-109">.NET Framework, <xref:System.Xml.Xsl.XslTransform> ad alanında bulunan sınıfı, <xref:System.Xml.Xsl> Bu belirtimin IŞLEVLERINI uygulayan XSLT işlemcisidir.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-109">In the .NET Framework, the <xref:System.Xml.Xsl.XslTransform> class, found in the <xref:System.Xml.Xsl> namespace, is the XSLT processor that implements the functionality of this specification.</span></span> <span data-ttu-id="0e0c8-110">[Bir XslTransform çıktılarında](outputs-from-an-xsltransform.md)LISTELENEN W3C XSLT 1,0 önerinden uygulanmayan az sayıda özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-110">There are a small number of features that have not been implemented from the W3C XSLT 1.0 recommendation, listed in [Outputs from an XslTransform](outputs-from-an-xsltransform.md).</span></span> <span data-ttu-id="0e0c8-111">Aşağıdaki şekilde .NET Framework dönüştürme mimarisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-111">The following figure shows the transformation architecture of the .NET Framework.</span></span>

## <a name="overview"></a><span data-ttu-id="0e0c8-112">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0e0c8-112">Overview</span></span>

![XSLT dönüştürme mimarisini gösteren diyagram.](./media/xslt-transformations-with-the-xsltransform-class/xslt-transformation-architecture.gif)

<span data-ttu-id="0e0c8-114">XSLT önerisi bir XML belgesinin parçalarını seçmek için XML yol dili (XPath) kullanır; burada XPath bir belge ağacının düğümlerinde gezinmek için kullanılan bir sorgu dilidir.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-114">The XSLT recommendation uses XML Path Language (XPath) to select parts of an XML document, where XPath is a query language used to navigate nodes of a document tree.</span></span> <span data-ttu-id="0e0c8-115">Diyagramda gösterildiği gibi, XPath .NET Framework uygulama, bir, ve gibi çeşitli sınıflarda depolanan XML parçalarını seçmek için kullanılır <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDataDocument> <xref:System.Xml.XPath.XPathDocument> .</span><span class="sxs-lookup"><span data-stu-id="0e0c8-115">As shown in the diagram, the .NET Framework implementation of XPath is used to select parts of XML stored in several classes, such as an <xref:System.Xml.XmlDocument>, an <xref:System.Xml.XmlDataDocument>, and an <xref:System.Xml.XPath.XPathDocument>.</span></span> <span data-ttu-id="0e0c8-116">, <xref:System.Xml.XPath.XPathDocument> En iyi duruma getirilmiş BIR XSLT veri deposudur ve ile kullanıldığında <xref:System.Xml.Xsl.XslTransform> , XSLT dönüştürmelerini iyi performansla sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-116">An <xref:System.Xml.XPath.XPathDocument> is an optimized XSLT data store, and when used with <xref:System.Xml.Xsl.XslTransform>, it provides XSLT transformations with good performance.</span></span>

<span data-ttu-id="0e0c8-117">Aşağıdaki tablo listesi, ve XPath ve işlevleri ile çalışırken yaygın olarak sınıfları kullanır <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="0e0c8-117">The following table list commonly uses classes when working with <xref:System.Xml.Xsl.XslTransform> and XPath and their function.</span></span>

|<span data-ttu-id="0e0c8-118">Sınıf veya arabirim</span><span class="sxs-lookup"><span data-stu-id="0e0c8-118">Class or Interface</span></span>|<span data-ttu-id="0e0c8-119">İşlev</span><span class="sxs-lookup"><span data-stu-id="0e0c8-119">Function</span></span>|
|------------------------|--------------|
|<xref:System.Xml.XPath.XPathNavigator>|<span data-ttu-id="0e0c8-120">Bu, bir mağaza üzerinde gezinmek için, XPath sorgu desteğiyle birlikte bir imleç stil modeli sağlayan bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-120">It is an API that provides a cursor style model for navigating over a store, along with XPath query support.</span></span> <span data-ttu-id="0e0c8-121">Temel alınan deponun düzenlenmesinin sağlanması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-121">It does not provide editing of the underlying store.</span></span> <span data-ttu-id="0e0c8-122">Düzenlemede, <xref:System.Xml.XmlDocument> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-122">For editing, use the <xref:System.Xml.XmlDocument> class.</span></span>|
|<xref:System.Xml.XPath.IXPathNavigable>|<span data-ttu-id="0e0c8-123">Mağaza için bir yöntemi sağlayan bir arabirimdir `CreateNavigator` <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="0e0c8-123">It is an interface that provides a `CreateNavigator` method to an <xref:System.Xml.XPath.XPathNavigator> for the store.</span></span>|
|<xref:System.Xml.XmlDocument>|<span data-ttu-id="0e0c8-124">Bu belgenin düzenlenmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-124">It enables editing of this document.</span></span> <span data-ttu-id="0e0c8-125"><xref:System.Xml.XPath.IXPathNavigable>XSLT dönüştürmelerinin daha sonra gerekli olduğu belge düzenlemesi senaryolarına izin vererek uygular.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-125">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing document-editing scenarios where XSLT transformations are subsequently required.</span></span> <span data-ttu-id="0e0c8-126">Daha fazla bilgi için bkz. [XslTransform 'A XmlDocument girişi](xmldocument-input-to-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="0e0c8-126">For more information, see [XmlDocument Input to XslTransform](xmldocument-input-to-xsltransform.md).</span></span>|
|<xref:System.Xml.XmlDataDocument>|<span data-ttu-id="0e0c8-127">, Öğesinden türetilir <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="0e0c8-127">It is derived from the <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="0e0c8-128"><xref:System.Data.DataSet>XML belgesi içindeki yapılandırılmış verilerin depolanmasını, içindeki belirtilen eşlemelere göre iyileştirmek için kullanarak ilişkisel ve XML çalışma LDS köprülerini köprüleyerek <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="0e0c8-128">It bridges the relational and XML worlds by using a <xref:System.Data.DataSet> to optimize storage of structured data within the XML document according to specified mappings on the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="0e0c8-129">Bu <xref:System.Xml.XPath.IXPathNavigable> , XSLT dönüştürmelerinin bir veritabanından alınan ilişkisel veriler üzerinden gerçekleştirilebileceği senaryolara olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-129">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing scenarios where XSLT transformations can be performed over relational data retrieved from a database.</span></span> <span data-ttu-id="0e0c8-130">Daha fazla bilgi için bkz. [Ilişkisel verilerle XML tümleştirmesi ve ADO.net](xml-integration-with-relational-data-and-adonet.md).</span><span class="sxs-lookup"><span data-stu-id="0e0c8-130">For more information, see [XML Integration with Relational Data and ADO.NET](xml-integration-with-relational-data-and-adonet.md).</span></span>|
|<xref:System.Xml.XPath.XPathDocument>|<span data-ttu-id="0e0c8-131">Bu sınıf <xref:System.Xml.Xsl.XslTransform> , işleme ve XPath sorguları için en iyi duruma getirilmiştir ve salt okunurdur ve yüksek performanslı önbellek sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-131">This class is optimized for <xref:System.Xml.Xsl.XslTransform> processing and XPath queries, and it provides a read-only high performance cache.</span></span> <span data-ttu-id="0e0c8-132"><xref:System.Xml.XPath.IXPathNavigable>XSLT dönüştürmeleri için kullanılacak tercih edilen mağaza ve uygular.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-132">It implements <xref:System.Xml.XPath.IXPathNavigable> and is the preferred store to use for XSLT transformations.</span></span>|
|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="0e0c8-133">XPath düğüm kümelerine göre gezinme sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-133">It provides navigation over XPath node sets.</span></span> <span data-ttu-id="0e0c8-134">Döndüren tüm XPath seçim yöntemleri <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNodeIterator> .</span><span class="sxs-lookup"><span data-stu-id="0e0c8-134">All XPath selection methods on the <xref:System.Xml.XPath.XPathNavigator> return an <xref:System.Xml.XPath.XPathNodeIterator>.</span></span> <span data-ttu-id="0e0c8-135"><xref:System.Xml.XPath.XPathNodeIterator>Her biri seçili düğüm kümesini temsil eden aynı mağaza üzerinde birden fazla nesne oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-135">Multiple <xref:System.Xml.XPath.XPathNodeIterator> objects can be created over the same store, each representing a selected set of nodes.</span></span>|

## <a name="msxml-xslt-extensions"></a><span data-ttu-id="0e0c8-136">MSXML XSLT uzantıları</span><span class="sxs-lookup"><span data-stu-id="0e0c8-136">MSXML XSLT Extensions</span></span>

<span data-ttu-id="0e0c8-137">`msxsl:script`Ve `msxsl:node-set` işlevleri, sınıfının desteklediği tek Microsoft XML Çekirdek HIZMETLERI (MSXML) XSLT uzantılarıdır <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="0e0c8-137">The `msxsl:script` and `msxsl:node-set` functions are the only Microsoft XML Core Services (MSXML) XSLT extensions supported by the <xref:System.Xml.Xsl.XslTransform> class.</span></span>

## <a name="example"></a><span data-ttu-id="0e0c8-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e0c8-138">Example</span></span>

<span data-ttu-id="0e0c8-139">Aşağıdaki kod örneği bir XSLT stil sayfası yükler, ' a mydata.xml adlı dosyayı okur ve yerleşik <xref:System.Xml.XPath.XPathDocument> çıktıyı konsola göndererek myStyleSheet. xsl adlı kurgusal bir dosyadaki verilerde bir dönüştürme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-139">The following code example loads an XSLT style sheet, reads a file called mydata.xml into an <xref:System.Xml.XPath.XPathDocument>, and performs a transformation on the data on a fictitious file called myStyleSheet.xsl, sending the formatted output to the console.</span></span>

```vb
Imports System.IO
Imports System.Xml
Imports System.Xml.XPath
Imports System.Xml.Xsl

Public Class Sample
    Private filename As [String] = "mydata.xml"
    Private stylesheet As [String] = "myStyleSheet.xsl"

    Public Shared Sub Main()
        Dim xslt As New XslTransform()
        xslt.Load(stylesheet)
        Dim xpathdocument As New XPathDocument(filename)
        Dim writer As New XmlTextWriter(Console.Out)
        writer.Formatting = Formatting.Indented

        xslt.Transform(xpathdocument, Nothing, writer, Nothing)
    End Sub 'Main
End Class 'Sample
```

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.XPath;
using System.Xml.Xsl;

public class Sample
{
    private const String filename = "mydata.xml";
    private const String stylesheet = "myStyleSheet.xsl";

    public static void Main()
    {
        XslTransform xslt = new XslTransform();
        xslt.Load(stylesheet);
        XPathDocument xpathdocument = new XPathDocument(filename);
        XmlTextWriter writer = new XmlTextWriter(Console.Out);
        writer.Formatting = Formatting.Indented;

        xslt.Transform(xpathdocument, null, writer, null);
    }
}
```

## <a name="see-also"></a><span data-ttu-id="0e0c8-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e0c8-140">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>
- [<span data-ttu-id="0e0c8-141">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="0e0c8-141">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="0e0c8-142">XslTransform Sınıfında İsteğe Bağlı Davranışların Uygulanması</span><span class="sxs-lookup"><span data-stu-id="0e0c8-142">Implementation of Discretionary Behaviors in the XslTransform Class</span></span>](implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)
- [<span data-ttu-id="0e0c8-143">Dönüşümlerde XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0e0c8-143">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)
- [<span data-ttu-id="0e0c8-144">Dönüşümlerde XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="0e0c8-144">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="0e0c8-145">XslTransform’a XPathDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="0e0c8-145">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="0e0c8-146">XslTransform’a XmlDataDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="0e0c8-146">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)
- [<span data-ttu-id="0e0c8-147">XslTransform’a XmlDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="0e0c8-147">XmlDocument Input to XslTransform</span></span>](xmldocument-input-to-xsltransform.md)
