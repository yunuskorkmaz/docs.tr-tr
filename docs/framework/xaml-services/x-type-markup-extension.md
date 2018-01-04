---
title: "x:Type İşaretleme Uzantısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
caps.latest.revision: "27"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4d645d5c953c0ff33435a5648024ace099455e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="xtype-markup-extension"></a>x:Type İşaretleme Uzantısı
CLR sağlayan <xref:System.Type> belirtilen bir XAML tür için temel alınan tür nesnesi.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı  
  
```xaml  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`prefix`|İsteğe bağlı. Varsayılan olmayan XAML ad uzayı eşleyen bir önek. Bir önek belirtme sık gerekli değildir. Açıklamalar bakın.|  
|`typeNameValue`|Gerekli. Tür adı için geçerli varsayılan XAML ad uzayı çözümlenebilir; veya belirtilen eşlenmiş öneki varsa `prefix` sağlanır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `x:Type` Biçimlendirme uzantısı benzer bir işlevi olan `typeof()` işlecinde [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] veya `GetType` işlecinde [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)].  
  
 `x:Type` Biçimlendirme uzantısı türü ele özellikleri için bir dize öğesinden dönüştürme davranış sağlayan <xref:System.Type>. Giriş XAML türüdür. Giriş XAML türü ve CLR çıkış arasındaki ilişkiyi <xref:System.Type> çıkış olan <xref:System.Type> olan <xref:System.Xaml.XamlType.UnderlyingType%2A> giriş <xref:System.Xaml.XamlType>, gerekli bakan sonra <xref:System.Xaml.XamlType> XAML şema içeriği ve göre<xref:System.Windows.Markup.IXamlTypeResolver>Hizmet bağlamı sağlar.  
  
 .NET Framework XAML hizmetlerinde bu biçimlendirme uzantısı işlenmesi tarafından tanımlanan <xref:System.Windows.Markup.TypeExtension> sınıfı.  
  
 Bazı özellikler belirli framework uygulamalarında alın <xref:System.Type> değeri doğrudan türünün adını kabul (tür dizesi değerini `Name`). Ancak, bu davranış uygulama karmaşık bir senaryo değildir. Örnekler için aşağıdaki "WPF kullanım notları" bölümüne bakın.  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Sonra sağlanan dize belirteci `x:Type` kimlik dizesi olarak atandığı <xref:System.Windows.Markup.TypeExtension.TypeName%2A> temel değer <xref:System.Windows.Markup.TypeExtension> uzantısı sınıfı. CLR türlerine dayanarak, .NET Framework XAML hizmetlerinde, varsayılan XAML şema içeriği bu özniteliğin değeri ya da altındadır <xref:System.Reflection.MemberInfo.Name%2A> istenen türde veya içeren <xref:System.Reflection.MemberInfo.Name%2A> varsayılan olmayan XAML ad uzayı için bir önek öncesinde eşleme.  
  
 `x:Type` Biçimlendirme uzantısı nesne öğesi sözdiziminde kullanılabilir. Bu durumda, değerini belirten <xref:System.Windows.Markup.TypeExtension.TypeName%2A> özelliği uzantıyı düzgün başlatmak için gereklidir.  
  
 `x:Type` Biçimlendirme uzantısı olarak ayrıntılı bir özniteliği de kullanılabilir; ancak bu kullanım tipik: `<``object``property``="{x:Type TypeName=``typeNameValue``}" .../>`  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>Varsayılan XAML Namespace ve tür eşlemesi  
 Varsayılan XAML ad uzayı WPF programlama için tipik XAML senaryoları için gereksinim duyduğunuz XAML türlerinin çoğu içerir; Bu nedenle, genellikle önekleri XAML tür değerleri başvururken önleyebilirsiniz. Özel bir derlemeyi ya da bir WPF derlemede var, ancak varsayılan XAML ad alanına eşlenmeyen bir CLR ad alanından olan türleri için bir tür başvuran varsa bir önek eşleme gerekebilir. Önekleri, XAML ad uzayları ve eşleme CLR ad alanları hakkında daha fazla bilgi için bkz: [XAML ad uzayları ve WPF XAML için Namespace eşleme](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
### <a name="type-properties-that-support-typename-as-string"></a>Özellikler bu destek Typename olarak-dizesi yazın  
 WPF destekleyen türünün bazı özellikleri değerini belirten etkinleştirmek teknikleri <xref:System.Type> gerektirmeden bir `x:Type` biçimlendirme uzantısı kullanımı. Bunun yerine, değer türü adları bir dize olarak belirtebilirsiniz. Bu öğeler örnekleri <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> ve <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>. Bu davranış desteği tür dönüştürücüleri veya işaretleme uzantıları aracılığıyla sağlanmadı. Bunun yerine, bu aracılığıyla uygulanan bir erteleme davranıştır <xref:System.Windows.FrameworkElementFactory>.  
  
 Silverlight benzer bir kuralı destekler. Aslında, Silverlight şu anda desteklemediği `{x:Type}` kendi XAML dil desteği ve kabul etmediği `{x:Type}` kullanımları Silverlight WPF XAML geçişi desteklemek için tasarlanmıştır birkaç durumlar dışında. Bu nedenle, dize olarak typename tüm Silverlight yerel özellik değerlendirmesi için yerleşik bir davranıştır burada bir <xref:System.Type> değerdir.  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 desteği sağlar. ek genel türleri ve özellik davranışını değiştiren `x:TypeArguments` ve `x:Type` bu desteği sağlamak için.  
  
-   `x:TypeArguments`ve ilişkili nesne öğesi genel nesne örneğini oluşturmada için kök başka öğelerde olabilir. Daha fazla bilgi için "XAML 2009" bölümüne bakın [x: TypeArguments yönergesi](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
-   XAML 2009 genel tür kısıtlaması biçimlendirmede belirtmek için bir söz dizimi destekler. Bu tarafından kullanılabilir `x:TypeArguments`, göre `x:Type`, veya iki özellik birlikte.  
  
-   Yük türünü kullanan belirli framework özellikleri örtük tür dönüştürme davranışını bu özelliği de ekler için XAML 2009 işlerken WPF XAML uygulama <xref:System.Type>.  
  
 WPF'de, ancak yalnızca gevşek XAML için (biçimlendirme-derlenmemiş XAML) XAML 2009 özellikleri kullanabilirsiniz. XAML biçimlendirme derlenmiş WPF ve XAML BAML form için şu anda desteklemediği XAML 2009 anahtar sözcükleri ve özellikler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Style>  
 [Stil ve Şablon Oluşturma](../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [XAML'ye Genel Bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [İşaretleme Uzantıları ve WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
