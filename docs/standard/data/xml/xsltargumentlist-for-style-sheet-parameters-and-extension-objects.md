---
title: Stil sayfası parametreleri ve uzantı nesneleri için XsltArgumentList
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 808d21ae0eabdc7502ef97facc3d45f2220883af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576815"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a>Stil sayfası parametreleri ve uzantı nesneleri için XsltArgumentList
<xref:System.Xml.Xsl.XsltArgumentList> Sınıfı Dönüşümleri (XSLT) parametreleri ve XSLT uzantısı nesneleri için Genişletilebilir Stil sayfası dili içerir. İçine geçirildiğinde <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi, bu parametreler ve uzantı nesneleri stil sayfalarını çağrılan.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Ve <xref:System.Xml.Xsl.XsltArgumentList> sınıfları ' te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Kullanarak XSLT dönüştürmeleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 <xref:System.Xml.Xsl.XsltArgumentList> Sınıfı XSLT parametreleri ve XSLT uzantısı nesneleri içerir. İçine geçirildiğinde <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi, bu parametreler ve uzantı nesneleri stil sayfalarını çağrılan.  
  
 Katıştırılmış bir komut dosyası kullanarak yerine bir nesne geçirme avantajları şunlardır:  
  
-   Daha iyi kapsülleme ve sınıfları kullanılmasını sağlar.  
  
-   Stil sayfaları, küçük ve daha rahat olmasını sağlar.  
  
-   Ad alanları kümesi içinde tanımlanan dışında ait sınıfları yöntemleri çağırma destekler desteklenen <xref:System> ad alanları.  
  
-   Sonuç ağaç parçaları kullanarak stil sayfası geçirilmesi destekler <xref:System.Xml.XPath.XPathNodeIterator>.  
  
## <a name="xslt-style-sheet-parameters"></a>XSLT stil sayfası parametreleri  
 XSLT parametreleri eklenir <xref:System.Xml.Xsl.XsltArgumentList> kullanarak <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemi. Bir tam adı ve ad alanı Tekdüzen Kaynak Tanımlayıcısı (URI) o anda parametre nesnesi ile ilişkilendirilmiş.  
  
 Parametre nesnesi, World Wide Web Konsorsiyumu (W3C) türüne karşılık gelmelidir. Aşağıdaki tabloda, karşılık gelen W3C türleri eşdeğer gösterilmektedir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sınıfları (tür) ve W3C türü bir XML Path dili (XPath) türü veya XSLT türü olup.  
  
|W3C türü|Eşdeğer .NET Framework sınıf (tür)|XPath türü veya XSLT türü|  
|--------------|----------------------------------------------|-----------------------------|  
|Dize|System.String|XPath|  
|Boole değeri|System.Boolean|XPath|  
|Sayı|System.Double|XPath|  
|Sonuç ağacı parçası|System.Xml.XPath.XPathNavigator|XSLT|  
|Düğüm kümesi|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 Parametre nesnesi yukarıdaki sınıflarından biri değilse, bunu çift veya dize için uygun şekilde zorlanır. Int16, UInt16, Int32, UInt32, Int64, UInt64, tek ve ondalık türleri için bir çift zorlanır. Tüm diğer türleri bir dizeye zorlanır kullanarak `ToString` yöntemi.  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a>XSLT parametre kullanmak üzere kullanıcı aşağıdakileri yapmalıdır:  
  
1.  Oluşturma bir <xref:System.Xml.Xsl.XsltArgumentList> ve kullanarak nesneleri eklemek <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.  
  
2.  Parametreleri stil sayfası içinden çağırın.  
  
3.  Geçirmek <xref:System.Xml.Xsl.XsltArgumentList> için <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> hesaplanan iskonto tarih tutmak için bir parametre oluşturmak için yöntemi. İndirim tarih sırası 20 gün olarak hesaplanır.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public class Sample  
  
   Private Const filename As String = "order.xml"  
   Private Const stylesheet As String = "discount.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Calculate the discount date.  
    Dim today As DateTime = DateTime.Now  
    Dim d As DateTime = today.AddDays(20)  
    xslArg.AddParam("discount", "", d.ToString())  
  
    'Create an XmlTextWriter to handle the output.  
    Dim writer As XmlTextWriter = New XmlTextWriter("orderout.xml", Nothing)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
  
    writer.Close()  
  
  End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "order.xml";  
   private const String stylesheet = "discount.xsl";  
  
   public static void Main() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Calculate the discount date.  
    DateTime today = DateTime.Now;  
    DateTime d = today.AddDays(20);  
    xslArg.AddParam("discount", "", d.ToString());  
  
    //Create an XmlTextWriter to handle the output.  
    XmlTextWriter writer = new XmlTextWriter("orderout.xml", null);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  }  
}  
```  
  
### <a name="input"></a>Giriş  
 Order.XML  
  
```xml  
<!--Represents a customer order-->  
<order>  
  <book ISBN='10-861003-324'>  
    <title>The Handmaid's Tale</title>  
    <price>19.95</price>  
  </book>  
  <cd ISBN='2-3631-4'>  
    <title>Americana</title>  
    <price>16.95</price>  
  </cd>  
</order>  
```  
  
 discount.xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:param name="discount"/>  
  <xsl:template match="/">  
    <order>  
      <xsl:variable name="sub-total" select="sum(//price)"/>  
      <total><xsl:value-of select="$sub-total"/></total>  
      15% discount if paid by: <xsl:value-of select="$discount"/>  
    </order>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a>Çıkış  
  
```xml  
<order>  
   <total>36.9</total>   
   15% discount if paid by: 5/6/2001 5:01:15 PM   
</order>  
```  
  
## <a name="xslt-extension-objects"></a>XSLT uzantısı nesneleri  
 XSLT uzantısı nesnelerinin eklenir <xref:System.Xml.Xsl.XsltArgumentList> kullanarak <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi. Bir tam adı ve ad alanı URI'si o anda uzantısı nesne ile ilişkili.  
  
 Bir nesne eklendiğinde, çağıranın <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> güvenlik ilkesinde tam olarak güvenilir olması gerekir. Arayan yarı güvenilmiyorsa eklenmesi başarısız olur.  
  
 Bir nesne başarıyla eklendi ancak, yürütme başarılı olacağını garanti etmez. Zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çağrıldığında, izin verilen bulgu göre hesaplanır <xref:System.Xml.Xsl.XslTransform.Load%2A> zaman ve izin kümesi için tüm dönüştürme süreci atanır. Uzantı nesnesi kümesinde bulunamadı izinleri gerektiren bir eylem başlatmak çalışırsa, bir özel durum oluşur.  
  
 Uzantı nesnelerden döndürülen veri türleri dört temel XPath veri türlerinin sayısı, dize, Boolean ve düğüm kümesi vardır.  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a>XSLT uzantı nesnesi kullanmak için kullanıcı aşağıdakileri yapmanız gerekir:  
  
1.  Oluşturma bir <xref:System.Xml.Xsl.XsltArgumentList> ve uzantı nesnesini kullanarak eklemek <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.  
  
2.  Stil sayfası uzantısı nesnesinden çağırır.  
  
3.  Geçirmek <xref:System.Xml.Xsl.XsltArgumentList> için <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, RADIUS verilen dairenin çevresi hesaplar.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "circle.xsl"  
  
   Public Shared Sub Main()  
        Dim test As Sample = New Sample  
   End Sub  
  
  Public Sub New()  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Add an object to calculate the circumference of the circle.  
    Dim obj As Calculate = New Calculate  
    xslArg.AddExtensionObject("urn:myObj", obj)  
  
    'Create an XmlTextWriter to output to the console.  
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
    writer.Close()  
  
  End Sub  
  
  'Calculates the circumference of a circle given the radius.  
  Public Class Calculate  
  
    Private circ As double = 0  
  
    Public Function Circumference(radius As Double) As Double  
       circ = Math.PI*2*radius  
       Return circ  
    End Function  
  End Class  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "circle.xsl";  
  
   public static void Main() {  
  
        Sample test = new Sample();  
    }  
  
  public Sample() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Add an object to calculate the circumference of the circle.  
    Calculate obj = new Calculate();  
    xslArg.AddExtensionObject("urn:myObj", obj);  
  
    //Create an XmlTextWriter to output to the console.  
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  
  }  
  
  //Calculates the circumference of a circle given the radius.  
  public class Calculate{  
  
    private double circ = 0;  
  
    public double Circumference(double radius){  
       circ = Math.PI*2*radius;  
       return circ;  
    }  
  }  
}  
```  
  
### <a name="input"></a>Giriş  
 Number.XML  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>    
```  
  
 Circle.xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:myObj="urn:myObj">  
  
  <xsl:template match="data">  
  <circles>  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="myObj:Circumference(radius)"/>          
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a>Çıkış  
 `<circles xmlns:myObj="urn:myObj">`  
  
 `<circle>`  
  
 `<radius>12</radius>`  
  
 `<circumference>75.398223686155</circumference>`  
  
 `</circle>`  
  
 `<circle>`  
  
 `<radius>37.5</radius>`  
  
 `<circumference>235.61944901923448</circumference>`  
  
 `</circle>`  
  
 `</circles>`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
