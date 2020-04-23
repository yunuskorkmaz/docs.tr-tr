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
ms.openlocfilehash: bee94b03d4fd6e6f5ef8571e83f554b381dd6582
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071656"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>XAML İçin Tür Dönüştürücüleri ve İşaretleme Uzantıları

Tür dönüştürücüler ve biçimlendirme uzantıları, XAML türü sistemlerinin ve XAML yazarlarının nesne grafik bileşenleri oluşturmak için kullandığı iki tekniktir. Bazı özellikleri paylaşsalar da, tür dönüştürücüler ve biçimlendirme uzantıları XAML düğüm akışında farklı şekilde temsil edilir. Bu belge kümesinde, tür dönüştürücüler, biçimlendirme uzantıları ve benzeri yapılar bazen topluca değer dönüştürücüler olarak adlandırılır.

## <a name="value-converters"></a>Değer Dönüştürücüler

XAML'de değer dönüştürücüler çeşitli senaryolar için kullanılır. Aşağıdaki liste XAML'deki farklı değer dönüştürücü türlerini gösterir:

- Tür dönüştürücü

- Biçimlendirme uzantısı

- Değer serileştirici

- XAML metin sözdizimi için mantık sağlayan ilgili sınıf veya destek sınıfı

## <a name="type-converters"></a>Tip Dönüştürücüler

.NET XAML Hizmetleri tanımında, tür dönüştürücüler CLR <xref:System.ComponentModel.TypeConverter> sınıfından türeyen sınıflardır. <xref:System.ComponentModel.TypeConverter>XAML var olmadan önce .NET'te olan bir sınıftır. Orijinal amacı özellik pencereleri ve IDE özellikleri için benzer metin tabanlı düzenleme metaforları desteklemek oldu. XAML'nin .NET'e <xref:System.ComponentModel.TypeConverter> getirilmesi, metin sözdizimini (öznitelik değerinde veya XAML değer düğümünde bulunduğu gibi) bir nesneye dönüştürmek için kullanır. <xref:System.ComponentModel.TypeConverter>metin sözdizimine nesne değerini serihale getirmek için de kullanılabilir. <xref:System.ComponentModel.TypeConverter>Windows Presentation Foundation (WPF) ve Windows Communication Foundation (WCF) önceki çerçeveye özgü XAML uygulamalarında da kullanılmıştır. <xref:System.ComponentModel.TypeConverter> XAML hakkında daha fazla bilgi [için, XAML Genel Bakış için Tip Dönüştürücüler](type-converters-overview.md)bakın.

## <a name="markup-extensions"></a>İşaretleme Uzantıları

.NET XAML Hizmetleri uygulamasında, biçimlendirme uzantıları <xref:System.Windows.Markup.MarkupExtension> sınıftan türeyen sınıflardır. Biçimlendirme uzantıları, bu biçimde XAML dili tarafından kökenli bir kavramdır. Biçimlendirme uzantısını, mantığını sağlamak için bir hizmet sınıfına çağıran genişletilebilir bir kaçış dizisi gibi bir şey olarak düşünebilirsiniz. Biçimlendirme açısından, XAML işlemcileri bir metin dizesindeki açılış ayracıyla ({) başlayan bir metin dizisiyle biçimlendirme uzantısını evrensel olarak tanırlar.

Biçimlendirme uzantıları tür dönüştürücülerden farklıdır. Tür dönüştürücüler genellikle türleri veya üyeleri ile ilişkilidir. Nesne grafiği oluşturma veya serileştirme, bu varlıklarla ilişkili metin sözdizimiyle karşılaştığında çağrılır.

Biçimlendirme uzantıları tek bir destekleyici hizmet sınıfıyla ilişkilidir, ancak herhangi bir üye değer için uygulanabilir. (Ancak, biçimlendirme uzantınızı, hizmet bağlamını kullanarak belirli üyelerveya hedef türleri ile kullanımını kasıtlı olarak kısıtlamak için uygulayabilirsiniz.) Biçimlendirme uzantıları bir tür dönüştürücü ilişkilendirme geçersiz kılabilir. Veya bunları, metin sözdizimini başka şekilde desteklemeyen üyeler için bir öznitelik değeri belirtmek için kullanabilirsiniz.

XAML için biçimlendirme uzantısı uygulama deseni hakkında daha fazla bilgi için, [XAML Genel Bakış için Biçimlendirme Uzantıları'na](markup-extensions-overview.md)bakın.

## <a name="value-serializers"></a>Değer Serializers

A, <xref:System.Windows.Markup.ValueSerializer> bir nesneyi dize dönüştürmek için en iyi duruma getirilmiş özel bir tür dönüştürücüdür. XAML için A <xref:System.Windows.Markup.ValueSerializer> `ConvertFrom` yöntemi hiç uygulamayabilir. Bir <xref:System.Windows.Markup.ValueSerializer> uygulama, bir <xref:System.ComponentModel.TypeConverter> uygulama gibi bir şekilde hizmet alır. Sanal yöntemler bir giriş `context` parametresi sağlar. Parametre, <xref:System.IServiceProvider> arabirimden devralan ve bir <xref:System.IServiceProvider.GetService%2A> metodu olan türdendir. <xref:System.Windows.Markup.IValueSerializerContext> `context`

XAML türü sisteminde ve serileştirme için XAML düğüm döngüsü işleme kullanan XAML yazar uygulamaları için, bir tür veya üye <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> ile ilişkili bir değer dönüştürücü kendi özelliği tarafından bildirilir. Serileştirme gerçekleştiren XAML yazarlarının anlamı, <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> a <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> ve varsa, yük yolu için tür dönüştürücünün kullanılması ve değer serileştiricisinin kaydetme yolu için kullanılmasıdır. <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> Varsa ancak <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> `null`varsa, tür dönüştürücü de kaydet yolu için kullanılır.

## <a name="other-value-converters"></a>Diğer Değer Dönüştürücüler

Değer dönüştürücü, tür dönüştürücünün veya biçimlendirme uzantısının belirli desenlerinin ötesinde genişletilebilir. Ancak, bu özelleştirme de .NET XAML Hizmetleri tarafından sağlanan XAML türü sisteminin yeniden tanımlanmasını gerektirir. Varolan XAML türü sisteminde tür dönüştürücüler, biçimlendirme uzantıları ve değer serileştiricileri için gösterimler ve raporlama sistemleri vardır, ancak özel değer dönüştürme biçimleri için değildir. Özel değer dönüştürücüleri oluşturmak istiyorsanız, <xref:System.Xaml.Schema.XamlValueConverter%601> türünü kullanın.

## <a name="type-converters-and-markup-extensions-in-combination"></a>Birlikte Dönüştürücüler ve Biçimlendirme Uzantıları Yazın

Biçimlendirme uzantıları ve tür dönüştürücüler XAML'de farklı durumlar için kullanılır. Biçimlendirme uzantısı kullanımları için bağlam kullanılabilir olsa da, biçimlendirme uzantısı sağlayan özelliklerin tür dönüştürme davranışı genellikle biçimlendirme uzantısı uygulamalarında denetlenmez. Başka bir deyişle, biçimlendirme uzantısı bir metin `ProvideValue` dizesini çıktıolarak döndürse bile, belirli bir özellik veya özellik değeri türüne uygulanan bu dizedeki dönüşüm davranışı çağrılmaz. Genellikle, biçimlendirme uzantısı amacı bir dize işlemek ve herhangi bir tür dönüştürücü dahil olmadan bir nesne döndürün.

## <a name="service-context-for-a-value-converter"></a>Değer Dönüştürücü için Hizmet Bağlamı

Bir değer dönüştürücü uyguladığınızda, genellikle değer dönüştürücünün uygulandığı bir içeriğe erişmeniz gerekir. Bu bağlam hizmet bağlamı olarak bilinir. Hizmet bağlamı, etkin XAML şeması bağlamı, XAML şema bağlamı ve XAML nesne yazarının sağladığı tür eşleme sistemine erişim ve benzeri bilgileri içerebilir. Değer dönüştürücü için kullanılabilen hizmet bağlamları ve hizmet bağlamının sağlayabileceği hizmetlere nasıl erişileceksiniz hakkında daha fazla bilgi için, [Tür Dönüştürücüler ve Biçimlendirme Uzantıları için Kullanılabilir Hizmet Bağlamları'na](service-contexts-with-type-converters-and-markup-extensions.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [XAML Biçimlendirme Uzantılarına Genel Bakış](markup-extensions-overview.md)
- [XAML Tür Dönüştürücülerine Genel Bakış](type-converters-overview.md)
- [Tür Dönüştürücülerinde ve İşaretleme Uzantılarında Kullanılabilir Hizmet Bağlamları](service-contexts-with-type-converters-and-markup-extensions.md)
