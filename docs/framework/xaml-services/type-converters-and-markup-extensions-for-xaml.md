---
title: XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services
- XAML [XAML Services], value converters
- XAML [XAML Services], markup extension services
- value converters for XAML [XAML Services]
- XAML [XAML Services], service context
ms.assetid: db07a952-05ce-4aa4-b6f9-aac7397d0326
ms.openlocfilehash: 0c9cb7e87416860dda98df0da967ffbc070bc270
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565869"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları
Tür dönüştürücüleri ve İşaretleme uzantıları Nesne grafiği bileşenleri oluşturmak için XAML türü sistemleri ve XAML yazıcılarının kullanan iki tekniklerle aynıdır. Bazı özellikleri paylaşır rağmen tür dönüştürücüleri ve İşaretleme uzantıları farklı bir XAML düğüm akış gösterilir. Bu belgede kümesi, tür dönüştürücüleri, biçimlendirme uzantıları ve benzer yapıları bazen topluca için değer dönüştürücüler bilinir.  
  
<a name="value_converters"></a>   
## <a name="value-converters"></a>Değer dönüştürücüler  
 XAML'de, değer dönüştürücüler çeşitli senaryolar için kullanılır. Aşağıdaki liste, değer dönüştürücüler farklı türde XAML'de gösterir:  
  
-   tür dönüştürücü  
  
-   İşaretleme uzantısı  
  
-   Değer seri hale getirici  
  
-   İlgili sınıfı veya mantığı için XAML metin sözdizimi sağlayan destek sınıfı  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Tür dönüştürücüleri  
 .NET Framework XAML hizmetlerinde tanımında tür dönüştürücüleri CLR türetilen sınıflardır <xref:System.ComponentModel.TypeConverter> sınıfı. <xref:System.ComponentModel.TypeConverter> Microsoft .NET Framework XAML yokken olan bir sınıftır. Özellik windows ve metin tabanlı benzer düzenleme metaphors için destek için özgün amacı olan [!INCLUDE[TLA2#tla_ide](../../../includes/tla2sharptla-ide-md.md)] özellikleri. .NET Framework XAML giriş kullanan <xref:System.ComponentModel.TypeConverter> metin sözdizimini (olarak bir öznitelik değeri ya da XAML değer düğümü bulundu) bir nesnesine dönüştürmek için. <xref:System.ComponentModel.TypeConverter> Ayrıca bir nesne değeri metin sözdizimi için seri hale getirmek için kullanılabilir. <xref:System.ComponentModel.TypeConverter> Ayrıca Windows Presentation Foundation (WPF) ve Windows Communication Foundation (WCF) önceki çerçeveye özel XAML uygulamalarında kullanıldı. Hakkında daha fazla bilgi için <xref:System.ComponentModel.TypeConverter> XAML'de bkz [XAML genel bakış için tür dönüştürücüleri](../../../docs/framework/xaml-services/type-converters-for-xaml-overview.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>İşaretleme uzantıları  
 Öğesinden türetilen sınıflar .NET Framework XAML hizmetlerinde uygulamasında biçimlendirme uzantıları <xref:System.Windows.Markup.MarkupExtension> sınıfı. Biçimlendirme uzantıları, XAML dili tarafından kaynaklanan bu formdaki bir kavramıdır. Biçimlendirme uzantısı, mantığını sağlamak için bir hizmet sınıfına çağırır Genişletilebilir kaçış dizisi şöyle olarak düşünebilirsiniz. Biçimlendirme bakımından XAML işlemcileri Evrensel biçimlendirme uzantısı, bir metin dizesindeki açılış ayracı ({}) ile başlayan bir metin dizisi tarafından farkındayız.  
  
 Biçimlendirme uzantıları tür dönüştürücüleri farklı. Tür dönüştürücüleri genellikle türleri veya üyeleri ile ilişkilendirilir. Bir nesne grafik oluşturma olduğunda çağrılır veya bir seri hale getirme bu varlıkların ile ilişkili metin sözdizimini karşılaşır.  
  
 Biçimlendirme uzantıları, tek bir destek hizmeti sınıf ile ilişkili ancak herhangi bir üye değer için uygulanabilir. (Ancak, kasıtlı olarak kullanımı belirli üyeleri veya hedef türleri, hizmet bağlamı kullanarak kısıtlamak için biçimlendirme uzantısı uygulayabilirsiniz.) Biçimlendirme uzantıları türü dönüştürücü ilişkilendirmesi geçersiz kılabilirsiniz. Veya bir metin sözdizimini desteklemek değil üyeleri için bir öznitelik değeri belirtmek için kullanabilirsiniz.  
  
 XAML biçimlendirme uzantısı uygulama modeli hakkında daha fazla bilgi için bkz: [işaretleme uzantılarına genel bakış XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Markup.MarkupExtension> Ve <xref:System.Windows.Markup.ValueSerializer> türleridir hem de <xref:System.Windows.Markup> ad alanı ve de <xref:System.Xaml> ad alanı. Bu bu tür aksi dizeyi içeren CLR ad alanları doldurmak WPF ya da Windows Forms teknolojiler için belirli göstermez `Windows`. <xref:System.Windows.Markup.MarkupExtension> ve <xref:System.Windows.Markup.ValueSerializer> System.Xaml derlemede ve belirli framework bağımlılık sahiptir. CLR ad alanı içinde bu tür var [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] ve CLR ad alanındaki kalır [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] başvuruları varolan WPF projelerindeki yeni önlemek için. Daha fazla bilgi için bkz: [geçirilen türler WPF gelen System.XAML'ye](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md).  
  
<a name="value_serializers"></a>   
## <a name="value-serializers"></a>Değer serileştiricileri  
 A <xref:System.Windows.Markup.ValueSerializer> bir nesne bir dizeye dönüştürmek için optimize edilmiş bir özel tür dönüştürücü. A <xref:System.Windows.Markup.ValueSerializer> XAML değil uygulayabilir için `ConvertFrom` hiç yöntemi. A <xref:System.Windows.Markup.ValueSerializer> uygulama hizmetleri benzer bir şekilde alacağı bir <xref:System.ComponentModel.TypeConverter> uygulaması. Sanal yöntemler için bir giriş sağlama `context` parametresi. `context` Parametredir türü <xref:System.Windows.Markup.IValueSerializerContext>, devralan <xref:System.IServiceProvider> arabirim ve sahip bir <xref:System.IServiceProvider.GetService%2A> yöntemi.  
  
 XAML tür sistemi ve seri hale getirme için XAML düğüm çevrim işleme kullanan XAML yazan uygulamaları için bir tür veya üye ile ilişkili değer dönüştürücüsü kendi tarafından bildirilen <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> özelliği. Anlamı sıralamanızı gerçekleştirmek XAML yazarları için ise bir <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> ve <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> var, tür dönüştürücüsünü yükleme yolu için kullanılması gereken ve değer seri hale getirici kaydetme için kullanılması gereken yolu. Varsa <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> var ancak <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> olan `null`, türü dönüştürücü de kaydetme kullanılır yolu.  
  
<a name="other_value_converters"></a>   
## <a name="other-value-converters"></a>Diğer değer dönüştürücüler  
 Değer dönüştürücüsü tür dönüştürücüsünü veya bir işaretleme uzantısı belirli desenlerini genişletilebilir. Ancak, bu özelleştirme de .NET Framework XAML Hizmetleri tarafından sağlanan gibi XAML tür sistemi yeniden tanımlama gerektirir. Varolan XAML tür sistemi Beyanları ve raporlama sistemleri için tür dönüştürücüleri ve İşaretleme uzantıları değeri serileştiricileri ancak özel formlar değeri dönüştürme için vardır. Özel değer dönüştürücüler oluşturmak istiyorsanız, kullanmak <xref:System.Xaml.Schema.XamlValueConverter%601> türü.  
  
<a name="type_converters_and_markup_extensions_in_combination"></a>   
## <a name="type-converters-and-markup-extensions-in-combination"></a>Birlikte tür dönüştürücüleri ve İşaretleme uzantıları  
 Biçimlendirme uzantıları ve tür dönüştürücüleri XAML farklı durumlarda kullanılır. Bağlam için işaretleme uzantısı kullanımları kullanılabilir olsa da, burada biçimlendirme uzantısı genellikle değerdir sağlar özellikleri türü dönüştürme davranışını biçimlendirme uzantısı uygulamalarında işaretlenmemiştir. Diğer bir deyişle, biçimlendirme uzantısı bir metin dizesi olarak döndürür olsa bile, `ProvideValue` çıkışı, belirli özellik ya da özellik değeri türü uygulanan olarak bu dize türü dönüştürme davranışını başvurulmaz. Genellikle, bir dize işlemek ve bir nesne türü dönüştürücü olmadan söz konusu dönmek için biçimlendirme uzantısı amacı içindir.  
  
<a name="service_context_for_a_value_converter"></a>   
## <a name="service-context-for-a-value-converter"></a>Değer dönüştürücüsü Hizmet bağlamı  
 Değer dönüştürücüsü uyguladığınızda, genellikle değer dönüştürücüsü uygulandığı bir içerik erişimi gerekir. Bu bağlamda Hizmet bağlamı olarak bilinir. Hizmet bağlamı etkin XAML şema içeriği gibi bilgileri içerir, XAML şema içeriği ve XAML nesne yazıcısı sağlayan ve benzeri türü eşleme sisteme erişim. Değer Dönüştürücüsü ve bir hizmet bağlamı sağlayabilir hizmetlere erişmek nasıl kullanılabilir hizmet bağlamları hakkında daha fazla bilgi için bkz: [hizmet bağlamları kullanılabilir tür dönüştürücüleri ve İşaretleme uzantıları](../../../docs/framework/xaml-services/service-contexts-available-to-type-converters-and-markup-extensions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Markup.MarkupExtension>  
 <xref:System.Xaml.XamlObjectWriter>  
 [XAML İşaretleme Uzantılarına Genel Bakış](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)  
 [XAML Tür Dönüştürücülerine Genel Bakış](../../../docs/framework/xaml-services/type-converters-for-xaml-overview.md)  
 [Tür Dönüştürücülerinde ve İşaretleme Uzantılarında Kullanılabilir Hizmet Bağlamları](../../../docs/framework/xaml-services/service-contexts-available-to-type-converters-and-markup-extensions.md)
