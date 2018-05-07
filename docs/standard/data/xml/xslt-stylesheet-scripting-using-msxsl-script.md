---
title: 'Komut dosyası stil XSLT kullanarak &lt;msxsl: Script&gt;'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5b1fb13e33f759c44e090a9294548c224e10344e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="xslt-stylesheet-scripting-using-ltmsxslscriptgt"></a>Komut dosyası stil XSLT kullanarak &lt;msxsl: Script&gt;
<xref:System.Xml.Xsl.XslTransform> Sınıfı destekler kullanarak katıştırılmış komut dosyası `script` öğesi.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır'te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil sayfası dili kullanarak Dönüşümleri (XSLT) dönüştürmeleri için gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 <xref:System.Xml.Xsl.XslTransform> Sınıfı destekler kullanarak katıştırılmış komut dosyası `script` öğesi. Stil sayfası yüklendiğinde, tanımlı hiçbir işlev Microsoft Ara dili (MSIL) bir sınıf tanımı Sarmalanan tarafından derlenir ve performans kaybı sonuç olarak sahip.  
  
 `<msxsl:script>` Öğesi aşağıda tanımlanmıştır:  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 Burada `msxsl` bir önek ad alanına bağlı `urn:schemas-microsoft-com:xslt`.  
  
 `language` Özniteliği zorunlu değildir, ancak belirtildiyse, değeri şunlardan biri olmalıdır: C#, VB, JScript, JavaScript, Visualbasic'tir veya CSharp. Belirtilmezse, dil için JScript varsayılan olur. `language-name` 'JavaScript' ve 'javascript' eşdeğer; bu nedenle, küçük harf duyarlıdır değil.  
  
 `implements-prefix` Özniteliği zorunludur. Bu öznitelik, bir ad alanı bildirimini ve betik bloğu ile ilişkilendirmek için kullanılır. Bu özniteliğin değeri ad alanını temsil eden önekidir. Bu ad, herhangi bir yerde bir stil sayfanızda tanımlanabilir.  
  
 Çünkü `msxsl:script` öğenin ait olduğu ad alanına `urn:schemas-microsoft-com:xslt`, stil sayfası ad alanı bildirimi içermelidir `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.  
  
 Komut dosyasını çağıran yoksa <xref:System.Security.Permissions.SecurityPermissionFlag> erişim izni, stil sayfasında komut dosyası hiçbir zaman derleme sonra ve çağrısı <xref:System.Xml.Xsl.XslTransform.Load%2A> başarısız olur.  
  
 Arayan varsa `UnmanagedCode` izni, komut dosyasını derler, ancak izin verilen işlemler, yükleme zamanında sağlanan kanıt bağlıdır.  
  
 Aşağıdakilerden birini kullanıyorsanız, <xref:System.Xml.Xsl.XslTransform.Load%2A> ele yöntemleri bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XPath.XPathNavigator> stil sayfası yüklemek için kullanmanız gerekir <xref:System.Xml.Xsl.XslTransform.Load%2A> alan aşırı bir <xref:System.Security.Policy.Evidence> parametre bağımsız değişkenlerinden biri olarak. Kanıt için arayan olmalıdır <xref:System.Security.Permissions.SecurityPermissionFlag> tedarik izni `Evidence` komut dosyası derleme için. Çağıranın bu izne sahip değil sonra ayarlayabilirsiniz `Evidence` parametresi `null`. Bu neden <xref:System.Xml.Xsl.XslTransform.Load%2A> komut dosyası bulursa, başarısız işlev. `ControlEvidence` İzni yalnızca yüksek oranda güvenilir kodu verilmelidir çok güçlü bir izin olarak kabul edilir.  
  
 Kanıt, derlemesinden almak için `this.GetType().Assembly.Evidence`. Bir Tekdüzen Kaynak Tanımlayıcısı (URI) gelen kanıt almak için `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.  
  
 Kullanırsanız <xref:System.Xml.Xsl.XslTransform.Load%2A> ele yöntemleri bir <xref:System.Xml.XmlResolver> ancak hiçbir `Evidence`, güvenlik bölgesi derleme için varsayılan olarak tam güven. Daha fazla bilgi için bkz: <xref:System.Security.SecurityZone> ve [adlandırılmış izin kümeleri](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).  
  
 İşlevler içinde bildirilebilir `msxsl:script` öğesi. Aşağıdaki tabloda, varsayılan olarak desteklenen ad alanlarını gösterir. Listelenen ad alanlarını dışında sınıflarını kullanabilirsiniz. Ancak, bu sınıfların tam olarak nitelenmiş olmalıdır.  
  
|Varsayılan ad alanları|Açıklama|  
|------------------------|-----------------|  
|Sistem|Sistem sınıfı.|  
|System.Collection|Koleksiyon sınıfları.|  
|System.Text|Metin sınıflar.|  
|System.Text.RegularExpressions|Normal ifade sınıfları.|  
|System.Xml|Çekirdek XML sınıfları.|  
|System.Xml.Xsl|XSLT sınıflar.|  
|System.Xml.XPath|XML Path dili (XPath) sınıfları.|  
|Microsoft.VisualBasic|Microsoft Visual Basic komut dosyası için sınıflar.|  
  
 Bir işlev bildirirken bir betik bloğu içinde yer alır. Stil sayfaları, birden çok komut dosyası blokları, diğerinden bağımsız çalışan her içerebilir. Bir komut dosyası bloğunun içine çalıştırıldığında, aynı ad ve aynı komut dosyası dili bildirilir sürece, başka bir betik bloğu içinde tanımlanan bir işlev çağıramazsınız anlamına gelir. Her komut dosyası bloğunun kendi dilde olabilir ve bu dil Ayrıştırıcıyı dilbilgisi kurallarına göre blok ayrıştırılır olduğundan, kullanılan dil için doğru sözdizimini kullanmanız gerekir. C# betik bloğunda varsa, örneğin, ardından bir XML açıklama düğümü kullanılacak hatadır `<!-- an XML comment -->` bloğundaki.  
  
 Sağlanan bağımsız değişkenler ve dönüş değerleri komut dosyası işlevleri tarafından tanımlanan World Wide Web Konsorsiyumu (W3C) XPath veya XSLT türlerinden biri olması gerekir. Aşağıdaki tabloda W3C türleri karşılık gelen gösterir (tür) eşdeğer .NET Framework sınıfları ve W3C türü olup olmadığını bir XPath türü veya XSLT türü.  
  
|Tür|Eşdeğer .NET Framework sınıf (tür)|XPath türü veya XSLT türü|  
|----------|----------------------------------------------|-----------------------------|  
|Dize|System.String|XPath|  
|Boole değeri|System.Boolean|XPath|  
|Sayı|System.Double|XPath|  
|Sonuç ağacı parçası|System.Xml.XPath.XPathNavigator|XSLT|  
|Düğüm kümesi|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 Betik işlevi aşağıdaki sayısal türlerinden birini kullanır,: Int16, UInt16, Int32, UInt32, Int64, UInt64, tek veya ondalık, bunlar zorunlu için çift, hangi W3C XPath türü sayıya eşler. Tüm diğer türleri çağırarak bir dizeye zorlanır `ToString` yöntemi.  
  
 Yukarıda belirtilen dışındaki bir türü betik işlevi kullanır veya işlev derlenmez varsa ne zaman stil sayfası yüklendiği içine <xref:System.Xml.Xsl.XslTransform> nesnesi, bir özel durum oluşur.  
  
 Kullanırken `msxsl:script` öğesi, kesinlikle önerilir dil, bağımsız olarak komut içinde CDATA bölümü yerleştirilmesi. Örneğin, aşağıdaki XML kodunuzu nereye yerleştirileceğini CDATA bölümünün şablonu gösterir.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 Operatörler, tanımlayıcılar ya da belirli bir dil için sınırlayıcılar XML olarak yanlış yorumlayan olası olduğundan tüm betik içeriği CDATA bölümünde yerleştirilmesi önerilir. Aşağıdaki örnek komut dosyasında mantıksal ve işlecini kullanımını göstermektedir.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp>  
    public string book(string abc, string xyz)  
    {  if ((abc== abc)&&(abc== xyz)) return bar+xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 Ve işaretlerini kaçışlı değil çünkü bu bir özel durum oluşturur. Belge XML olarak yüklenir ve özel bir işlemden arasındaki metni uygulanan `msxsl:script` öğe etiketleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek komut dosyası katıştırılmış kendi RADIUS verilen dairenin çevresi hesaplamak için kullanır.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "calc.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XmlTextWriter to output to the console.               
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
    writer.Formatting = Formatting.Indented  
  
    'Transform the file.  
    xslt.Transform(doc, Nothing, writer, Nothing)  
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
   private const String filename = "number.xml";  
   private const String stylesheet = "calc.xsl";  
  
   public static void Main() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XmlTextWriter to output to the console.               
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting = Formatting.Indented;  
  
    //Transform the file.  
    xslt.Transform(doc, null, writer, null);  
    writer.Close();  
  }   
}  
```  
  
## <a name="input"></a>Giriş  
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
  
 CALC.xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius){  
       double pi = 3.14;  
       double circ = pi*radius*2;  
       return circ;  
     }  
      ]]>  
   </msxsl:script>  
  
  <xsl:template match="data">    
  <circles>  
  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="user:circumference(radius)"/>   
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a>Çıkış  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>    
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
