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
ms.openlocfilehash: dee5ec65993cf20cb57377694f61af092b0ccf26
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939697"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları
Tür dönüştürücüler ve biçimlendirme uzantıları, XAML tür sistemleri ve XAML yazıcılarının nesne Graph bileşenleri oluşturmak için kullandığı iki tekniktir. Bazı özellikleri paylaşmakla birlikte, tür dönüştürücüler ve biçimlendirme uzantıları XAML düğüm akışında farklı şekilde temsil edilir. Bu belge kümesinde dönüştürücüler, biçimlendirme uzantıları ve benzer yapılar bazen değer dönüştürücüler olarak adlandırılır.  
  
<a name="value_converters"></a>   
## <a name="value-converters"></a>Değer dönüştürücüler  
 XAML 'de, değer dönüştürücüler çeşitli senaryolar için kullanılır. Aşağıdaki liste, XAML 'de farklı değer dönüştürücülerinin türlerini gösterir:  
  
- Tür dönüştürücüsü  
  
- Biçimlendirme uzantısı  
  
- Değer seri hale getirici  
  
- XAML metin sözdizimi için mantık sağlayan ilgili sınıf veya destek sınıfı  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Tür dönüştürücüler  
 .NET Framework xaml Hizmetleri tanımında, tür dönüştürücüler clr <xref:System.ComponentModel.TypeConverter> sınıfından türetilen sınıflardır. <xref:System.ComponentModel.TypeConverter>, XAML 'den önce Microsoft .NET Framework içinde olan bir sınıftır. Özgün amacı, özellik pencerelerini ve IDE özellikleri için de benzer metin tabanlı düzenlemeler destekliyoruz. .NET Framework xaml 'ye giriş, bir metin <xref:System.ComponentModel.TypeConverter> söz dizimini (öznitelik değeri veya xaml değer düğümünde bulunduğu şekilde) bir nesneye dönüştürmek için kullanır. <xref:System.ComponentModel.TypeConverter>, bir nesne değerini metin sözdizimine seri hale getirmek için de kullanılabilir. <xref:System.ComponentModel.TypeConverter>Ayrıca, Windows Presentation Foundation (WPF) ve Windows Communication Foundation (WCF) içindeki önceki çerçeveye özgü XAML uygulamalarında da kullanılmıştı. Xaml <xref:System.ComponentModel.TypeConverter> 'de hakkında daha fazla bilgi için bkz. [XAML için tür dönüştürücüleri genel bakış](type-converters-for-xaml-overview.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>İşaretleme Uzantıları  
 .NET Framework xaml Hizmetleri uygulamasında, biçimlendirme uzantıları <xref:System.Windows.Markup.MarkupExtension> sınıfından türetilen sınıflardır. Biçimlendirme uzantıları, bu formda XAML dili tarafından oluşturulan bir kavramdır. Bir biçimlendirme uzantısını, mantığını sağlamak için bir hizmet sınıfına çağıran bir Genişletilebilir kaçış sırası gibi düşünebilirsiniz. Biçimlendirme açısından XAML işlemcileri, bir metin dizesinde açma ayracı ({) ile başlayan bir metin dizisi ile biçimlendirme uzantısını evrensel olarak tanır.  
  
 Biçimlendirme uzantıları tür dönüştürücülerden farklıdır. Tür dönüştürücüler genellikle türler veya üyelerle ilişkilendirilir. Bir nesne grafiği oluşturma veya serileştirme, bu varlıklarla ilişkili bir metin söz dizimi ile karşılaştığında çağırılır.  
  
 Biçimlendirme uzantıları tek bir destekleme hizmeti sınıfıyla ilişkilendirilir, ancak herhangi bir üye değeri için uygulanabilir. (Ancak, hizmet bağlamını kullanarak kullanımını belirli üyelere veya hedef türlerine kasıtlı olarak kısıtlamak için biçimlendirme uzantınızı uygulayabilirsiniz.) Biçimlendirme uzantıları, bir tür dönüştürücü ilişkilendirmesini geçersiz kılabilir. Alternatif olarak, bir metin sözdizimini desteklemeyen Üyeler için bir öznitelik değeri belirtmek üzere bunları kullanabilirsiniz.  
  
 XAML için biçimlendirme uzantısı uygulama düzeniyle ilgili daha fazla bilgi için bkz. [xaml Için biçimlendirme uzantıları genel bakış](markup-extensions-for-xaml-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Markup.MarkupExtension> Ve <xref:System.Windows.Markup.ValueSerializer> türleri ad alanında değil <xref:System.Windows.Markup> ad alanında bulunur. <xref:System.Xaml> Bu, bu türlerin WPF veya Windows Forms teknolojilerine özgü olduğunu göstermez, aksi takdirde dize `Windows`içeren clr ad alanlarını dolduracaktır. <xref:System.Windows.Markup.MarkupExtension>System <xref:System.Windows.Markup.ValueSerializer> . xaml derlemesinde ve belirli bir çerçeve bağımlılığı yoktur. Bu türler .NET Framework 3,0 için CLR ad alanında vardı ve var olan WPF projelerindeki başvuruların oluşmasını önlemek için .NET Framework 4 ' teki CLR ad alanında kalır. Daha fazla bilgi için bkz. [WPF 'Den System. xaml 'e geçirilen türler](types-migrated-from-wpf-to-system-xaml.md).  
  
<a name="value_serializers"></a>   
## <a name="value-serializers"></a>Değer serileştiricileri  
 <xref:System.Windows.Markup.ValueSerializer> , Bir nesneyi dizeye dönüştürmek için optimize edilmiş özel bir tür dönüştürücütür. Bir <xref:System.Windows.Markup.ValueSerializer> XAML için bir, `ConvertFrom` metodu hiç uygulayamaz. Uygulama, Hizmetleri <xref:System.ComponentModel.TypeConverter> uygulama gibi bir şekilde edinir. <xref:System.Windows.Markup.ValueSerializer> Sanal yöntemler bir giriş `context` parametresi sağlar. Parametresi, arabiriminden devralan ve <xref:System.Windows.Markup.IValueSerializerContext> bir<xref:System.IServiceProvider.GetService%2A> yöntemine sahip olan türüdür. <xref:System.IServiceProvider> `context`  
  
 Xaml tür sisteminde ve serileştirme için xaml düğüm döngüsü işleme kullanan XAML yazıcı uygulamalarında, bir tür veya üyeyle ilişkili bir değer Dönüştürücüsü kendi <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> özelliği tarafından raporlanır. Serileştirme gerçekleştiren xaml yazıcılarının anlamı, bir ve <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> varsa, tür dönüştürücüsünün yükleme yolu için kullanılması ve kayıt için seri hale getirici 'nin bir değer olarak kullanılması gerekir. Varsa, ancak <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> , tür dönüştürücüsü Kaydet yolu için de kullanılır. `null` <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType>  
  
<a name="other_value_converters"></a>   
## <a name="other-value-converters"></a>Diğer değer dönüştürücüler  
 Bir değer Dönüştürücüsü, bir tür dönüştürücünün veya biçimlendirme uzantısının belirli desenlerinin ötesinde genişletilebilir. Ancak, bu özelleştirme XAML türü sisteminin .NET Framework XAML Hizmetleri tarafından sağlandığı şekilde yeniden tanımlanması de gerektirir. Var olan XAML tür sisteminde tür dönüştürücüler, biçimlendirme uzantıları ve değer serileştiricileri için temsiller ve raporlama sistemleri vardır, ancak özel değer dönüştürme biçimleri için kullanılamaz. Özel değer dönüştürücüler oluşturmak istiyorsanız, <xref:System.Xaml.Schema.XamlValueConverter%601> türü kullanın.  
  
<a name="type_converters_and_markup_extensions_in_combination"></a>   
## <a name="type-converters-and-markup-extensions-in-combination"></a>Kombinasyonda tür dönüştürücüler ve biçimlendirme uzantıları  
 Biçimlendirme uzantıları ve tür dönüştürücüler XAML 'deki farklı durumlar için kullanılır. Bağlam biçimlendirme uzantısı kullanımları için kullanılabilir olsa da, biçimlendirme uzantısının bir değer sağladığı özelliklerin dönüştürme davranışı genellikle biçimlendirme uzantısı uygulamalarında denetlenmez. Diğer bir deyişle, bir biçimlendirme uzantısı `ProvideValue` çıkış olarak bir metin dizesi döndürse bile, belirli bir özelliğe uygulanan veya özellik değeri türü çağrılmayan Bu dizeye dönüştürme davranışı yazın. Genellikle, bir biçimlendirme uzantısının amacı bir dizeyi işlemek ve herhangi bir tür dönüştürücüsü olmadan bir nesne döndürmek olur.  
  
<a name="service_context_for_a_value_converter"></a>   
## <a name="service-context-for-a-value-converter"></a>Değer Dönüştürücüsü için hizmet bağlamı  
 Bir değer Dönüştürücüsü uyguladığınızda, genellikle değer dönüştürücünün uygulandığı bir içeriğe erişmeniz gerekir. Bu bağlam hizmet bağlamı olarak bilinir. Hizmet bağlamı, etkin XAML şeması bağlamı, XAML şema bağlamı ve XAML nesne yazıcısının sağladığı tür eşleme sistemine erişim vb. gibi bilgileri içerebilir. Bir değer Dönüştürücüsü için kullanılabilen hizmet bağlamları ve bir hizmet bağlamının sağlayabilecek hizmetlere erişme hakkında daha fazla bilgi için, bkz. [tür dönüştürücüler ve biçimlendirme uzantıları Için kullanılabilir hizmet bağlamları](service-contexts-available-to-type-converters-and-markup-extensions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [XAML İşaretleme Uzantılarına Genel Bakış](markup-extensions-for-xaml-overview.md)
- [XAML Tür Dönüştürücülerine Genel Bakış](type-converters-for-xaml-overview.md)
- [Tür Dönüştürücülerinde ve İşaretleme Uzantılarında Kullanılabilir Hizmet Bağlamları](service-contexts-available-to-type-converters-and-markup-extensions.md)
