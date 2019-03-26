---
title: XslTransform sınıfı ile XSLT dönüşümleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 500335af-f9b5-413b-968a-e6d9a824478c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db10dda3cbb328cd143afa48e300588ccc7667a6
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463078"
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a><span data-ttu-id="71655-102">XslTransform sınıfı ile XSLT dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="71655-102">XSLT Transformations with the XslTransform Class</span></span>

> [!NOTE]
> <span data-ttu-id="71655-103"><xref:System.Xml.Xsl.XslTransform> Sınıftır eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="71655-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="71655-104">Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="71655-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="71655-105">Bkz: [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](migrating-from-the-xsltransform-class.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="71655-105">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>

<span data-ttu-id="71655-106">Farklı biçimde veya yapısı (örneğin, bir Web sitesinde kullanılmak HTML'e XML dönüştürmek için veya yalnızca alanları gerekli b içeren bir belgeye dönüştürmek için başka bir belgeye kaynak XML belgesinin içeriğini dönüştürmek için XSLT hedefi olan "y, bir uygulama).</span><span class="sxs-lookup"><span data-stu-id="71655-106">The goal of the XSLT is to transform the content of a source XML document into another document that is different in format or structure (for example, to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application).</span></span> <span data-ttu-id="71655-107">Bu dönüştürme süreci World Wide Web Consortium (W3C) tarafından belirtilen[XSLT sürümü 1.0 öneri](https://www.w3.org/TR/1999/REC-xslt-19991116).</span><span class="sxs-lookup"><span data-stu-id="71655-107">This transformation process is specified by the World Wide Web Consortium (W3C)[XSLT version 1.0 recommendation](https://www.w3.org/TR/1999/REC-xslt-19991116).</span></span> <span data-ttu-id="71655-108">İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], <xref:System.Xml.Xsl.XslTransform> bulunan sınıf <xref:System.Xml.Xsl> ad, bu belirtim işlevselliğini uygular XSLT işlemci alanıdır.</span><span class="sxs-lookup"><span data-stu-id="71655-108">In the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], the <xref:System.Xml.Xsl.XslTransform> class, found in the <xref:System.Xml.Xsl> namespace, is the XSLT processor that implements the functionality of this specification.</span></span> <span data-ttu-id="71655-109">Az sayıda gelen listelenen W3C XSLT 1.0 öneri henüz geliştirilmemiştir özellikleri vardır [XslTransform çıkışları](outputs-from-an-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="71655-109">There are a small number of features that have not been implemented from the W3C XSLT 1.0 recommendation, listed in [Outputs from an XslTransform](outputs-from-an-xsltransform.md).</span></span> <span data-ttu-id="71655-110">Dönüştürme mimarisi aşağıdaki şekilde gösterilmiştir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="71655-110">The following figure shows the transformation architecture of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>

## <a name="overview"></a><span data-ttu-id="71655-111">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="71655-111">Overview</span></span>

![XSLT dönüşümü mimarisini gösteren diyagram.](./media/xslt-transformations-with-the-xsltransform-class/xslt-transformation-architecture.gif) 

<span data-ttu-id="71655-113">XSLT öneri, XPath düğümleri belge ağacının gezinmek için kullanılan bir sorgu dili olduğu parçaları bir XML belgesi seçmek için XML Path Language (XPath) kullanır.</span><span class="sxs-lookup"><span data-stu-id="71655-113">The XSLT recommendation uses XML Path Language (XPath) to select parts of an XML document, where XPath is a query language used to navigate nodes of a document tree.</span></span> <span data-ttu-id="71655-114">Diyagramda gösterildiği gibi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] XPath uygulaması gibi birçok sınıf içinde depolanan XML bölümlerini seçmek amacıyla kullanılan bir <xref:System.Xml.XmlDocument>e <xref:System.Xml.XmlDataDocument>ve bir <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="71655-114">As shown in the diagram, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementation of XPath is used to select parts of XML stored in several classes, such as an <xref:System.Xml.XmlDocument>, an <xref:System.Xml.XmlDataDocument>, and an <xref:System.Xml.XPath.XPathDocument>.</span></span> <span data-ttu-id="71655-115">Bir <xref:System.Xml.XPath.XPathDocument> en iyi duruma getirilmiş bir XSLT veri deposu ve ile kullanıldığında <xref:System.Xml.Xsl.XslTransform>, XSLT dönüşümleri iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="71655-115">An <xref:System.Xml.XPath.XPathDocument> is an optimized XSLT data store, and when used with <xref:System.Xml.Xsl.XslTransform>, it provides XSLT transformations with good performance.</span></span>

<span data-ttu-id="71655-116">Aşağıdaki tablo listesini yaygın olarak çalışırken sınıfları kullanan <xref:System.Xml.Xsl.XslTransform> ve XPath ve bunların işlevi.</span><span class="sxs-lookup"><span data-stu-id="71655-116">The following table list commonly uses classes when working with <xref:System.Xml.Xsl.XslTransform> and XPath and their function.</span></span>

|<span data-ttu-id="71655-117">Sınıf veya arabirim</span><span class="sxs-lookup"><span data-stu-id="71655-117">Class or Interface</span></span>|<span data-ttu-id="71655-118">İşlev</span><span class="sxs-lookup"><span data-stu-id="71655-118">Function</span></span>|
|------------------------|--------------|
|<xref:System.Xml.XPath.XPathNavigator>|<span data-ttu-id="71655-119">XPath sorgusu desteğiyle birlikte bir depolama üzerinde gezinmek için bir imleç stil model sağlayan bir API'dir.</span><span class="sxs-lookup"><span data-stu-id="71655-119">It is an API that provides a cursor style model for navigating over a store, along with XPath query support.</span></span> <span data-ttu-id="71655-120">Temel alınan deposu düzenleme sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="71655-120">It does not provide editing of the underlying store.</span></span> <span data-ttu-id="71655-121">Düzenlemek üzere <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="71655-121">For editing, use the <xref:System.Xml.XmlDocument> class.</span></span>|
|<xref:System.Xml.XPath.IXPathNavigable>|<span data-ttu-id="71655-122">Sağlayan bir arabirimi olan bir `CreateNavigator` yönteme bir <xref:System.Xml.XPath.XPathNavigator> deposu.</span><span class="sxs-lookup"><span data-stu-id="71655-122">It is an interface that provides a `CreateNavigator` method to an <xref:System.Xml.XPath.XPathNavigator> for the store.</span></span>|
|<xref:System.Xml.XmlDocument>|<span data-ttu-id="71655-123">Ancak, bu belgenin düzenleme etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="71655-123">It enables editing of this document.</span></span> <span data-ttu-id="71655-124">Bunu uygulayan <xref:System.Xml.XPath.IXPathNavigable>, belge düzenleme senaryoları XSLT dönüşümleri nerede daha sonra gerekli izin verme.</span><span class="sxs-lookup"><span data-stu-id="71655-124">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing document-editing scenarios where XSLT transformations are subsequently required.</span></span> <span data-ttu-id="71655-125">Daha fazla bilgi için [xsltransform'a XmlDocument girişi](xmldocument-input-to-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="71655-125">For more information, see [XmlDocument Input to XslTransform](xmldocument-input-to-xsltransform.md).</span></span>|
|<xref:System.Xml.XmlDataDocument>|<span data-ttu-id="71655-126">Öğesinden türetilen <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="71655-126">It is derived from the <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="71655-127">İlişkisel arasında köprü ve sektörün en iyilerinden kullanarak XML bir <xref:System.Data.DataSet> üzerinde belirtilen eşlemeleri göre bir XML belgesi içinde yapılandırılmış verilerin depolama en iyi duruma getirme <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="71655-127">It bridges the relational and XML worlds by using a <xref:System.Data.DataSet> to optimize storage of structured data within the XML document according to specified mappings on the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="71655-128">Bunu uygulayan <xref:System.Xml.XPath.IXPathNavigable>, burada XSLT dönüşümleri gerçekleştirilebilir ilişkisel veriler bir veritabanından alınan üzerinde senaryoları izin verme.</span><span class="sxs-lookup"><span data-stu-id="71655-128">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing scenarios where XSLT transformations can be performed over relational data retrieved from a database.</span></span> <span data-ttu-id="71655-129">Daha fazla bilgi için [ilişkisel veriler ve ADO.NET ile XML tümleştirmesi](xml-integration-with-relational-data-and-adonet.md).</span><span class="sxs-lookup"><span data-stu-id="71655-129">For more information, see [XML Integration with Relational Data and ADO.NET](xml-integration-with-relational-data-and-adonet.md).</span></span>|
|<xref:System.Xml.XPath.XPathDocument>|<span data-ttu-id="71655-130">Bu sınıf için optimize edilmiştir <xref:System.Xml.Xsl.XslTransform> işleme ve XPath sorgularını ve salt okunur yüksek performanslı bir önbellek sağlar.</span><span class="sxs-lookup"><span data-stu-id="71655-130">This class is optimized for <xref:System.Xml.Xsl.XslTransform> processing and XPath queries, and it provides a read-only high performance cache.</span></span> <span data-ttu-id="71655-131">Bunu uygulayan <xref:System.Xml.XPath.IXPathNavigable> ve XSLT dönüşümleri için kullanılacak tercih edilen deposudur.</span><span class="sxs-lookup"><span data-stu-id="71655-131">It implements <xref:System.Xml.XPath.IXPathNavigable> and is the preferred store to use for XSLT transformations.</span></span>|
|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="71655-132">Bu XPath düğüm kümeleri üzerinde gezinme sağlar.</span><span class="sxs-lookup"><span data-stu-id="71655-132">It provides navigation over XPath node sets.</span></span> <span data-ttu-id="71655-133">Tüm XPath seçimi yöntemlerde <xref:System.Xml.XPath.XPathNavigator> dönüş bir <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="71655-133">All XPath selection methods on the <xref:System.Xml.XPath.XPathNavigator> return an <xref:System.Xml.XPath.XPathNodeIterator>.</span></span> <span data-ttu-id="71655-134">Birden çok <xref:System.Xml.XPath.XPathNodeIterator> nesneleri her bir seçili düğümleri kümesini temsil eden aynı depo üzerinde oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="71655-134">Multiple <xref:System.Xml.XPath.XPathNodeIterator> objects can be created over the same store, each representing a selected set of nodes.</span></span>|

## <a name="msxml-xslt-extensions"></a><span data-ttu-id="71655-135">MSXML XSLT uzantıları</span><span class="sxs-lookup"><span data-stu-id="71655-135">MSXML XSLT Extensions</span></span>

<span data-ttu-id="71655-136">`msxsl:script` Ve `msxsl:node-set` işlevlerdir yalnızca Microsoft XML Çekirdek Hizmetleri (MSXML) XSLT uzantıları tarafından desteklenen <xref:System.Xml.Xsl.XslTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="71655-136">The `msxsl:script` and `msxsl:node-set` functions are the only Microsoft XML Core Services (MSXML) XSLT extensions supported by the <xref:System.Xml.Xsl.XslTransform> class.</span></span>

## <a name="example"></a><span data-ttu-id="71655-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="71655-137">Example</span></span>

<span data-ttu-id="71655-138">Aşağıdaki kod örneği bir XSLT stil sayfası yükler okur mydata.xml içine adlı bir dosyaya bir <xref:System.Xml.XPath.XPathDocument>ve veri myStyleSheet.xsl, konsola biçimlendirilmiş çıktı gönderen adlı kurgusal bir dosya çubuğunda bir dönüştürme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="71655-138">The following code example loads an XSLT style sheet, reads a file called mydata.xml into an <xref:System.Xml.XPath.XPathDocument>, and performs a transformation on the data on a fictitious file called myStyleSheet.xsl, sending the formatted output to the console.</span></span>

```vb
Imports System
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

## <a name="see-also"></a><span data-ttu-id="71655-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71655-139">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>
- [<span data-ttu-id="71655-140">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="71655-140">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="71655-141">XslTransform Sınıfında İsteğe Bağlı Davranışların Uygulanması</span><span class="sxs-lookup"><span data-stu-id="71655-141">Implementation of Discretionary Behaviors in the XslTransform Class</span></span>](implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)
- [<span data-ttu-id="71655-142">Dönüşümlerde XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="71655-142">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)
- [<span data-ttu-id="71655-143">Dönüşümlerde XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="71655-143">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="71655-144">XslTransform’a XPathDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="71655-144">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="71655-145">XslTransform’a XmlDataDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="71655-145">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)
- [<span data-ttu-id="71655-146">XslTransform’a XmlDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="71655-146">XmlDocument Input to XslTransform</span></span>](xmldocument-input-to-xsltransform.md)
