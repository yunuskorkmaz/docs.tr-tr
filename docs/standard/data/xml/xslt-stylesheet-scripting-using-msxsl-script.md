---
title: 'XSLT stil sayfası komut dosyalarını kullanarak &lt;msxsl: Script&gt;'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68c98b3b4effbe7cea1a3c4443d2222e6bbcd43c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45964796"
---
# <a name="xslt-stylesheet-scripting-using-ltmsxslscriptgt"></a>XSLT stil sayfası komut dosyalarını kullanarak &lt;msxsl: Script&gt;
<xref:System.Xml.Xsl.XslTransform> Sınıfı destekler kullanarak katıştırılmış betik `script` öğesi.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 <xref:System.Xml.Xsl.XslTransform> Sınıfı destekler kullanarak katıştırılmış betik `script` öğesi. Stil sayfası yüklendiğinde, herhangi bir tanımlı işlevlere Microsoft Ara dili (MSIL) bir sınıf tanımı içinde sarmalanmış tarafından derlenir ve sonuç olarak performans kaybı olmadan sahip.  
  
 `<msxsl:script>` Öğesi aşağıda tanımlanmıştır:  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 Burada `msxsl` bir önek ad alanına bağlı `urn:schemas-microsoft-com:xslt`.  
  
 `language` Özniteliği zorunlu değildir, ancak belirtilirse, değeri aşağıdakilerden biri olmalıdır: C#, VB, JScript, JavaScript, VisualBasic veya CSharp. Belirtilmezse, dil için JScript Varsayılanları. `language-name` 'JavaScript' ve 'javascript' eşdeğer olacak şekilde duyarlı değildir.  
  
 `implements-prefix` Özniteliği zorunludur. Bu öznitelik, bir ad alanı bildirin ve komut dosyası bloğu ile ilişkilendirmek için kullanılır. Bu özniteliğin değeri ad alanını temsil eden önekidir. Bu ad herhangi bir yerde bir stil sayfası içinde tanımlanabilir.  
  
 Çünkü `msxsl:script` öğenin ait olduğu ad alanına `urn:schemas-microsoft-com:xslt`, stil sayfası, ad alanı bildirimi içermelidir `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.  
  
 Komut dosyasını çağıran yoksa <xref:System.Security.Permissions.SecurityPermissionFlag> bir stil sayfası betik hiçbir zaman derleyeceği sonra erişim izni ve çağrısı <xref:System.Xml.Xsl.XslTransform.Load%2A> başarısız olur.  
  
 Çağıranın varsa `UnmanagedCode` izni, kod derlenir, ancak izin verilen işlemler yükleme zamanında sağlanan kanıt bağlıdır.  
  
 Aşağıdakilerden birini kullanıyorsanız <xref:System.Xml.Xsl.XslTransform.Load%2A> ele yöntemleri bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XPath.XPathNavigator> stil sayfası yüklemek için kullanmanız gerekir <xref:System.Xml.Xsl.XslTransform.Load%2A> alan aşırı yüklemesini bir <xref:System.Security.Policy.Evidence> parametre bağımsız değişkenlerinden biri olarak. Kanıt sağlamak için çağıranın olmalıdır <xref:System.Security.Permissions.SecurityPermissionFlag> izin vermesini `Evidence` betik derleme için. Çağıranın bu izni yok. ardından ayarlayabilirler `Evidence` parametresi `null`. Bu neden <xref:System.Xml.Xsl.XslTransform.Load%2A> betik bulursa başarısız işlev. `ControlEvidence` İzni yüksek derecede güvenilen koda verilen yalnızca çok güçlü bir izin olarak kabul edilir.  
  
 Kanıt derlemenizden almak için kullanın `this.GetType().Assembly.Evidence`. Bir Tekdüzen Kaynak Tanımlayıcısı (URI) öğesinden kanıt sağlamak için kullanın `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.  
  
 Kullanırsanız <xref:System.Xml.Xsl.XslTransform.Load%2A> ele yöntemleri bir <xref:System.Xml.XmlResolver> ancak hiçbir `Evidence`, derleme için güvenlik bölgesi varsayılan olarak tam güven için. Daha fazla bilgi için <xref:System.Security.SecurityZone> ve [adlandırılmış izin kümeleri](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).  
  
 İşlevler içinde bildirilebilir `msxsl:script` öğesi. Aşağıdaki tabloda, varsayılan olarak desteklenen ad alanlarını gösterir. Listelenen ad alanlarını dışında sınıfları kullanabilirsiniz. Ancak, bu sınıflar, tam olarak nitelenmiş olmalıdır.  
  
|Varsayılan ad alanları|Açıklama|  
|------------------------|-----------------|  
|Sistem|Sistem sınıfı.|  
|System.Collection|Koleksiyon sınıfları.|  
|System.Text|Metin sınıflar.|  
|System.Text.RegularExpressions|Normal ifade sınıfları.|  
|System.Xml|Çekirdek XML sınıfları.|  
|System.Xml.Xsl|XSLT sınıflar.|  
|System.Xml.XPath|XML Path Language (XPath) sınıflar.|  
|Microsoft.VisualBasic|Microsoft Visual Basic komut dosyası için sınıflar sağlar.|  
  
 Bildirilen bir işlev, bir komut dosyası bloğu içinde yer alır. Stil sayfaları, birden çok komut dosyası blokları, diğerinden bağımsız çalışan her içerebilir. Bir betik bloğu içinde yürütülen, aynı ad ve aynı komut dosyası dili bildirildiği sürece başka bir betik bloğu içinde tanımlanan bir işlev çağrısı yapamazsınız anlamına gelir. Çünkü her betik bloğu kendi dilinde olabilir ve blok o dil ayrıştırıcı dilbilgisi kurallara göre ayrıştırılır kullanılan dilin doğru sözdizimini kullanmanız gerekir. Bir C# betik bloğu içinde varsa, örneğin, bir XML açıklama düğümü kullanmak için bir hata ise `<!-- an XML comment -->` bloğundaki.  
  
 Sağlanan bağımsız değişkenler ve dönüş değerleri betik işlevleri tarafından tanımlanan World Wide Web Consortium (W3C) XPath veya XSLT türlerinden biri olması gerekir. Aşağıdaki tablo W3C türleri karşılık gelen gösterir (tür) eşdeğeri .NET Framework sınıfları ve W3C türü olup olmadığını bir XPath türü veya XSLT türü.  
  
|Tür|Eşdeğeri .NET Framework sınıfı (tür)|XPath türü veya XSLT türü|  
|----------|----------------------------------------------|-----------------------------|  
|Dize|System.String|XPath|  
|Boole değeri|System.Boolean|XPath|  
|Sayı|System.Double|XPath|  
|Sonuç ağacı parçası|System.Xml.XPath.XPathNavigator|XSLT|  
|Düğüm kümesi|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 Betik işlevi aşağıdaki sayısal türlerinden birini kullanır,: Int16, Uınt16, Int32, Uınt32, Int64, UInt64, tek veya ondalık, bunlar zorunlu için çift, hangi W3C XPath türü sayıya eşler. Diğer tüm türlerin bir dizeye çağırarak zorlanır `ToString` yöntemi.  
  
 Betik işlevi kullanır yukarıda belirtenlere dışında bir tür veya işlev derlenemiyor varsa, stil sayfası yüklenir içine <xref:System.Xml.Xsl.XslTransform> nesnesi, bir özel durum harekete geçirilir.  
  
 Kullanırken `msxsl:script` öğesi kesinlikle önerilir dili ne olursa olsun kodun içindeki CDATA bölümüne yerleştirilmesi. Örneğin, aşağıdaki XML kodunuzu nereye yerleştirileceğini CDATA bölümü şablonunu gösterir.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 Operatörler, tanımlayıcılar ya da belirli bir dil için sınırlayıcılar XML olarak yanlış olası olduğundan tüm betik içeriği bir CDATA bölümde yerleştirilmesi önerilir. Aşağıdaki örnek komut dosyasında mantıksal AND işlecinin kullanımını gösterir.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp>  
    public string book(string abc, string xyz)  
    {  if ((abc== abc)&&(abc== xyz)) return bar+xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 Bu, kodlarına kaçış için özel durum oluşturur. Belge XML olarak yüklenir ve hiçbir özel olarak değerlendirilmesi arasındaki metni uygulanan `msxsl:script` öğesi etiketleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir katıştırılmış betik, RADIUS verilmiş bir daire çevresi hesaplamak için kullanır.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
