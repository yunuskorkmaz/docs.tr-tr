---
title: Stil Sayfası Parametreleri ve Genişletme Nesneleri için XsltArgumentList
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6209df7d226d7e3acb938801d1fb77afbe1249b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026615"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a>Stil Sayfası Parametreleri ve Genişletme Nesneleri için XsltArgumentList
<xref:System.Xml.Xsl.XsltArgumentList> Sınıfı içeren Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) parametreleri ve XSLT genişletme nesneleri için. Yöntemlere geçirilen zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi, bu parametreleri ve genişletme nesneleri stil sayfası içinden çağrılan.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Ve <xref:System.Xml.Xsl.XsltArgumentList> sınıflardır eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Kullanarak XSLT dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 <xref:System.Xml.Xsl.XsltArgumentList> Sınıfı XSLT parametreleri ve XSLT genişletme nesneleri içerir. Yöntemlere geçirilen zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi, bu parametreleri ve genişletme nesneleri stil sayfası içinden çağrılan.  
  
 Katıştırılmış bir betik kullanmak yerine bir nesne geçirme avantajları şunlardır:  
  
- Daha iyi kapsülleme ve sınıfları kullanılmasını sağlar.  
  
- Stil sayfaları, daha küçük ve daha rahat olmasını sağlar.  
  
- Desteklenen dizi içinde tanımlanan dışındaki ad alanlarına ait sınıfların yöntemleri çağırma destekler <xref:System> ad alanları.  
  
- Sonucu ağacı parçalarını kullanımını ile stil sayfası geçirerek destekler <xref:System.Xml.XPath.XPathNodeIterator>.  
  
## <a name="xslt-style-sheet-parameters"></a>XSLT stil sayfası parametreleri  
 XSLT parametreleri eklenir <xref:System.Xml.Xsl.XsltArgumentList> kullanarak <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemi. Bir tam adı ve ad alanı Tekdüzen Kaynak Tanımlayıcısı (URI), o anda parametresi nesnesi ile ilişkilendirilmiş.  
  
 Parametre nesnesine bir World Wide Web Consortium (W3C) türüne karşılık gelmelidir. Aşağıdaki tabloda karşılık gelen W3C türleri, eşdeğer gösterir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sınıfları (tür) ve W3C türün bir XML yolu dil (XPath) türü veya XSLT türü olup.  
  
|W3C türü|Eşdeğeri .NET Framework sınıfı (tür)|XPath türü veya XSLT türü|  
|--------------|----------------------------------------------|-----------------------------|  
|Dize|System.String|XPath|  
|Boole değeri|System.Boolean|XPath|  
|Sayı|System.Double|XPath|  
|Sonuç ağacı parçası|System.Xml.XPath.XPathNavigator|XSLT|  
|Düğüm kümesi|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 Parametre nesnesine yukarıdaki sınıflardan biri değilse, bunu Double veya dizesi için uygun şekilde zorlanır. Int16, Uınt16, Int32, Uınt32, Int64, UInt64, tek ve ondalık türleri için bir Double zorlanır. Diğer tüm türlerin bir dizeye zorlanır kullanarak `ToString` yöntemi.  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a>XSLT parametresini kullanmak için kullanıcı şunları yapmanız gerekir:  
  
1. Oluşturma bir <xref:System.Xml.Xsl.XsltArgumentList> ve kullanarak nesne eklemek <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.  
  
2. Stil sayfası parametreleri çağırın.  
  
3. Geçirmek <xref:System.Xml.Xsl.XsltArgumentList> için <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemi hesaplanan indirimi tarihini tutmak için bir parametre oluşturun. İndirimi tarihini, sipariş tarihi 20 gün olarak hesaplanır.  
  
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
  
## <a name="xslt-extension-objects"></a>XSLT Genişletme Nesneleri  
 XSLT genişletme nesneleri eklenir <xref:System.Xml.Xsl.XsltArgumentList> kullanarak <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi. Bir tam adı ve ad alanı URI o anda uzantısı nesnesi ile ilişkilendirilmiş.  
  
 Bir nesne eklendiğinde, çağıran <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> güvenlik ilkesinde tam olarak güvenilir olması gerekir. Çağıranın kısmen güvenilen ise, ayrıca başarısız olur.  
  
 Nesne başarıyla eklendi ancak bunu yürütme başarılı olacağını garanti etmez. Zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çağrıldığında, izin verilen kanıt karşı hesaplandığı <xref:System.Xml.Xsl.XslTransform.Load%2A> zaman ve izin kümesi için tüm dönüştürme süreci atanır. Kümede bulunamadı izinleri gerektiren bir eylem başlatmak bir uzantı nesnesi çalışırsa, bir özel durum oluşturulur.  
  
 Uzantı nesnelerinden döndürülen veri türleri, sayı, dize, Boolean ve düğüm kümesinin dört temel XPath veri türleri biridir.  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a>XSLT uzantı nesnesini kullanmak için kullanıcı aşağıdakileri yapmanız gerekir:  
  
1. Oluşturma bir <xref:System.Xml.Xsl.XsltArgumentList> ve uzantısını kullanarak nesne eklemek <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.  
  
2. Stil sayfası uzantısı nesneden çağırın.  
  
3. Geçirmek <xref:System.Xml.Xsl.XsltArgumentList> için <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, RADIUS verilmiş bir daire çevresi hesaplar.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
