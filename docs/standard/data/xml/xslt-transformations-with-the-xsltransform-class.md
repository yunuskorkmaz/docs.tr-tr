---
title: XslTransform Sınıfı ile XSLT Dönüşümleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 500335af-f9b5-413b-968a-e6d9a824478c
ms.openlocfilehash: ccdee1bbb94581d842cfc6fabe0f98dd6ec1d252
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818238"
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a>XslTransform Sınıfı ile XSLT Dönüşümleri

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor. Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> . Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .

XSLT 'nin amacı, bir kaynak XML belgesinin içeriğini biçim veya yapıda farklı bir belgeye dönüştürmektir (örneğin, XML 'i bir Web sitesinde kullanılmak üzere veya yalnızca bir uygulama tarafından gereken alanları içeren bir belgeye dönüştürmek için). Bu dönüştürme işlemi World Wide Web Konsorsiyumu (W3C)[XSLT sürüm 1,0 önerisi](https://www.w3.org/TR/1999/REC-xslt-19991116)tarafından belirtilir. .NET Framework, <xref:System.Xml.Xsl.XslTransform> ad alanında bulunan sınıfı, <xref:System.Xml.Xsl> Bu belirtimin IŞLEVLERINI uygulayan XSLT işlemcisidir. [Bir XslTransform çıktılarında](outputs-from-an-xsltransform.md)LISTELENEN W3C XSLT 1,0 önerinden uygulanmayan az sayıda özellik vardır. Aşağıdaki şekilde .NET Framework dönüştürme mimarisi gösterilmektedir.

## <a name="overview"></a>Genel Bakış

![XSLT dönüştürme mimarisini gösteren diyagram.](./media/xslt-transformations-with-the-xsltransform-class/xslt-transformation-architecture.gif)

XSLT önerisi bir XML belgesinin parçalarını seçmek için XML yol dili (XPath) kullanır; burada XPath bir belge ağacının düğümlerinde gezinmek için kullanılan bir sorgu dilidir. Diyagramda gösterildiği gibi, XPath .NET Framework uygulama, bir, ve gibi çeşitli sınıflarda depolanan XML parçalarını seçmek için kullanılır <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDataDocument> <xref:System.Xml.XPath.XPathDocument> . , <xref:System.Xml.XPath.XPathDocument> En iyi duruma getirilmiş BIR XSLT veri deposudur ve ile kullanıldığında <xref:System.Xml.Xsl.XslTransform> , XSLT dönüştürmelerini iyi performansla sağlar.

Aşağıdaki tablo listesi, ve XPath ve işlevleri ile çalışırken yaygın olarak sınıfları kullanır <xref:System.Xml.Xsl.XslTransform> .

|Sınıf veya arabirim|İşlev|
|------------------------|--------------|
|<xref:System.Xml.XPath.XPathNavigator>|Bu, bir mağaza üzerinde gezinmek için, XPath sorgu desteğiyle birlikte bir imleç stil modeli sağlayan bir API 'dir. Temel alınan deponun düzenlenmesinin sağlanması gerekmez. Düzenlemede, <xref:System.Xml.XmlDocument> sınıfını kullanın.|
|<xref:System.Xml.XPath.IXPathNavigable>|Mağaza için bir yöntemi sağlayan bir arabirimdir `CreateNavigator` <xref:System.Xml.XPath.XPathNavigator> .|
|<xref:System.Xml.XmlDocument>|Bu belgenin düzenlenmesine izin vermez. <xref:System.Xml.XPath.IXPathNavigable>XSLT dönüştürmelerinin daha sonra gerekli olduğu belge düzenlemesi senaryolarına izin vererek uygular. Daha fazla bilgi için bkz. [XslTransform 'A XmlDocument girişi](xmldocument-input-to-xsltransform.md).|
|<xref:System.Xml.XmlDataDocument>|, Öğesinden türetilir <xref:System.Xml.XmlDocument> . <xref:System.Data.DataSet>XML belgesi içindeki yapılandırılmış verilerin depolanmasını, içindeki belirtilen eşlemelere göre iyileştirmek için kullanarak ilişkisel ve XML çalışma LDS köprülerini köprüleyerek <xref:System.Data.DataSet> . Bu <xref:System.Xml.XPath.IXPathNavigable> , XSLT dönüştürmelerinin bir veritabanından alınan ilişkisel veriler üzerinden gerçekleştirilebileceği senaryolara olanak tanır. Daha fazla bilgi için bkz. [Ilişkisel verilerle XML tümleştirmesi ve ADO.net](xml-integration-with-relational-data-and-adonet.md).|
|<xref:System.Xml.XPath.XPathDocument>|Bu sınıf <xref:System.Xml.Xsl.XslTransform> , işleme ve XPath sorguları için en iyi duruma getirilmiştir ve salt okunurdur ve yüksek performanslı önbellek sağlar. <xref:System.Xml.XPath.IXPathNavigable>XSLT dönüştürmeleri için kullanılacak tercih edilen mağaza ve uygular.|
|<xref:System.Xml.XPath.XPathNodeIterator>|XPath düğüm kümelerine göre gezinme sağlar. Döndüren tüm XPath seçim yöntemleri <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNodeIterator> . <xref:System.Xml.XPath.XPathNodeIterator>Her biri seçili düğüm kümesini temsil eden aynı mağaza üzerinde birden fazla nesne oluşturulabilir.|

## <a name="msxml-xslt-extensions"></a>MSXML XSLT uzantıları

`msxsl:script`Ve `msxsl:node-set` işlevleri, sınıfının desteklediği tek Microsoft XML Çekirdek HIZMETLERI (MSXML) XSLT uzantılarıdır <xref:System.Xml.Xsl.XslTransform> .

## <a name="example"></a>Örnek

Aşağıdaki kod örneği bir XSLT stil sayfası yükler, ' a mydata.xml adlı dosyayı okur ve yerleşik <xref:System.Xml.XPath.XPathDocument> çıktıyı konsola göndererek myStyleSheet. xsl adlı kurgusal bir dosyadaki verilerde bir dönüştürme gerçekleştirir.

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
