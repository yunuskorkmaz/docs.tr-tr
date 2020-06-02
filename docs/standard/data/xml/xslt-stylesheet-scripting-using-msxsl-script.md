---
title: <msxsl:script> Kullanarak XSLT Stil Sayfası Betiğini Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
ms.openlocfilehash: aef2471a375469f7cd4dff27084b305ef9394d5e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291974"
---
# <a name="xslt-stylesheet-scripting-using-msxslscript"></a>Kullanarak XSLT stil sayfası betiği oluşturma\<msxsl:script>
<xref:System.Xml.Xsl.XslTransform>Sınıfı, öğesini kullanarak gömülü komut dosyalarını destekler `script` .  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor. Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> . Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .  
  
 <xref:System.Xml.Xsl.XslTransform>Sınıfı, öğesini kullanarak gömülü komut dosyalarını destekler `script` . Stil sayfası yüklendiğinde, tanımlanmış tüm işlevler bir sınıf tanımına sarmalanarak Microsoft ara dili 'ne (MSIL) derlenir ve sonuç olarak performans kaybı olmaz.  
  
 `<msxsl:script>`Öğe aşağıda tanımlanmıştır:  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 , `msxsl` ad alanına göre bir ön ek olur `urn:schemas-microsoft-com:xslt` .  
  
 `language`Özniteliği zorunlu değildir, ancak belirtilmişse değeri şunlardan biri olmalıdır: `C#` , `VB` ,, `JScript` `JavaScript` , `VisualBasic` veya `CSharp` . Belirtilmemişse, dil varsayılan olarak JScript olur. `language-name`Büyük/küçük harfe duyarlı değildir, bu nedenle ' JavaScript ' ve ' JavaScript ' eşdeğerdir.  
  
 `implements-prefix`Özniteliği zorunludur. Bu öznitelik, bir ad alanını bildirmek ve betik bloğu ile ilişkilendirmek için kullanılır. Bu özniteliğin değeri, ad alanını temsil eden önekidir. Bu ad alanı, bir stil sayfasında bir yerde tanımlanabilir.  
  
 `msxsl:script`Öğesi ad alanına ait olduğundan `urn:schemas-microsoft-com:xslt` , stil sayfası ad alanı bildirimini içermelidir `xmlns:msxsl=urn:schemas-microsoft-com:xslt` .  
  
 Komut dosyası çağıranın <xref:System.Security.Permissions.SecurityPermissionFlag> erişim izni yoksa, bir stil sayfasındaki betiği hiçbir şekilde derlenmez ve çağrısı <xref:System.Xml.Xsl.XslTransform.Load%2A> başarısız olur.  
  
 Çağıranın `UnmanagedCode` izni varsa, komut dosyası derlenir, ancak izin verilen işlemler, yükleme zamanında sağlanan kanıta bağımlıdır.  
  
 <xref:System.Xml.Xsl.XslTransform.Load%2A> <xref:System.Xml.XmlReader> Stil sayfasını yüklemek veya içeren yöntemlerden birini kullanıyorsanız <xref:System.Xml.XPath.XPathNavigator> , <xref:System.Xml.Xsl.XslTransform.Load%2A> <xref:System.Security.Policy.Evidence> bağımsız değişkenlerinden biri olarak bir parametre alan aşırı yüklemeyi kullanmanız gerekir. Kanıt sağlamak için çağıranın <xref:System.Security.Permissions.SecurityPermissionFlag> betik derlemesini sağlama izni olması gerekir `Evidence` . Çağıranın bu izni yoksa, `Evidence` parametresini olarak ayarlayabilirler `null` . Bu, <xref:System.Xml.Xsl.XslTransform.Load%2A> komut dosyası bulursa işlevin başarısız olmasına neden olur. `ControlEvidence`İzin, yalnızca son derece güvenilen koda verilmesi gereken çok güçlü bir izin olarak değerlendirilir.  
  
 Derlemeinizden kanıt almak için kullanın `this.GetType().Assembly.Evidence` . Bir Tekdüzen Kaynak tanımlayıcısından (URI) kanıt almak için kullanın `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)` .  
  
 <xref:System.Xml.Xsl.XslTransform.Load%2A>Ancak Hayır alan yöntemler kullanıyorsanız <xref:System.Xml.XmlResolver> `Evidence` , derleme için güvenlik bölgesi varsayılan olarak tam güven olur. Daha fazla bilgi için bkz <xref:System.Security.SecurityZone> . ve [adlandırılmış izin kümeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).  
  
 İşlevler, öğesi içinde bildirilebilecek `msxsl:script` . Aşağıdaki tabloda, varsayılan olarak desteklenen ad alanları gösterilmektedir. Sınıfları listelenen ad alanları dışında kullanabilirsiniz. Ancak, bu sınıfların tam nitelikli olması gerekir.  
  
|Varsayılan ad alanları|Description|  
|------------------------|-----------------|  
|Sistem|Sistem sınıfı.|  
|System.Collection|Koleksiyon sınıfları.|  
|System.Text|Metin sınıfları.|  
|System.Text.RegularExpressions|Normal ifade sınıfları.|  
|System.Xml|Çekirdek XML sınıfları.|  
|System. xml. Xsl|XSLT sınıfları.|  
|System.Xml.XPath|XML Path Language (XPath) sınıfları.|  
|Microsoft. VisualBasic|Microsoft Visual Basic betikleri için sınıflar.|  
  
 Bir işlev bildirildiğinde, bir betik bloğunda bulunur. Stil sayfaları, her biri diğerinin bağımsız olarak çalışan birden çok betik bloğu içerebilir. Diğer bir deyişle, bir betik bloğunun içinde yürütüyorsunuz, aynı ad alanına ve aynı komut dosyası diline sahip olmak üzere bildirilmeden, başka bir betik bloğunda tanımladığınız bir işlevi çağıramadığınız anlamına gelir. Her bir betik bloğu kendi dilinde olabileceğinden ve blok söz konusu dil ayrıştırıcısının dilbilgisi kurallarına göre ayrıştırılacağından, kullanımda olan dil için doğru sözdizimini kullanmanız gerekir. Örneğin, bir C# komut dosyası bloğunda, bloğunda bir XML açıklama düğümü kullanılması hatadır `<!-- an XML comment -->` .  
  
 Sağlanan bağımsız değişkenler ve betik işlevleri tarafından tanımlanan dönüş değerleri World Wide Web Konsorsiyumu (W3C) XPath veya XSLT türlerinden biri olmalıdır. Aşağıdaki tabloda karşılık gelen W3C türleri, eşdeğer .NET Framework sınıfları (türü) ve W3C türünün bir XPath türü veya XSLT türü olup olmadığı gösterilmektedir.  
  
|Tür|Eşdeğer .NET Framework sınıfı (tür)|XPath türü veya XSLT türü|  
|----------|----------------------------------------------|-----------------------------|  
|Dize|System. String|XPath|  
|Boole|System. Boolean|XPath|  
|Sayı|System. Double|XPath|  
|Sonuç ağacı parçası|System. xml. XPath. XPathNavigator|XSLT|  
|Düğüm kümesi|System. xml. XPath. XPathNodeIterator|XPath|  
  
 Betik işlevi şu sayısal türlerden birini kullanıyorsa: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single veya Decimal, W3C XPath tür numarasıyla eşlenen Double olarak zorlanır. Tüm diğer türler, yöntemi çağırarak bir dizeye zorlanır `ToString` .  
  
 Betik işlevi yukarıda bahsedilen olanlardan farklı bir tür kullanıyorsa veya işlev, nesne içine yüklendiğinde işlev derlenmezse, <xref:System.Xml.Xsl.XslTransform> bir özel durum oluşturulur.  
  
 `msxsl:script`Öğesi kullanılırken, dilden bağımsız olarak betiğin BIR CDATA bölümünün içine yerleştirilmesi kesinlikle önerilir. Örneğin, aşağıdaki XML, kodunuzun yerleştirildiği CDATA bölümünün şablonunu gösterir.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 Belirli bir dilin işleçleri, tanımlayıcıları veya sınırlandırıcılarının XML olarak yanlış yorumlanmasına sahip olması nedeniyle, tüm betik içeriğinin bir CDATA bölümüne yerleştirilmesi kesinlikle önerilir. Aşağıdaki örnek, komut dosyasında mantıksal AND işlecinin kullanımını gösterir.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    public string book(string abc, string xyz)  
    {  
        if ((abc == bar) && (abc == xyz)) return bar + xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 Bu, ve işaretleri hariç olmadığından bir özel durum oluşturur. Belge XML olarak yüklenir ve öğe etiketleri arasındaki metne özel bir işleme uygulanmaz `msxsl:script` .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yarıçapı verilen bir dairenin çevresini hesaplamak için gömülü bir betiği kullanır.  
  
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
  
   public static void Main()  
   {  
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
  
 Calc. Xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius)  
     {  
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
  
## <a name="output"></a>Çıktı  
  
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

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](xsltransform-class-implements-the-xslt-processor.md)
