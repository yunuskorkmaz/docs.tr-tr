---
title: "Komut dosyası blokları kullanarak msxsl: Script"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2e127fb02725d11e62c45157b4e45327fc9f1ace
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="script-blocks-using-msxslscript"></a>Komut dosyası blokları kullanarak msxsl: Script
<xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı kullanarak katıştırılmış komut dosyalarını destekler `msxsl:script` öğesi. Stil sayfası yüklendiğinde, tanımlı hiçbir işlev Microsoft Ara dili (MSIL) kod belge nesne modeli (CodeDOM) tarafından derlenir ve çalışma zamanı sırasında yürütülür. Katıştırılmış betik bloğundan oluşturulan derleme için stil sayfası oluşturulan derleme daha ayrıdır.  
  
## <a name="enable-xslt-script"></a>XSLT betik etkinleştir  
 Katıştırılmış komut dosyaları için destek olduğundan isteğe bağlı bir XSLT ayar <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Komut dosyası desteği varsayılan olarak devre dışıdır. Komut dosyası desteğini etkinleştirmek için Oluştur bir <xref:System.Xml.Xsl.XsltSettings> nesnesi ile <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> özelliğini `true` ve nesneyi geçirin <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi.  
  
> [!NOTE]
>  XSLT betik oluşturma yalnızca komut dosyası desteği gerektirir ve tam güvenilen bir ortamda çalışıyorsanız etkinleştirilmelidir.  
  
## <a name="msxslscript-element-definition"></a>msxsl: Script öğesi tanımı  
 `msxsl:script` Öğesi XSLT 1.0 öneri için bir Microsoft uzantısı olup aşağıdaki tanımını içerir:  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 `msxsl` Öneki bağlı `urn:schemas-microsoft-com:xslt` ad alanı URI'si. Stil sayfası içermelidir `xmlns:msxsl=urn:schemas-microsoft-com:xslt` ad alanı bildirimi.  
  
 `language` Özniteliği isteğe bağlıdır. Değerini katıştırılmış kod bloğu kod dilidir. Dil uygun CodeDOM derleyici kullanmaya eşlendi <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> yöntemi. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı, uygun sağlayıcısı makineye yüklenir ve machine.config dosyasının system.codedom bölümünde kayıtlı olduğu varsayılarak, herhangi bir Microsoft .NET dil destekleyebilir. Varsa bir `language` özniteliği belirtilmezse, dil, JScript için varsayılan olarak belirlenir. Dil adı büyük küçük harfe duyarlı değil 'JavaScript' ve 'javascript' eşdeğerdir.  
  
 `implements-prefix` Özniteliği zorunludur. Bu öznitelik, bir ad alanı bildirimini ve betik bloğu ile ilişkilendirmek için kullanılır. Bu özniteliğin değeri ad alanını temsil eden önekidir. Bu ön ek bir stil sayfanızda bir yerde tanımlanabilir.  
  
> [!NOTE]
>  Kullanırken `msxsl:script` öğesi öneririz dil, bağımsız olarak komut içinde CDATA bölümü yerleştirilmesi. CDATA bölüm içinde bulunmuyorsa betik operatörler, tanımlayıcılar ya da belirli bir dil için sınırlayıcılar içerebileceği için XML olarak yanlış yorumlayan, olasılığı vardır. Aşağıdaki XML kodunu nereye yerleştirileceğini CDATA bölümünün bir şablon gösterir.  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a>Komut dosyası işlevleri  
 İşlevler içinde bildirilebilir `msxsl:script` öğesi. Bir işlev bildirirken bir betik bloğu içinde yer alır. Stil sayfaları, birden çok komut dosyası blokları, diğerinden bağımsız çalışan her içerebilir. Bir komut dosyası bloğunun içine çalıştırıldığında, aynı ad ve aynı komut dosyası dili bildirilir sürece, başka bir betik bloğu içinde tanımlanan bir işlev çağıramazsınız anlamına gelir. Çünkü her komut dosyası bloğunun kendi dilde olabilir ve bu dil Ayrıştırıcıyı dilbilgisi kurallarına göre blok ayrıştırılır kullanımda dilin doğru sözdizimi kullanmanızı öneririz. Microsoft C# betik bloğunda varsa, örneğin, C# açıklama sözdizimini kullanın.  
  
 Sağlanan bağımsız değişkenler ve işlevinin dönüş değerleri herhangi bir türde olabilir. W3C XPath türleri ortak dil çalışma zamanı (CLR) türlerinin bir alt olduğundan, tür dönüştürme XPath tür olarak kabul edilmez türlerinde gerçekleşir. Aşağıdaki tabloda, karşılık gelen W3C türleri ve eşdeğer CLR türü gösterilmektedir.  
  
|W3C türü|CLR türü|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 CLR sayısal türler dönüştürülür <xref:System.Double>. <xref:System.DateTime> Türü için dönüştürülür <xref:System.String>. <xref:System.Xml.XPath.IXPathNavigable>türlerine dönüştürülür <xref:System.Xml.XPath.XPathNavigator>. **XPathNavigator []** dönüştürülür <xref:System.Xml.XPath.XPathNodeIterator>.  
  
 Tüm diğer türleri hata atar.  
  
### <a name="importing-namespaces-and-assemblies"></a>Ad alanları ve derlemeler içeri aktarma  
 <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı önceden belirler derlemeler ve varsayılan olarak tarafından desteklenen ad alanları kümesini `msxsl:script` öğesi. Ancak, sınıflar ve üyeleri derlemeyi ve ad alanında içeri aktararak önceden tanımlanmış listede olmayan bir ad alanına ait kullanabilirsiniz `msxsl:script` bloğu.  
  
#### <a name="assemblies"></a>Derlemeler  
 Aşağıdaki iki derlemeler varsayılan olarak başvurulur:  
  
-   System.dll  
  
-   System.Xml.dll  
  
-   (Komut dosyası dili VB olduğunda) Microsoft.VisualBasic.dll içinde  
  
 Kullanarak ek derlemeler aktarabilirsiniz `msxsl:assembly` öğesi. Bu, stil sayfası derlendiğinde derleme içerir. `msxsl:assembly` Öğesi aşağıdaki tanım var:  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 `name` Özniteliği içeren derlemenin adını ve `href` özniteliği içeren derleme yolu. Derleme adı bir tam ad gibi olabilir "System.Data, sürüm 2.0.3600.0, Culture = neutral, PublicKeyToken = b77a5c561934e089", veya "System.Web" gibi kısa bir ad.  
  
#### <a name="namespaces"></a>Ad Alanları  
 Şu ad alanlarından varsayılan olarak eklenir:  
  
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
 Aşağıdaki örnek komut dosyası katıştırılmış kendi RADIUS verilen dairenin çevresi hesaplamak için kullanır.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XSLT dönüştürmeleri](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [Dinamik kaynak kodu oluşturma ve derleme](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
