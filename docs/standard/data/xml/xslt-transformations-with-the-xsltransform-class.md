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
# <a name="xslt-transformations-with-the-xsltransform-class"></a>XslTransform sınıfı ile XSLT dönüşümleri

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Sınıftır eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](migrating-from-the-xsltransform-class.md) daha fazla bilgi için.

Farklı biçimde veya yapısı (örneğin, bir Web sitesinde kullanılmak HTML'e XML dönüştürmek için veya yalnızca alanları gerekli b içeren bir belgeye dönüştürmek için başka bir belgeye kaynak XML belgesinin içeriğini dönüştürmek için XSLT hedefi olan "y, bir uygulama). Bu dönüştürme süreci World Wide Web Consortium (W3C) tarafından belirtilen[XSLT sürümü 1.0 öneri](https://www.w3.org/TR/1999/REC-xslt-19991116). İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], <xref:System.Xml.Xsl.XslTransform> bulunan sınıf <xref:System.Xml.Xsl> ad, bu belirtim işlevselliğini uygular XSLT işlemci alanıdır. Az sayıda gelen listelenen W3C XSLT 1.0 öneri henüz geliştirilmemiştir özellikleri vardır [XslTransform çıkışları](outputs-from-an-xsltransform.md). Dönüştürme mimarisi aşağıdaki şekilde gösterilmiştir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].

## <a name="overview"></a>Genel Bakış

![XSLT dönüşümü mimarisini gösteren diyagram.](./media/xslt-transformations-with-the-xsltransform-class/xslt-transformation-architecture.gif) 

XSLT öneri, XPath düğümleri belge ağacının gezinmek için kullanılan bir sorgu dili olduğu parçaları bir XML belgesi seçmek için XML Path Language (XPath) kullanır. Diyagramda gösterildiği gibi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] XPath uygulaması gibi birçok sınıf içinde depolanan XML bölümlerini seçmek amacıyla kullanılan bir <xref:System.Xml.XmlDocument>e <xref:System.Xml.XmlDataDocument>ve bir <xref:System.Xml.XPath.XPathDocument>. Bir <xref:System.Xml.XPath.XPathDocument> en iyi duruma getirilmiş bir XSLT veri deposu ve ile kullanıldığında <xref:System.Xml.Xsl.XslTransform>, XSLT dönüşümleri iyi performans sağlar.

Aşağıdaki tablo listesini yaygın olarak çalışırken sınıfları kullanan <xref:System.Xml.Xsl.XslTransform> ve XPath ve bunların işlevi.

|Sınıf veya arabirim|İşlev|
|------------------------|--------------|
|<xref:System.Xml.XPath.XPathNavigator>|XPath sorgusu desteğiyle birlikte bir depolama üzerinde gezinmek için bir imleç stil model sağlayan bir API'dir. Temel alınan deposu düzenleme sağlamaz. Düzenlemek üzere <xref:System.Xml.XmlDocument> sınıfı.|
|<xref:System.Xml.XPath.IXPathNavigable>|Sağlayan bir arabirimi olan bir `CreateNavigator` yönteme bir <xref:System.Xml.XPath.XPathNavigator> deposu.|
|<xref:System.Xml.XmlDocument>|Ancak, bu belgenin düzenleme etkinleştirir. Bunu uygulayan <xref:System.Xml.XPath.IXPathNavigable>, belge düzenleme senaryoları XSLT dönüşümleri nerede daha sonra gerekli izin verme. Daha fazla bilgi için [xsltransform'a XmlDocument girişi](xmldocument-input-to-xsltransform.md).|
|<xref:System.Xml.XmlDataDocument>|Öğesinden türetilen <xref:System.Xml.XmlDocument>. İlişkisel arasında köprü ve sektörün en iyilerinden kullanarak XML bir <xref:System.Data.DataSet> üzerinde belirtilen eşlemeleri göre bir XML belgesi içinde yapılandırılmış verilerin depolama en iyi duruma getirme <xref:System.Data.DataSet>. Bunu uygulayan <xref:System.Xml.XPath.IXPathNavigable>, burada XSLT dönüşümleri gerçekleştirilebilir ilişkisel veriler bir veritabanından alınan üzerinde senaryoları izin verme. Daha fazla bilgi için [ilişkisel veriler ve ADO.NET ile XML tümleştirmesi](xml-integration-with-relational-data-and-adonet.md).|
|<xref:System.Xml.XPath.XPathDocument>|Bu sınıf için optimize edilmiştir <xref:System.Xml.Xsl.XslTransform> işleme ve XPath sorgularını ve salt okunur yüksek performanslı bir önbellek sağlar. Bunu uygulayan <xref:System.Xml.XPath.IXPathNavigable> ve XSLT dönüşümleri için kullanılacak tercih edilen deposudur.|
|<xref:System.Xml.XPath.XPathNodeIterator>|Bu XPath düğüm kümeleri üzerinde gezinme sağlar. Tüm XPath seçimi yöntemlerde <xref:System.Xml.XPath.XPathNavigator> dönüş bir <xref:System.Xml.XPath.XPathNodeIterator>. Birden çok <xref:System.Xml.XPath.XPathNodeIterator> nesneleri her bir seçili düğümleri kümesini temsil eden aynı depo üzerinde oluşturulabilir.|

## <a name="msxml-xslt-extensions"></a>MSXML XSLT uzantıları

`msxsl:script` Ve `msxsl:node-set` işlevlerdir yalnızca Microsoft XML Çekirdek Hizmetleri (MSXML) XSLT uzantıları tarafından desteklenen <xref:System.Xml.Xsl.XslTransform> sınıfı.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği bir XSLT stil sayfası yükler okur mydata.xml içine adlı bir dosyaya bir <xref:System.Xml.XPath.XPathDocument>ve veri myStyleSheet.xsl, konsola biçimlendirilmiş çıktı gönderen adlı kurgusal bir dosya çubuğunda bir dönüştürme gerçekleştirir.

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

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Xsl.XslTransform>
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](xsltransform-class-implements-the-xslt-processor.md)
- [XslTransform Sınıfında İsteğe Bağlı Davranışların Uygulanması](implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)
- [Dönüşümlerde XPathNavigator](xpathnavigator-in-transformations.md)
- [Dönüşümlerde XPathNodeIterator](xpathnodeiterator-in-transformations.md)
- [XslTransform’a XPathDocument Girişi](xpathdocument-input-to-xsltransform.md)
- [XslTransform’a XmlDataDocument Girişi](xmldatadocument-input-to-xsltransform.md)
- [XslTransform’a XmlDocument Girişi](xmldocument-input-to-xsltransform.md)
