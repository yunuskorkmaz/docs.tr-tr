---
title: msxsl:script Kullanan Betik Blokları
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1488fb6b7671acd86286bcac6fbfce8bee9429ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939585"
---
# <a name="script-blocks-using-msxslscript"></a>msxsl:script Kullanan Betik Blokları
<xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı ,`msxsl:script` öğesini kullanarak katıştırılmış betikleri destekler. Stil sayfası yüklendiğinde, tanımlanmış tüm işlevler Kod Belge Nesne Modeli (CodeDOM) tarafından Microsoft ara dili (MSIL) ile derlenir ve çalışma zamanında yürütülür. Katıştırılmış betik bloğundan oluşturulan derleme, stil sayfası için oluşturulan derlemeden ayrıdır.  
  
## <a name="enable-xslt-script"></a>XSLT betiğini etkinleştir  
 Katıştırılmış betikler için destek, <xref:System.Xml.Xsl.XslCompiledTransform> sınıf üzerinde isteğe bağlı bir XSLT ayarıdır. Komut dosyası desteği varsayılan olarak devre dışıdır. Betik <xref:System.Xml.Xsl.XsltSettings> desteğini etkinleştirmek için, <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> özelliği olarak `true` ayarlanmış bir nesne oluşturun ve nesneyi <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemine geçirin.  
  
> [!NOTE]
> XSLT betiği oluşturma yalnızca betik desteğine ihtiyacınız varsa ve tamamen güvenilir bir ortamda çalışıyorsanız etkinleştirilmelidir.  
  
## <a name="msxslscript-element-definition"></a>msxsl: betik öğesi tanımı  
 `msxsl:script` Öğesi, XSLT 1,0 önerisi için bir Microsoft uzantısıdır ve aşağıdaki tanıma sahiptir:  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 Ön ek, `urn:schemas-microsoft-com:xslt` ad alanı URI 'sine bağlanır. `msxsl` Stil sayfası, `xmlns:msxsl=urn:schemas-microsoft-com:xslt` ad alanı bildirimini içermelidir.  
  
 `language` Özniteliği isteğe bağlıdır. Değeri, gömülü kod bloğunun kod dilidir. Dil, <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> yöntemi kullanılarak uygun CodeDOM derleyicisi ile eşleştirilir. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı, uygun sağlayıcının makinede yüklü olduğunu varsayarak ve Machine. config dosyasının System. CodeDom bölümünde kayıtlı olan tüm Microsoft .net dillerini destekleyebilir. Bir `language` öznitelik belirtilmemişse, dil varsayılan olarak JScript olur. Dil adı büyük/küçük harfe duyarlı değildir, bu nedenle ' JavaScript ' ve ' JavaScript ' eşdeğerdir.  
  
 `implements-prefix` Özniteliği zorunludur. Bu öznitelik, bir ad alanını bildirmek ve betik bloğu ile ilişkilendirmek için kullanılır. Bu özniteliğin değeri, ad alanını temsil eden önekidir. Bu ön ek, bir stil sayfasında bir yerde tanımlanabilir.  
  
> [!NOTE]
> `msxsl:script` Öğesi kullanılırken, dilden bağımsız olarak betiğin bir CDATA bölümünün içine yerleştirilmesi önemle önerilir. Komut dosyası belirli bir dil için işleç, tanımlayıcı veya sınırlayıcılar içerebildiğinden, CDATA bölümünde yoksa, XML olarak yanlış yorumlanmakta olma olasılığı vardır. Aşağıdaki XML, kodun yerleştirilebileceği CDATA bölümünün bir şablonunu gösterir.  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a>Betik Işlevleri  
 İşlevler, `msxsl:script` öğesi içinde bildirilebilecek. Bir işlev bildirildiğinde, bir betik bloğunda bulunur. Stil sayfaları, her biri diğerinin bağımsız olarak çalışan birden çok betik bloğu içerebilir. Diğer bir deyişle, bir betik bloğunun içinde yürütüyorsunuz, aynı ad alanına ve aynı komut dosyası diline sahip olmak üzere bildirilmeden, başka bir betik bloğunda tanımladığınız bir işlevi çağıramadığınız anlamına gelir. Her bir betik bloğu kendi dilinde olabileceğinden ve blok söz konusu dil ayrıştırıcısının dilbilgisi kurallarına göre ayrıştırılacağından, kullanımda olan dil için doğru sözdizimini kullanmanızı öneririz. Örneğin, bir Microsoft C# komut dosyası bloğunda, C# açıklama sözdizimini kullanın.  
  
 Sağlanan bağımsız değişkenler ve işlevin dönüş değerleri herhangi bir türde olabilir. W3C XPath türleri ortak dil çalışma zamanı (CLR) türlerinin bir alt kümesi olduğundan, bir XPath türü olarak kabul etmeyen türler için tür dönüştürme gerçekleşir. Aşağıdaki tabloda karşılık gelen W3C türleri ve eşdeğer CLR türü gösterilmektedir.  
  
|W3C türü|CLR türü|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 CLR sayısal türleri öğesine <xref:System.Double>dönüştürülür. <xref:System.DateTime> Tür öğesine<xref:System.String>dönüştürülür. <xref:System.Xml.XPath.IXPathNavigable>türler öğesine <xref:System.Xml.XPath.XPathNavigator>dönüştürülür. **XPathNavigator []** , öğesine <xref:System.Xml.XPath.XPathNodeIterator>dönüştürüldü.  
  
 Diğer tüm türler bir hata oluşturur.  
  
### <a name="importing-namespaces-and-assemblies"></a>Ad alanları ve derlemeler içeri aktarılıyor  
 Sınıfı, varsayılan olarak `msxsl:script` öğesi tarafından desteklenen derleme ve ad alanları kümesini önceden tanımlar. <xref:System.Xml.Xsl.XslCompiledTransform> Ancak, derleme ve ad alanını `msxsl:script` bloğunda içeri aktararak önceden tanımlanmış listede olmayan bir ad alanına ait sınıfları ve üyeleri kullanabilirsiniz.  
  
#### <a name="assemblies"></a>Bütünleştirilmiş kodlar  
 Aşağıdaki iki derlemeye varsayılan olarak başvurulur:  
  
- System.dll  
  
- System.Xml.dll  
  
- Microsoft. VisualBasic. dll (komut dosyası dili VB olduğunda)  
  
 `msxsl:assembly` Öğesini kullanarak ek derlemeleri içeri aktarabilirsiniz. Bu, stil sayfası derlendiğinde derlemeyi içerir. `msxsl:assembly` Öğesi aşağıdaki tanıma sahiptir:  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 Öznitelik, derlemenin adını içerir `href` ve özniteliği derlemenin yolunu içerir. `name` Derleme adı "System. Data, Version = 2.0.3600.0, Culture = neutral, PublicKeyToken = b77a5c561934e089" gibi bir tam ad veya "System. Web" gibi kısa bir ad olabilir.  
  
#### <a name="namespaces"></a>Ad Alanları  
 Aşağıdaki ad alanları varsayılan olarak dahil edilmiştir:  
  
- Sistem  
  
- System.Collection  
  
- System.Text  
  
- System.Text.RegularExpressions  
  
- System.Xml  
  
- System.Xml.Xsl  
  
- System.Xml.XPath  
  
- Microsoft. VisualBasic (komut dosyası dili VB olduğunda)  
  
 `namespace` Özniteliğini kullanarak ek ad alanları için destek ekleyebilirsiniz. Öznitelik değeri, ad alanının adıdır.  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yarıçapı verilen bir dairenin çevresini hesaplamak için gömülü bir betiği kullanır.  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a>Number. xml  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a>Calc. Xsl  
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
