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
# <a name="xslt-transformations-with-the-xsltransform-class"></a>Çok sınıfı ile XSLT dönüştürmeler
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır'te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil sayfası dili kullanarak Dönüşümleri (XSLT) dönüştürmeleri için gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 XSLT farklı biçimde veya yapısı (örneğin, bir Web sitesinde kullanılmak üzere XML HTML'e dönüştürmek için veya yalnızca alanları gerekli b içeren bir belgeye dönüştürmek için başka bir belge kaynak XML belgesinin içeriği dönüştürmek için hedefidir "y, bir uygulama). Bu dönüştürme süreci www.w3.org/TR/xslt bulunan World Wide Web Konsorsiyumu (W3C) XSLT sürüm 1.0 öneri belirtilir. İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], <xref:System.Xml.Xsl.XslTransform> bulunan sınıfı <xref:System.Xml.Xsl> ad, bu belirtimi işlevselliğini uygulayan XSLT işlemci alanıdır. Az sayıda listelenen W3C XSLT 1.0 öneri gelen henüz geliştirilmemiştir özellikleri vardır [bir çok Çıkışlarından](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md). Dönüştürme mimarisi aşağıdaki şekilde gösterilmiştir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="overview"></a>Genel Bakış  
 ![XSLT dönüşümü mimarisi](../../../../docs/standard/data/xml/media/xslttransformationswithxsltransformclass.gif "xsltTransformationsWithXslTransformClass")  
Dönüştürme mimarisi  
  
 XSLT öneri, bir XML belgesi XPath belge ağaç düğümleri gezinmek için kullanılan bir sorgu dili olduğu bölümlerini seçmek için XML Path dili (XPath) kullanır. Aşağıdaki çizimde gösterildiği gibi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] XPath uyarlamasını birkaç sınıflarda depolanmış XML bölümlerini seçmek amacıyla kullanılan bir <xref:System.Xml.XmlDocument>, bir <xref:System.Xml.XmlDataDocument>ve bir <xref:System.Xml.XPath.XPathDocument>. Bir <xref:System.Xml.XPath.XPathDocument> bir en iyi duruma getirilmiş XSLT veri deposu ve kullanıldığında <xref:System.Xml.Xsl.XslTransform>, XSLT dönüştürmeleri iyi performans sağlar.  
  
 Aşağıdaki tablo listesini yaygın olarak çalışırken sınıfları kullanan <xref:System.Xml.Xsl.XslTransform> ve XPath ve bunların işlevi.  
  
|Sınıf veya arabirim|İşlev|  
|------------------------|--------------|  
|<xref:System.Xml.XPath.XPathNavigator>|XPath sorgusu desteğinin yanı sıra bir mağaza üzerinden gezinmek için bir imleç stili modeli sağlayan bir API'dir. Temel alınan deposu düzenleme sağlamaz. Düzenleme için kullanmak <xref:System.Xml.XmlDocument> sınıfı.|  
|<xref:System.Xml.XPath.IXPathNavigable>|Sağlayan bir arabirimi olan bir `CreateNavigator` yönteme bir <xref:System.Xml.XPath.XPathNavigator> deposu için.|  
|<xref:System.Xml.XmlDocument>|Bu belgenin düzenlenmesi sağlar. Bunu uygulayan <xref:System.Xml.XPath.IXPathNavigable>, belge düzenleme senaryoları XSLT dönüştürmeleri nerede daha sonra gerekli izin verme. Daha fazla bilgi için bkz: [çok XmlDocument giriş](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md).|  
|<xref:System.Xml.XmlDataDocument>|Öğesinden türetilen <xref:System.Xml.XmlDocument>. İlişkisel arasında köprü ve XML dünyaları kullanarak bir <xref:System.Data.DataSet> üzerinde yapılandırılmış verilerin belirtilen eşlemeleri göre XML belgesi içindeki depolama en iyi duruma getirme <xref:System.Data.DataSet>. Bunu uygulayan <xref:System.Xml.XPath.IXPathNavigable>, burada XSLT dönüştürmeleri yapılabilir bir veritabanından ilişkisel veriler üzerinde senaryoları izin verme. Daha fazla bilgi için bkz: [ilişkisel veri ve ADO.NET XML tümleştirme](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).|  
|<xref:System.Xml.XPath.XPathDocument>|Bu sınıf en iyi hale getirildiği <xref:System.Xml.Xsl.XslTransform> işleme ve XPath sorguları ve onu bir salt okunur yüksek performanslı önbellek sağlar. Bunu uygulayan <xref:System.Xml.XPath.IXPathNavigable> ve XSLT dönüştürmeleri için kullanmayı tercih edilen deposudur.|  
|<xref:System.Xml.XPath.XPathNodeIterator>|Bu gezinti XPath düğüm kümeleri sağlar. Tüm XPath seçimi yöntemlere <xref:System.Xml.XPath.XPathNavigator> dönüş bir <xref:System.Xml.XPath.XPathNodeIterator>. Birden çok <xref:System.Xml.XPath.XPathNodeIterator> nesneleri her seçili kümesi düğümlerinin temsil eden aynı deponun üzerinde oluşturulabilir.|  
  
## <a name="msxml-xslt-extensions"></a>MSXML XSLT uzantıları  
 `msxsl:script` Ve `msxsl:node-set` işlevlerdir tarafından desteklenen yalnızca Microsoft XML Çekirdek Hizmetleri (MSXML) XSLT uzantılarını <xref:System.Xml.Xsl.XslTransform> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde yükleyen bir XSLT stil sayfası okur içine mydata.xml adlı bir dosya bir <xref:System.Xml.XPath.XPathDocument>ve biçimlendirilmiş çıktıyı konsola gönderme myStyleSheet.xsl adlı kurgusal bir dosyadaki veriler üzerinde dönüştürme gerçekleştirir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Xsl.XslTransform>  
 [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [XslTransform Sınıfında İsteğe Bağlı Davranışların Uygulanması](../../../../docs/standard/data/xml/implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)  
 [Dönüşümlerde XPathNavigator](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [Dönüşümlerde XPathNodeIterator](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [XslTransform’a XPathDocument Girişi](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [XslTransform’a XmlDataDocument Girişi](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [XslTransform’a XmlDocument Girişi](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
