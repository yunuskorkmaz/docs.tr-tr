---
title: 'Komut dosyası blokları msxsl: Script kullanan'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4d7dee9ebaed20970f715026661c29aae701289
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44062942"
---
# <a name="script-blocks-using-msxslscript"></a>Komut dosyası blokları msxsl: Script kullanan
<xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı kullanarak katıştırılmış betikleri destekler `msxsl:script` öğesi. Stil sayfası yüklendiğinde, herhangi bir tanımlı işlevlere kod belge nesne modeli (CodeDOM) tarafından derlenmiş Microsoft Ara dili (MSIL) ve çalışma zamanı sırasında yürütülür. Katıştırılmış betik bloğundan oluşturulan derleme, stil sayfası için oluşturulan derlemesinden ayrıdır.  
  
## <a name="enable-xslt-script"></a>XSLT betik etkinleştir  
 Gömülü betikler için destek etkin isteğe bağlı bir XSLT ayar <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Betik desteği, varsayılan olarak devre dışıdır. Betik desteği etkinleştirmek için oluşturun bir <xref:System.Xml.Xsl.XsltSettings> nesnesi ile <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> özelliğini `true` ve nesneyi geçirin <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi.  
  
> [!NOTE]
>  XSLT betik yalnızca betik desteği gerektiriyorsa ve tam olarak güvenilen bir ortamda çalışıyorsanız etkinleştirilmelidir.  
  
## <a name="msxslscript-element-definition"></a>msxsl: Script öğesi tanımı  
 `msxsl:script` Öğesi XSLT 1.0 öneri bir Microsoft uzantısıdır ve aşağıdaki tanımları içerir:  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 `msxsl` İçin bağlı öneki `urn:schemas-microsoft-com:xslt` ad alanı URI. Stil sayfası içermelidir `xmlns:msxsl=urn:schemas-microsoft-com:xslt` ad alanı bildirimi.  
  
 `language` İsteğe bağlı öznitelik. Değerini, gömülü kod bloğunun kod dilidir. Dil uygun CodeDOM derleyici kullanmayı eşlenir <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> yöntemi. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı uygun sağlayıcıyı makineye yüklenir ve machine.config dosyasının system.codedom bölümünde kayıtlı olduğundan, herhangi bir Microsoft .NET dil destekleyebilir. Varsa bir `language` özniteliği belirtilmezse, dil Varsayılanları JScript için. Dil adı büyük küçük harfe duyarlı değil 'JavaScript' ve 'javascript' eşdeğerdir.  
  
 `implements-prefix` Özniteliği zorunludur. Bu öznitelik, bir ad alanı bildirin ve komut dosyası bloğu ile ilişkilendirmek için kullanılır. Bu özniteliğin değeri ad alanını temsil eden önekidir. Bu ön ek bir yerde bir stil sayfası içinde tanımlanabilir.  
  
> [!NOTE]
>  Kullanırken `msxsl:script` öğesi öneririz, diline bakılmaksızın komut içindeki CDATA bölümüne yerleştirilmesi. Bir CDATA bölümde yer bulunmuyorsa betik operatörler, tanımlayıcılar ya da belirli bir dil için sınırlayıcılar içerebileceği için XML olarak yanlış olasılığı vardır. Aşağıdaki XML kodu nereye yerleştirilmesi CDATA bölümünün bir şablon gösterir.  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a>Betik işlevleri  
 İşlevler içinde bildirilebilir `msxsl:script` öğesi. Bildirilen bir işlev, bir komut dosyası bloğu içinde yer alır. Stil sayfaları, birden çok komut dosyası blokları, diğerinden bağımsız çalışan her içerebilir. Bir betik bloğu içinde yürütülen, aynı ad ve aynı komut dosyası dili bildirildiği sürece başka bir betik bloğu içinde tanımlanan bir işlev çağrısı yapamazsınız anlamına gelir. Her komut dosyası bloğu kendi dilinde olabilir ve blok o dil ayrıştırıcı dilbilgisi kurallara göre ayrıştırılır çünkü dili kullanmak için doğru sözdizimi kullanmanızı öneririz. Örneğin, bir Microsoft C# betik bloğu içinde varsa, C# yorum sözdizimini kullanın.  
  
 Sağlanan bağımsız değişkenler ve dönüş değerleri işlevi herhangi bir türde olabilir. W3C XPath türlerde ortak dil çalışma zamanı (CLR) türlerinin bir alt kümesi olduğundan, tür dönüştürme bir XPath türü olmasını dikkate alınmaz türleri üzerinde gerçekleşir. Aşağıdaki tablo W3C türleri ve karşılık gelen ve eşdeğer CLR türü gösterir.  
  
|W3C türü|CLR türü|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 CLR sayısal türleri dönüştürülür <xref:System.Double>. <xref:System.DateTime> Türüne dönüştürülür <xref:System.String>. <xref:System.Xml.XPath.IXPathNavigable> türleri dönüştürülür <xref:System.Xml.XPath.XPathNavigator>. **XPathNavigator []** dönüştürülür <xref:System.Xml.XPath.XPathNodeIterator>.  
  
 Diğer tüm türlerin bir hata atar.  
  
### <a name="importing-namespaces-and-assemblies"></a>Ad alanları ve derlemeler alınıyor  
 <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı önceden belirler, derlemeleri ve varsayılan olarak tarafından desteklenen ad alanları kümesi `msxsl:script` öğesi. Ancak, sınıflar ve üyeler derlemenin ve ad alanındaki içeri aktararak önceden tanımlanmış listede olmayan bir ad alanına ait kullanabilirsiniz `msxsl:script` blok.  
  
#### <a name="assemblies"></a>Derlemeleri  
 Varsayılan olarak aşağıdaki iki derlemelerini başvurulan:  
  
-   System.dll  
  
-   System.Xml.dll  
  
-   (Komut dosyası dili VB olduğunda) Microsoft.VisualBasic.dll içinde  
  
 Ek bütünleştirilmiş kodları kullanarak içeri aktarabilirsiniz `msxsl:assembly` öğesi. Bu, stil sayfası derlendiğinde derleme içerir. `msxsl:assembly` Öğesinin aşağıdaki tanımı:  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 `name` Özniteliği, derlemenin adını içerir ve `href` özniteliği derleme yolunu içerir. Derleme adı gibi tam bir ad olabilir "System.Data, sürüm 2.0.3600.0, Culture = neutral, PublicKeyToken = b77a5c561934e089", veya "System.Web" gibi kısa bir ad.  
  
#### <a name="namespaces"></a>Ad Alanları  
 Aşağıdaki ad alanları, varsayılan olarak dahil edilmiştir:  
  
-   Sistem  
  
-   System.Collection  
  
-   System.Text  
  
-   System.Text.RegularExpressions  
  
-   System.Xml  
  
-   System.Xml.Xsl  
  
-   System.Xml.XPath  
  
-   (Komut dosyası dili VB olduğunda) Microsoft.VisualBasic  
  
 Ek ad alanlarını kullanma için destek ekleyebilirsiniz `namespace` özniteliği. Öznitelik değeri, ad alanının adıdır.  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir katıştırılmış betik, RADIUS verilmiş bir daire çevresi hesaplamak için kullanır.  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a>Number.XML  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a>CALC.xsl  
 [!code-xml[XSLT_Script#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/calc.xsl#3)]  
  
### <a name="output"></a>Çıkış  
  
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

- [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)  
- [Dinamik Kaynak Kodu Oluşturma ve Derleme](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
