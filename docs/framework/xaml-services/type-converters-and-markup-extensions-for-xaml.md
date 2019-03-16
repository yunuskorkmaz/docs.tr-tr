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
ms.openlocfilehash: 1704a7a86e89685763da7bf49a67c1fe8373124a
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58050534"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları
Tür dönüştürücülerinde ve İşaretleme uzantılarında Nesne grafiği bileşenleri oluşturmak için XAML türü sistemleri ve XAML yazarları kullanan iki tekniklerdir. Farklı bazı özellikleri paylaşır olsa da, tür dönüştürücüleri ve İşaretleme uzantılarında XAML düğümü akışı temsil edilir. Bu belgede kümesi, tür dönüştürücüleri, biçimlendirme uzantılarını ve benzer yapıları bazen topluca için değer dönüştürücüler adlandırılır.  
  
<a name="value_converters"></a>   
## <a name="value-converters"></a>Değer dönüştürücüler  
 XAML içinde değer dönüştürücüler çeşitli senaryolar için kullanılır. Aşağıdaki liste, XAML değer dönüştürücüler farklı türde gösterir:  
  
-   Tür dönüştürücü  
  
-   İşaretleme uzantısı  
  
-   Değer seri hale getirici  
  
-   İlgili sınıfı veya XAML metni sözdizimi mantığı sağlayan destek sınıfı  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Tür dönüştürücüleri  
 .NET Framework XAML hizmetlerinde tanımında tür dönüştürücüleri CLR'den türetilen sınıflardır <xref:System.ComponentModel.TypeConverter> sınıfı. <xref:System.ComponentModel.TypeConverter> Microsoft .NET Framework XAML yokken olan bir sınıftır. Windows özelliği ve metin tabanlı benzer düzenleme metaphors için desteklemek için asıl amacı olan [!INCLUDE[TLA2#tla_ide](../../../includes/tla2sharptla-ide-md.md)] özellikleri. .NET Framework XAML sunulmasıyla kullanan <xref:System.ComponentModel.TypeConverter> metin sözdizimi (olarak bir öznitelik değeri ya da XAML değer düğümü bulundu) bir nesneye dönüştürmek için. <xref:System.ComponentModel.TypeConverter> Ayrıca bir nesne değeri metin sözdizimi için seri hale getirmek için kullanılabilir. <xref:System.ComponentModel.TypeConverter> Windows Presentation Foundation (WPF) ve Windows Communication Foundation (WCF) önceki çerçeveye özgü XAML uygulamalarında da kullanıldı. Hakkında daha fazla bilgi için <xref:System.ComponentModel.TypeConverter> XAML içinde bkz [genel XAML tür Dönüştürücülerine](type-converters-for-xaml-overview.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Biçimlendirme uzantıları  
 Türetilen sınıflar .NET Framework XAML hizmetlerinde uygulamasında biçimlendirme uzantılarıdır <xref:System.Windows.Markup.MarkupExtension> sınıfı. Biçimlendirme uzantıları, bu form XAML dili tarafından oluşturulan bir kavramdır. Bir işaretleme uzantısı gibi mantığını sağlamak için bir hizmet sınıfına çağıran bir Genişletilebilir kaçış dizisi olarak düşünebilirsiniz. Biçimlendirme açısından XAML işlemci Evrensel bir işaretleme uzantısı, bir metin dizesindeki bir açılış ayracı ({}) ile başlayan bir metin diziyle tanır.  
  
 Biçimlendirme uzantıları tür dönüştürücüleri farklı. Tür dönüştürücüleri genellikle türleri veya üyeleri ile ilişkilidir. Bir nesne grafiği oluşturma sırasında çağrılan veya bu varlıklarla ilişkili metin sözdiziminin bir seri hale getirme karşılaşır.  
  
 Biçimlendirme uzantıları, tek bir destek hizmeti sınıf ile ilişkilendirilir, ancak herhangi bir üyenin değeri için uygulanabilir. (Ancak, kasıtlı olarak kullanımını belirli üyeleri veya hedef türleri, hizmet bağlamı kullanarak kısıtlamak için bir işaretleme uzantısı uygulayabilirsiniz.) Biçimlendirme uzantıları, bir tür dönüştürücüsü ilişkilendirme geçersiz kılabilirsiniz. Veya bir metin söz dizimi desteğimizi sonlandıracağımızı olmayan üyeler için bir öznitelik değeri belirtmek için kullanabilirsiniz.  
  
 XAML işaretleme uzantısı uygulama modeli hakkında daha fazla bilgi için bkz. [genel XAML işaretleme uzantılarına](markup-extensions-for-xaml-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Markup.MarkupExtension> Ve <xref:System.Windows.Markup.ValueSerializer> türleridir hem de <xref:System.Windows.Markup> ad alanı ve de <xref:System.Xaml> ad alanı. Bu bu tür aksi dizeyi içeren CLR ad alanları doldurmak WPF veya Windows Forms teknolojiye özgü göstermez `Windows`. <xref:System.Windows.Markup.MarkupExtension> ve <xref:System.Windows.Markup.ValueSerializer> System.Xaml derlemede ve belirli framework bağımlılığı olmayan sahiptir. Bu türler için CLR ad alanı varolan [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] ve CLR ad alanında kalır [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] başvuruları varolan WPF projelerinde bozmayı önlemek için. Daha fazla bilgi için [geçirilen türler wpf'den System.XAML'ye](types-migrated-from-wpf-to-system-xaml.md).  
  
<a name="value_serializers"></a>   
## <a name="value-serializers"></a>Değer seri hale getiricileri genişletme  
 A <xref:System.Windows.Markup.ValueSerializer> nesneyi bir dizeye dönüştürmek için optimize edilmiş bir özel tür dönüştürücü. A <xref:System.Windows.Markup.ValueSerializer> XAML değil uygulayabilir için `ConvertFrom` hiç yöntemi. A <xref:System.Windows.Markup.ValueSerializer> uygulaması edinir Hizmetleri gibi bir şekilde bir <xref:System.ComponentModel.TypeConverter> uygulaması. Sanal yöntemleri bir giriş sağlaması `context` parametresi. `context` Parametre türüdür <xref:System.Windows.Markup.IValueSerializerContext>, işlevinden devralan <xref:System.IServiceProvider> arabirim ve sahip bir <xref:System.IServiceProvider.GetService%2A> yöntemi.  
  
 XAML tür sisteminde ve seri hale getirme için XAML düğümü çevrim işleme kullanan XAML yazıcı uygulamaları için bir tür veya üye ile ilişkili bir değer dönüştürücü kendi tarafından bildirilen <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> özelliği. Serileştirme gerçekleştiren XAML yazıcılar anlamı ise bir <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> ve <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> yok, yükleme yolu için tür dönüştürücüsü kullanılmalıdır ve değeri seri hale getirici kaydetme için kullanılması gereken yolu. Varsa <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> var ancak <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> olduğu `null`, tür dönüştürücüsünü kaydetme için de kullanılır yolu.  
  
<a name="other_value_converters"></a>   
## <a name="other-value-converters"></a>Diğer değer dönüştürücüler  
 Bir değer dönüştürücü dışında bir tür dönüştürücüsü veya bir işaretleme uzantısı belirli desenlerle genişletilebilir. Ancak, bu özelleştirme .NET Framework XAML hizmetlerinde tarafından sağlanan XAML tür sistemi yeniden tanımlanması gerekir. Gösterimler ve raporlama sistemleri için tür dönüştürücüleri ve İşaretleme uzantıları değeri seri hale getiricileri genişletme, ancak özel formlar değeri dönüştürme için mevcut XAML tür sistemi vardır. Özel değer dönüştürücüler oluşturmak istediğiniz kullanırsanız <xref:System.Xaml.Schema.XamlValueConverter%601> türü.  
  
<a name="type_converters_and_markup_extensions_in_combination"></a>   
## <a name="type-converters-and-markup-extensions-in-combination"></a>Tür dönüştürücülerinde ve İşaretleme uzantılarında birlikte  
 İşaretleme uzantıları ve tür dönüştürücüleri XAML farklı durumlarda kullanılır. Bağlam için işaretleme uzantısı kullanımları kullanılabilir olsa da, burada bir değerdir genellikle bir işaretleme uzantısı sağlar. özellikleri türü dönüştürme davranışını işaretleme uzantısı uygulamalarında işaretlenmemiştir. Diğer bir deyişle, bile bir işaretleme uzantısı bir metin dizesi olarak döndürür, `ProvideValue` çıkışı, belirli özellik ya da özellik değeri türü uygulanan olarak bu dize türü dönüştürme davranışını değil çağrılır. Genellikle, bir işaretleme uzantısı amacı bir dize işleme ve ilgili herhangi bir tür dönüştürücüsü olmadan bir nesne döndürür oluşturmaktır.  
  
<a name="service_context_for_a_value_converter"></a>   
## <a name="service-context-for-a-value-converter"></a>Hizmet bağlamı için bir değer dönüştürücü  
 Bir değer dönüştürücü uyguladığınızda, genellikle değer dönüştürücü uygulandığı bir bağlam erişimi gerekir. Bu bağlam, hizmet bağlamı bilinir. Hizmet bağlamı etkin XAML şema içeriği gibi bilgileri ekleyin, XAML şema içeriği ve XAML nesne yazıcısı sağlayan ve benzeri türü eşleme sistemine erişebilir. Bir değer dönüştürücü ve nasıl bir hizmet bağlamı sağlayabilir hizmetlere erişmek için kullanılabilir hizmet bağlamları hakkında daha fazla bilgi için bkz: [tür dönüştürücüleri ve İşaretleme uzantıları için hizmet bağlamı kullanılabilir](service-contexts-available-to-type-converters-and-markup-extensions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [XAML İşaretleme Uzantılarına Genel Bakış](markup-extensions-for-xaml-overview.md)
- [XAML Tür Dönüştürücülerine Genel Bakış](type-converters-for-xaml-overview.md)
- [Tür Dönüştürücülerinde ve İşaretleme Uzantılarında Kullanılabilir Hizmet Bağlamları](service-contexts-available-to-type-converters-and-markup-extensions.md)
