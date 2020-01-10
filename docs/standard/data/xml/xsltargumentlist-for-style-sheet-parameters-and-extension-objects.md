---
title: Stil Sayfası Parametreleri ve Genişletme Nesneleri için XsltArgumentList
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
ms.openlocfilehash: 5cd733d557dabe66145fdbb848c473411d63c62b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709627"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a>Stil Sayfası Parametreleri ve Genişletme Nesneleri için XsltArgumentList
<xref:System.Xml.Xsl.XsltArgumentList> sınıfı, dönüşümler (XSLT) parametreleri ve XSLT uzantı nesneleri için Genişletilebilir Stil sayfası dili içerir. <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemine geçirildiğinde, bu parametreler ve uzantı nesneleri stil sayfalarından çağrılabilir.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> ve <xref:System.Xml.Xsl.XsltArgumentList> sınıfları .NET Framework 2,0 ' de kullanılmıyor. <xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanarak XSLT dönüşümleri gerçekleştirebilirsiniz. Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 <xref:System.Xml.Xsl.XsltArgumentList> sınıfı XSLT parametrelerini ve XSLT uzantısı nesnelerini içerir. <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemine geçirildiğinde, bu parametreler ve uzantı nesneleri stil sayfalarından çağrılabilir.  
  
 Bir katıştırılmış betik kullanmak yerine bir nesne geçirmenin avantajları aşağıda verilmiştir:  
  
- Sınıfların daha iyi kapsüllemesini ve yeniden kullanılmasını sağlar.  
  
- Stil sayfalarının daha küçük ve sürdürülebilir olmasını sağlar.  
  
- Desteklenen <xref:System> ad alanları kümesi içinde tanımlananlardan farklı ad alanlarına ait sınıflarda çağırma yöntemlerini destekler.  
  
- <xref:System.Xml.XPath.XPathNodeIterator>kullanımı ile, sonuç ağacı parçalarının stil sayfasına geçirilmesini destekler.  
  
## <a name="xslt-style-sheet-parameters"></a>XSLT stil sayfası parametreleri  
 XSLT parametreleri, <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemi kullanılarak eklenir. Tam ad ve ad alanı Tekdüzen Kaynak tanımlayıcısı (URI), parametre nesnesiyle ilişkili zamanda ilişkilendirilir.  
  
 Parameter nesnesi bir World Wide Web Konsorsiyumu (W3C) türüne karşılık gelmelidir. Aşağıdaki tablo, karşılık gelen W3C türlerini, eşdeğer .NET Framework sınıfları (türü) ve W3C türünün bir XML Path Language (XPath) türü ya da XSLT türü olup olmadığını gösterir.  
  
|W3C türü|Eşdeğer .NET Framework sınıfı (tür)|XPath türü veya XSLT türü|  
|--------------|----------------------------------------------|-----------------------------|  
|Dize|System. String|{1&gt;XPath&lt;1}|  
|Boole değeri|System. Boolean|{1&gt;XPath&lt;1}|  
|Sayı|System. Double|{1&gt;XPath&lt;1}|  
|Sonuç ağacı parçası|System. xml. XPath. XPathNavigator|XSLT|  
|Düğüm kümesi|System.Xml.XPath.XPathNodeIterator|{1&gt;XPath&lt;1}|  
  
 Parametre nesnesi yukarıdaki sınıflardan biri değilse, uygun şekilde bir Double veya String öğesine zorlanır. Int16, UInt16, Int32, UInt32, Int64, UInt64, tek ve ondalık türler Double 'a zorlanır. Tüm diğer türler `ToString` yöntemi kullanılarak bir dizeye zorlanır.  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a>XSLT parametresini kullanmak için, kullanıcının şunları yapması gerekir:  
  
1. <xref:System.Xml.Xsl.XsltArgumentList> oluşturun ve <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>kullanarak nesneleri ekleyin.  
  
2. Stil sayfasından parametreleri çağırın.  
  
3. <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoduna geçirin.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir hesaplanan indirim tarihini tutacak bir parametre oluşturmak için <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemini kullanır. İndirim tarihi, sipariş tarihinden itibaren 20 gün olacak şekilde hesaplanır.  
  
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
 Order. xml  
  
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
  
 Discount. Xsl  
  
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
  
## <a name="xslt-extension-objects"></a>XSLT Genişletme Nesneleri  
 XSLT uzantı nesneleri <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi kullanılarak eklenir. Tam ad ve ad alanı URI 'SI, o zaman uzantı nesnesiyle ilişkilendirilir.  
  
 Bir nesne eklendiğinde <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> çağıranın güvenlik ilkesinde tam olarak güvenilir olması gerekir. Arayan yarı güvenilir ise, ekleme başarısız olur.  
  
 Bir nesne başarıyla eklenirse, yürütmenin başarılı olacağını garanti etmez. <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çağrıldığında izinler, <xref:System.Xml.Xsl.XslTransform.Load%2A> zamanında verilen kanıtla karşılaştırılır ve bu izin kümesi tüm dönüştürme işlemine atanır. Uzantı nesnesi, küme içinde bulunamayan izinleri gerektiren bir eylem başlatmaya çalışırsa, bir özel durum oluşturulur.  
  
 Uzantı nesnelerinden döndürülen veri türleri, sayı, dize, Boolean ve düğüm kümesinin dört temel XPath veri türünden biridir.  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a>XSLT Uzantı nesnesini kullanmak için, kullanıcının şunları yapması gerekir:  
  
1. <xref:System.Xml.Xsl.XsltArgumentList> oluşturun ve <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>kullanarak Uzantı nesnesini ekleyin.  
  
2. Uzantı nesnesini stil sayfasından çağırın.  
  
3. <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoduna geçirin.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, yarıçapı verilen bir dairenin çevresini hesaplar.  
  
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
  public class Calculate {  
  
    private double circ = 0;  
  
    public double Circumference(double radius){  
       circ = Math.PI*2*radius;  
       return circ;  
    }  
  }  
}  
```  
  
### <a name="input"></a>Giriş  
 Number. xml  
  
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
  
 Circle. Xsl  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
