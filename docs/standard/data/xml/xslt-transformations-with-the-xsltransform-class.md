---
title: XslTransform Sınıfı ile XSLT Dönüşümleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 500335af-f9b5-413b-968a-e6d9a824478c
ms.openlocfilehash: e03eb08c71ff2d031ac61a702683e3950d94f2be
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160241"
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a>XslTransform Sınıfı ile XSLT Dönüşümleri

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> sınıfı, .NET Framework 2,0 ' de kullanılmıyor. <xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz. Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .

XSLT 'nin amacı, bir kaynak XML belgesinin içeriğini biçim veya yapıda farklı bir belgeye dönüştürmektir (örneğin, XML 'i bir Web sitesinde kullanılmak üzere veya yalnızca gerekli alanları içeren bir belgeye dönüştürmek için). y bir uygulama). Bu dönüştürme işlemi World Wide Web Konsorsiyumu (W3C)[XSLT sürüm 1,0 önerisi](https://www.w3.org/TR/1999/REC-xslt-19991116)tarafından belirtilir. .NET Framework, <xref:System.Xml.Xsl> ad alanında bulunan <xref:System.Xml.Xsl.XslTransform> sınıfı, bu belirtimin işlevlerini uygulayan XSLT işlemcisidir. [Bir XslTransform çıktılarında](outputs-from-an-xsltransform.md)LISTELENEN W3C XSLT 1,0 önerinden uygulanmayan az sayıda özellik vardır. Aşağıdaki şekilde .NET Framework dönüştürme mimarisi gösterilmektedir.

## <a name="overview"></a>Genel Bakış

![XSLT dönüştürme mimarisini gösteren diyagram.](./media/xslt-transformations-with-the-xsltransform-class/xslt-transformation-architecture.gif)

XSLT önerisi bir XML belgesinin parçalarını seçmek için XML yol dili (XPath) kullanır; burada XPath bir belge ağacının düğümlerinde gezinmek için kullanılan bir sorgu dilidir. Diyagramda gösterildiği gibi, XPath .NET Framework uygulanması, bir <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>ve <xref:System.Xml.XPath.XPathDocument>gibi çeşitli sınıflarda depolanan XML parçalarını seçmek için kullanılır. <xref:System.Xml.XPath.XPathDocument> en iyi duruma getirilmiş bir XSLT veri deposudur ve <xref:System.Xml.Xsl.XslTransform>kullanıldığında, XSLT dönüştürmeleri iyi performansa sahip olur.

Aşağıdaki tablo listesi, <xref:System.Xml.Xsl.XslTransform> ve XPath ile çalışırken genellikle sınıfları ve bunların işlevlerini kullanır.

|Sınıf veya arabirim|İşlev|
|------------------------|--------------|
|<xref:System.Xml.XPath.XPathNavigator>|Bu, bir mağaza üzerinde gezinmek için, XPath sorgu desteğiyle birlikte bir imleç stil modeli sağlayan bir API 'dir. Temel alınan deponun düzenlenmesinin sağlanması gerekmez. Düzenlenmek için <xref:System.Xml.XmlDocument> sınıfını kullanın.|
|<xref:System.Xml.XPath.IXPathNavigable>|Mağaza için bir <xref:System.Xml.XPath.XPathNavigator> `CreateNavigator` yöntemi sağlayan bir arabirimdir.|
|<xref:System.Xml.XmlDocument>|Bu belgenin düzenlenmesine izin vermez. XSLT dönüştürmelerinin daha sonra gerekli olduğu belge düzenlemesi senaryolarına izin vererek <xref:System.Xml.XPath.IXPathNavigable>uygular. Daha fazla bilgi için bkz. [XslTransform 'A XmlDocument girişi](xmldocument-input-to-xsltransform.md).|
|<xref:System.Xml.XmlDataDocument>|<xref:System.Xml.XmlDocument>türetilir. XML belgesi içindeki yapılandırılmış verilerin depolanmasını, <xref:System.Data.DataSet>belirtilen eşlemelere göre iyileştirmek için bir <xref:System.Data.DataSet> kullanarak ilişkisel ve XML dünyalarını köprüler. <xref:System.Xml.XPath.IXPathNavigable>uygular ve XSLT dönüştürmelerinin bir veritabanından alınan ilişkisel veriler üzerinden gerçekleştirilebileceği senaryolara olanak tanır. Daha fazla bilgi için bkz. [Ilişkisel verilerle XML tümleştirmesi ve ADO.net](xml-integration-with-relational-data-and-adonet.md).|
|<xref:System.Xml.XPath.XPathDocument>|Bu sınıf, <xref:System.Xml.Xsl.XslTransform> işleme ve XPath sorguları için iyileştirilmiştir ve salt okunurdur ve yüksek performanslı önbellek sağlar. <xref:System.Xml.XPath.IXPathNavigable> uygular ve XSLT dönüştürmeleri için kullanılacak tercih edilen depodır.|
|<xref:System.Xml.XPath.XPathNodeIterator>|XPath düğüm kümelerine göre gezinme sağlar. <xref:System.Xml.XPath.XPathNavigator> tüm XPath seçim yöntemleri bir <xref:System.Xml.XPath.XPathNodeIterator>döndürür. Her biri seçili düğüm kümesini temsil eden aynı mağaza üzerinde birden çok <xref:System.Xml.XPath.XPathNodeIterator> nesne oluşturulabilir.|

## <a name="msxml-xslt-extensions"></a>MSXML XSLT uzantıları

`msxsl:script` ve `msxsl:node-set` işlevleri, <xref:System.Xml.Xsl.XslTransform> sınıfı tarafından desteklenen tek Microsoft XML Çekirdek Hizmetleri (MSXML) XSLT uzantılarıdır.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği bir XSLT stil sayfası yükler, mydata. xml adlı bir dosyayı <xref:System.Xml.XPath.XPathDocument>okur ve yerleşik çıktıyı konsola göndererek myStyleSheet. xsl adlı kurgusal bir dosyadaki verilerde bir dönüştürme gerçekleştirir.

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

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Xsl.XslTransform>
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](xsltransform-class-implements-the-xslt-processor.md)
- [XslTransform Sınıfında İsteğe Bağlı Davranışların Uygulanması](implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)
- [Dönüşümlerde XPathNavigator](xpathnavigator-in-transformations.md)
- [Dönüşümlerde XPathNodeIterator](xpathnodeiterator-in-transformations.md)
- [XslTransform’a XPathDocument Girişi](xpathdocument-input-to-xsltransform.md)
- [XslTransform’a XmlDataDocument Girişi](xmldatadocument-input-to-xsltransform.md)
- [XslTransform’a XmlDocument Girişi](xmldocument-input-to-xsltransform.md)
