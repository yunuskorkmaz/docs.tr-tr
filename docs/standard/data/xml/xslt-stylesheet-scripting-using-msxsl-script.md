---
title: <msxsl:script> Kullanarak XSLT Stil Sayfası Betiğini Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
ms.openlocfilehash: 01e11ed62b0855b9027dfd7999f8b787c075028a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709679"
---
# <a name="xslt-stylesheet-scripting-using-msxslscript"></a>\<msxsl: script > kullanarak XSLT stil sayfası betiği oluşturma
<xref:System.Xml.Xsl.XslTransform> sınıfı, `script` öğesi kullanılarak gömülü komut dosyalarını destekler.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> sınıfı, .NET Framework 2,0 ' de kullanılmıyor. <xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz. Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 <xref:System.Xml.Xsl.XslTransform> sınıfı, `script` öğesi kullanılarak gömülü komut dosyalarını destekler. Stil sayfası yüklendiğinde, tanımlanmış tüm işlevler bir sınıf tanımına sarmalanarak Microsoft ara dili 'ne (MSIL) derlenir ve sonuç olarak performans kaybı olmaz.  
  
 `<msxsl:script>` öğesi aşağıda tanımlanmıştır:  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 Burada `msxsl` ad alanına `urn:schemas-microsoft-com:xslt`bir ön ektir.  
  
 `language` özniteliği zorunlu değildir, ancak belirtilmişse değerinin aşağıdakilerden biri olması gerekir: `C#`, `VB`, `JScript`, `JavaScript`, `VisualBasic`veya `CSharp`. Belirtilmemişse, dil varsayılan olarak JScript olur. `language-name`, büyük/küçük harfe duyarlı değildir, bu nedenle ' JavaScript ' ve ' JavaScript ' eşdeğerdir.  
  
 `implements-prefix` özniteliği zorunludur. Bu öznitelik, bir ad alanını bildirmek ve betik bloğu ile ilişkilendirmek için kullanılır. Bu özniteliğin değeri, ad alanını temsil eden önekidir. Bu ad alanı, bir stil sayfasında bir yerde tanımlanabilir.  
  
 `msxsl:script` öğesi `urn:schemas-microsoft-com:xslt`ad alanına ait olduğundan, stil sayfası, ad alanı bildirimi `xmlns:msxsl=urn:schemas-microsoft-com:xslt`içermelidir.  
  
 Betik çağıranın <xref:System.Security.Permissions.SecurityPermissionFlag> erişim izni yoksa, bir stil sayfasındaki betik hiçbir şekilde derlenmez ve <xref:System.Xml.Xsl.XslTransform.Load%2A> çağrısı başarısız olur.  
  
 Çağıranın `UnmanagedCode` izni varsa, betik derlenir, ancak izin verilen işlemler, yükleme zamanında sağlanan kanıta bağımlıdır.  
  
 Stil sayfasını yüklemek için <xref:System.Xml.XmlReader> veya <xref:System.Xml.XPath.XPathNavigator> alan <xref:System.Xml.Xsl.XslTransform.Load%2A> yöntemlerinden birini kullanıyorsanız, bağımsız değişkenlerinden biri olarak bir <xref:System.Security.Policy.Evidence> parametresi alan <xref:System.Xml.Xsl.XslTransform.Load%2A> aşırı yüklemeyi kullanmanız gerekir. Kanıt sağlamak için çağıranın betik derlemesi için `Evidence` sağlaması için <xref:System.Security.Permissions.SecurityPermissionFlag> iznine sahip olması gerekir. Çağıranın bu izni yoksa, `Evidence` parametresini `null`olarak ayarlayabilirler. Bu, komut dosyası bulursa <xref:System.Xml.Xsl.XslTransform.Load%2A> işlevinin başarısız olmasına neden olur. `ControlEvidence` izin, yalnızca son derece güvenilen koda verilmesi gereken çok güçlü bir izin olarak değerlendirilir.  
  
 Derlemeinizden kanıt almak için `this.GetType().Assembly.Evidence`kullanın. Bir Tekdüzen Kaynak tanımlayıcısından (URI) kanıt almak için `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`kullanın.  
  
 <xref:System.Xml.XmlResolver> olan ancak `Evidence`olmayan <xref:System.Xml.Xsl.XslTransform.Load%2A> Yöntemler kullanırsanız, derleme için güvenlik bölgesi varsayılan olarak tam güven olur. Daha fazla bilgi için bkz. <xref:System.Security.SecurityZone> ve [adlandırılmış Izin kümeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).  
  
 İşlevler `msxsl:script` öğesi içinde bildirilebilecek. Aşağıdaki tabloda, varsayılan olarak desteklenen ad alanları gösterilmektedir. Sınıfları listelenen ad alanları dışında kullanabilirsiniz. Ancak, bu sınıfların tam nitelikli olması gerekir.  
  
|Varsayılan ad alanları|Açıklama|  
|------------------------|-----------------|  
|Sistem|Sistem sınıfı.|  
|System.Collection|Koleksiyon sınıfları.|  
|System.Text|Metin sınıfları.|  
|System.Text.RegularExpressions|Normal ifade sınıfları.|  
|System.Xml|Çekirdek XML sınıfları.|  
|System.Xml.Xsl|XSLT sınıfları.|  
|System.Xml.XPath|XML Path Language (XPath) sınıfları.|  
|Microsoft. VisualBasic|Microsoft Visual Basic betikleri için sınıflar.|  
  
 Bir işlev bildirildiğinde, bir betik bloğunda bulunur. Stil sayfaları, her biri diğerinin bağımsız olarak çalışan birden çok betik bloğu içerebilir. Diğer bir deyişle, bir betik bloğunun içinde yürütüyorsunuz, aynı ad alanına ve aynı komut dosyası diline sahip olmak üzere bildirilmeden, başka bir betik bloğunda tanımladığınız bir işlevi çağıramadığınız anlamına gelir. Her bir betik bloğu kendi dilinde olabileceğinden ve blok söz konusu dil ayrıştırıcısının dilbilgisi kurallarına göre ayrıştırılacağından, kullanımda olan dil için doğru sözdizimini kullanmanız gerekir. Örneğin, bir C# betik bloğudur, bloğunda `<!-- an XML comment -->` bir XML açıklama düğümü kullanılması hatadır.  
  
 Sağlanan bağımsız değişkenler ve betik işlevleri tarafından tanımlanan dönüş değerleri World Wide Web Konsorsiyumu (W3C) XPath veya XSLT türlerinden biri olmalıdır. Aşağıdaki tabloda karşılık gelen W3C türleri, eşdeğer .NET Framework sınıfları (türü) ve W3C türünün bir XPath türü veya XSLT türü olup olmadığı gösterilmektedir.  
  
|Tür|Eşdeğer .NET Framework sınıfı (tür)|XPath türü veya XSLT türü|  
|----------|----------------------------------------------|-----------------------------|  
|Dize|System. String|{1&gt;XPath&lt;1}|  
|Boole değeri|System. Boolean|{1&gt;XPath&lt;1}|  
|Sayı|System. Double|{1&gt;XPath&lt;1}|  
|Sonuç ağacı parçası|System. xml. XPath. XPathNavigator|XSLT|  
|Düğüm kümesi|System.Xml.XPath.XPathNodeIterator|{1&gt;XPath&lt;1}|  
  
 Betik işlevi şu sayısal türlerden birini kullanıyorsa: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single veya Decimal, W3C XPath tür numarasıyla eşlenen Double olarak zorlanır. Tüm diğer türler `ToString` yöntemi çağırarak bir dizeye zorlanır.  
  
 Betik işlevi yukarıda belirtilenlerden farklı bir tür kullanıyorsa veya stil sayfası <xref:System.Xml.Xsl.XslTransform> nesnesine yüklendiğinde işlev derlenmezse, bir özel durum oluşturulur.  
  
 `msxsl:script` öğesi kullanılırken, dilden bağımsız olarak betiğin bir CDATA bölümünün içine yerleştirilmesi kesinlikle önerilir. Örneğin, aşağıdaki XML, kodunuzun yerleştirildiği CDATA bölümünün şablonunu gösterir.  
  
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
  
 Bu, ve işaretleri hariç olmadığından bir özel durum oluşturur. Belge XML olarak yüklenir ve `msxsl:script` öğesi etiketleri arasındaki metne özel bir işleme uygulanmaz.  
  
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
