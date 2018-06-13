---
title: Çok sınıfı ile XSLT dönüştürmeler
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 500335af-f9b5-413b-968a-e6d9a824478c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ece159b35cfbc83e05432b93ce7df06a5ca9fcac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576174"
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a><span data-ttu-id="27d5c-102">Çok sınıfı ile XSLT dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="27d5c-102">XSLT Transformations with the XslTransform Class</span></span>
> [!NOTE]
>  <span data-ttu-id="27d5c-103"><xref:System.Xml.Xsl.XslTransform> Sınıftır'te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27d5c-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="27d5c-104">Genişletilebilir Stil sayfası dili kullanarak Dönüşümleri (XSLT) dönüştürmeleri için gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="27d5c-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="27d5c-105">Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="27d5c-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="27d5c-106">XSLT farklı biçimde veya yapısı (örneğin, bir Web sitesinde kullanılmak üzere XML HTML'e dönüştürmek için veya yalnızca alanları gerekli b içeren bir belgeye dönüştürmek için başka bir belge kaynak XML belgesinin içeriği dönüştürmek için hedefidir "y, bir uygulama).</span><span class="sxs-lookup"><span data-stu-id="27d5c-106">The goal of the XSLT is to transform the content of a source XML document into another document that is different in format or structure (for example, to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application).</span></span> <span data-ttu-id="27d5c-107">Bu dönüştürme süreci www.w3.org/TR/xslt bulunan World Wide Web Konsorsiyumu (W3C) XSLT sürüm 1.0 öneri belirtilir.</span><span class="sxs-lookup"><span data-stu-id="27d5c-107">This transformation process is specified by the World Wide Web Consortium (W3C) XSLT version 1.0 recommendation located at www.w3.org/TR/xslt.</span></span> <span data-ttu-id="27d5c-108">İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], <xref:System.Xml.Xsl.XslTransform> bulunan sınıfı <xref:System.Xml.Xsl> ad, bu belirtimi işlevselliğini uygulayan XSLT işlemci alanıdır.</span><span class="sxs-lookup"><span data-stu-id="27d5c-108">In the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], the <xref:System.Xml.Xsl.XslTransform> class, found in the <xref:System.Xml.Xsl> namespace, is the XSLT processor that implements the functionality of this specification.</span></span> <span data-ttu-id="27d5c-109">Az sayıda listelenen W3C XSLT 1.0 öneri gelen henüz geliştirilmemiştir özellikleri vardır [bir çok Çıkışlarından](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="27d5c-109">There are a small number of features that have not been implemented from the W3C XSLT 1.0 recommendation, listed in [Outputs from an XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md).</span></span> <span data-ttu-id="27d5c-110">Dönüştürme mimarisi aşağıdaki şekilde gösterilmiştir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27d5c-110">The following figure shows the transformation architecture of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="overview"></a><span data-ttu-id="27d5c-111">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="27d5c-111">Overview</span></span>  
 <span data-ttu-id="27d5c-112">![XSLT dönüşümü mimarisi](../../../../docs/standard/data/xml/media/xslttransformationswithxsltransformclass.gif "xsltTransformationsWithXslTransformClass")</span><span class="sxs-lookup"><span data-stu-id="27d5c-112">![XSLT Transformation Architecture](../../../../docs/standard/data/xml/media/xslttransformationswithxsltransformclass.gif "xsltTransformationsWithXslTransformClass")</span></span>  
<span data-ttu-id="27d5c-113">Dönüştürme mimarisi</span><span class="sxs-lookup"><span data-stu-id="27d5c-113">Transformation Architecture</span></span>  
  
 <span data-ttu-id="27d5c-114">XSLT öneri, bir XML belgesi XPath belge ağaç düğümleri gezinmek için kullanılan bir sorgu dili olduğu bölümlerini seçmek için XML Path dili (XPath) kullanır.</span><span class="sxs-lookup"><span data-stu-id="27d5c-114">The XSLT recommendation uses XML Path Language (XPath) to select parts of an XML document, where XPath is a query language used to navigate nodes of a document tree.</span></span> <span data-ttu-id="27d5c-115">Aşağıdaki çizimde gösterildiği gibi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] XPath uyarlamasını birkaç sınıflarda depolanmış XML bölümlerini seçmek amacıyla kullanılan bir <xref:System.Xml.XmlDocument>, bir <xref:System.Xml.XmlDataDocument>ve bir <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="27d5c-115">As shown in the diagram, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementation of XPath is used to select parts of XML stored in several classes, such as an <xref:System.Xml.XmlDocument>, an <xref:System.Xml.XmlDataDocument>, and an <xref:System.Xml.XPath.XPathDocument>.</span></span> <span data-ttu-id="27d5c-116">Bir <xref:System.Xml.XPath.XPathDocument> bir en iyi duruma getirilmiş XSLT veri deposu ve kullanıldığında <xref:System.Xml.Xsl.XslTransform>, XSLT dönüştürmeleri iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="27d5c-116">An <xref:System.Xml.XPath.XPathDocument> is an optimized XSLT data store, and when used with <xref:System.Xml.Xsl.XslTransform>, it provides XSLT transformations with good performance.</span></span>  
  
 <span data-ttu-id="27d5c-117">Aşağıdaki tablo listesini yaygın olarak çalışırken sınıfları kullanan <xref:System.Xml.Xsl.XslTransform> ve XPath ve bunların işlevi.</span><span class="sxs-lookup"><span data-stu-id="27d5c-117">The following table list commonly uses classes when working with <xref:System.Xml.Xsl.XslTransform> and XPath and their function.</span></span>  
  
|<span data-ttu-id="27d5c-118">Sınıf veya arabirim</span><span class="sxs-lookup"><span data-stu-id="27d5c-118">Class or Interface</span></span>|<span data-ttu-id="27d5c-119">İşlev</span><span class="sxs-lookup"><span data-stu-id="27d5c-119">Function</span></span>|  
|------------------------|--------------|  
|<xref:System.Xml.XPath.XPathNavigator>|<span data-ttu-id="27d5c-120">XPath sorgusu desteğinin yanı sıra bir mağaza üzerinden gezinmek için bir imleç stili modeli sağlayan bir API'dir.</span><span class="sxs-lookup"><span data-stu-id="27d5c-120">It is an API that provides a cursor style model for navigating over a store, along with XPath query support.</span></span> <span data-ttu-id="27d5c-121">Temel alınan deposu düzenleme sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="27d5c-121">It does not provide editing of the underlying store.</span></span> <span data-ttu-id="27d5c-122">Düzenleme için kullanmak <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="27d5c-122">For editing, use the <xref:System.Xml.XmlDocument> class.</span></span>|  
|<xref:System.Xml.XPath.IXPathNavigable>|<span data-ttu-id="27d5c-123">Sağlayan bir arabirimi olan bir `CreateNavigator` yönteme bir <xref:System.Xml.XPath.XPathNavigator> deposu için.</span><span class="sxs-lookup"><span data-stu-id="27d5c-123">It is an interface that provides a `CreateNavigator` method to an <xref:System.Xml.XPath.XPathNavigator> for the store.</span></span>|  
|<xref:System.Xml.XmlDocument>|<span data-ttu-id="27d5c-124">Bu belgenin düzenlenmesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="27d5c-124">It enables editing of this document.</span></span> <span data-ttu-id="27d5c-125">Bunu uygulayan <xref:System.Xml.XPath.IXPathNavigable>, belge düzenleme senaryoları XSLT dönüştürmeleri nerede daha sonra gerekli izin verme.</span><span class="sxs-lookup"><span data-stu-id="27d5c-125">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing document-editing scenarios where XSLT transformations are subsequently required.</span></span> <span data-ttu-id="27d5c-126">Daha fazla bilgi için bkz: [çok XmlDocument giriş](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="27d5c-126">For more information, see [XmlDocument Input to XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md).</span></span>|  
|<xref:System.Xml.XmlDataDocument>|<span data-ttu-id="27d5c-127">Öğesinden türetilen <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="27d5c-127">It is derived from the <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="27d5c-128">İlişkisel arasında köprü ve XML dünyaları kullanarak bir <xref:System.Data.DataSet> üzerinde yapılandırılmış verilerin belirtilen eşlemeleri göre XML belgesi içindeki depolama en iyi duruma getirme <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="27d5c-128">It bridges the relational and XML worlds by using a <xref:System.Data.DataSet> to optimize storage of structured data within the XML document according to specified mappings on the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="27d5c-129">Bunu uygulayan <xref:System.Xml.XPath.IXPathNavigable>, burada XSLT dönüştürmeleri yapılabilir bir veritabanından ilişkisel veriler üzerinde senaryoları izin verme.</span><span class="sxs-lookup"><span data-stu-id="27d5c-129">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing scenarios where XSLT transformations can be performed over relational data retrieved from a database.</span></span> <span data-ttu-id="27d5c-130">Daha fazla bilgi için bkz: [ilişkisel veri ve ADO.NET XML tümleştirme](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).</span><span class="sxs-lookup"><span data-stu-id="27d5c-130">For more information, see [XML Integration with Relational Data and ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).</span></span>|  
|<xref:System.Xml.XPath.XPathDocument>|<span data-ttu-id="27d5c-131">Bu sınıf en iyi hale getirildiği <xref:System.Xml.Xsl.XslTransform> işleme ve XPath sorguları ve onu bir salt okunur yüksek performanslı önbellek sağlar.</span><span class="sxs-lookup"><span data-stu-id="27d5c-131">This class is optimized for <xref:System.Xml.Xsl.XslTransform> processing and XPath queries, and it provides a read-only high performance cache.</span></span> <span data-ttu-id="27d5c-132">Bunu uygulayan <xref:System.Xml.XPath.IXPathNavigable> ve XSLT dönüştürmeleri için kullanmayı tercih edilen deposudur.</span><span class="sxs-lookup"><span data-stu-id="27d5c-132">It implements <xref:System.Xml.XPath.IXPathNavigable> and is the preferred store to use for XSLT transformations.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="27d5c-133">Bu gezinti XPath düğüm kümeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="27d5c-133">It provides navigation over XPath node sets.</span></span> <span data-ttu-id="27d5c-134">Tüm XPath seçimi yöntemlere <xref:System.Xml.XPath.XPathNavigator> dönüş bir <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="27d5c-134">All XPath selection methods on the <xref:System.Xml.XPath.XPathNavigator> return an <xref:System.Xml.XPath.XPathNodeIterator>.</span></span> <span data-ttu-id="27d5c-135">Birden çok <xref:System.Xml.XPath.XPathNodeIterator> nesneleri her seçili kümesi düğümlerinin temsil eden aynı deponun üzerinde oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="27d5c-135">Multiple <xref:System.Xml.XPath.XPathNodeIterator> objects can be created over the same store, each representing a selected set of nodes.</span></span>|  
  
## <a name="msxml-xslt-extensions"></a><span data-ttu-id="27d5c-136">MSXML XSLT uzantıları</span><span class="sxs-lookup"><span data-stu-id="27d5c-136">MSXML XSLT Extensions</span></span>  
 <span data-ttu-id="27d5c-137">`msxsl:script` Ve `msxsl:node-set` işlevlerdir tarafından desteklenen yalnızca Microsoft XML Çekirdek Hizmetleri (MSXML) XSLT uzantılarını <xref:System.Xml.Xsl.XslTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="27d5c-137">The `msxsl:script` and `msxsl:node-set` functions are the only Microsoft XML Core Services (MSXML) XSLT extensions supported by the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27d5c-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="27d5c-138">Example</span></span>  
 <span data-ttu-id="27d5c-139">Aşağıdaki kod örneğinde yükleyen bir XSLT stil sayfası okur içine mydata.xml adlı bir dosya bir <xref:System.Xml.XPath.XPathDocument>ve biçimlendirilmiş çıktıyı konsola gönderme myStyleSheet.xsl adlı kurgusal bir dosyadaki veriler üzerinde dönüştürme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="27d5c-139">The following code example loads an XSLT style sheet, reads a file called mydata.xml into an <xref:System.Xml.XPath.XPathDocument>, and performs a transformation on the data on a fictitious file called myStyleSheet.xsl, sending the formatted output to the console.</span></span>  
  
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
    XPathDocument xpathdocument = new  
    XPathDocument(filename);  
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting=Formatting.Indented;  
  
    xslt.Transform(xpathdocument, null, writer, null);      
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="27d5c-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27d5c-140">See Also</span></span>  
 <xref:System.Xml.Xsl.XslTransform>  
 [<span data-ttu-id="27d5c-141">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="27d5c-141">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [<span data-ttu-id="27d5c-142">XslTransform Sınıfında İsteğe Bağlı Davranışların Uygulanması</span><span class="sxs-lookup"><span data-stu-id="27d5c-142">Implementation of Discretionary Behaviors in the XslTransform Class</span></span>](../../../../docs/standard/data/xml/implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)  
 [<span data-ttu-id="27d5c-143">Dönüşümlerde XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="27d5c-143">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [<span data-ttu-id="27d5c-144">Dönüşümlerde XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="27d5c-144">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [<span data-ttu-id="27d5c-145">XslTransform’a XPathDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="27d5c-145">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [<span data-ttu-id="27d5c-146">XslTransform’a XmlDataDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="27d5c-146">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [<span data-ttu-id="27d5c-147">XslTransform’a XmlDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="27d5c-147">XmlDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
