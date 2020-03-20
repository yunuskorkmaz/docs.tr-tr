---
title: Çerçeve Özelliği Meta Verileri
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: 8fb6e1b4cf6aed9454e9e9f1a77277d2f3611ca8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186649"
---
# <a name="framework-property-metadata"></a>Çerçeve Özelliği Meta Verileri
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Çerçeve özelliği meta veri seçenekleri, mimaride WPF çerçeve düzeyinde olduğu düşünülen nesne öğelerinin özellikleri için bildirilir. Genel olarak WPF çerçeve düzeyinde ki atama, render, veri bağlama ve özellik sistemi iyileştirmeleri gibi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerin sunu API'leri ve yürütülebilir ler tarafından işlenmesini gerektirir. Çerçeve özelliği meta verileri, belirli öğe özelliklerinin özel özelliklerine özgü özelliklerini belirlemek için bu sistemler tarafından sorgulanır.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, bağımlılık özelliklerini sınıflardaki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] varolan bağımlılık özelliklerinin tüketici perspektifinden anladığınızı ve Bağımlılık Özellikleri Genel [Bakış'ı](dependency-properties-overview.md)okuduğunuzu varsayar. [Ayrıca Bağımlılık Özelliği Metaverileri](dependency-property-metadata.md)okumuş olmalısınız.  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>
## <a name="what-is-communicated-by-framework-property-metadata"></a>Çerçeve Özellik MetaData Tarafından Tebliğ Nedir  
 Çerçeve özelliği meta verileri aşağıdaki kategorilere ayrılabilir:  
  
- Bir öğeyi etkileyen düzen<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>özelliklerini <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>bildirme ( , , , ). Özellik bu yönleri etkiliyorsa ve düzeni sistemine belirli işleme davranışı ve <xref:System.Windows.FrameworkElement.MeasureOverride%2A>  /  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> bilgilerini sağlamak için sınıfınızdaki yöntemleri de uyguluyorsanız, bu bayrakları meta verilerde ayarlayabilirsiniz. Genellikle, böyle bir uygulama, bu düzen özelliklerinden herhangi birinin özellik meta verilerinde doğru olduğu bağımlılık özelliklerindeki özellik geçersizliklerini denetler ve yalnızca bu geçersiz likler yeni bir düzen geçişi isteği gerektirir.  
  
- Bir öğenin üst öğesini etkileyen<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>düzen <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>özelliklerini bildirme ( , ). Bu bayrakların varsayılan olarak ayarlandığı bazı örnekler <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> ve <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>.  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. Varsayılan olarak, bağımlılık özellikleri değerleri devralmaz. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A>bazı kontrol birleştirme senaryoları için gerekli olan görsel bir ağaca da kalıtım yolunun seyahat etmesini sağlar.  
  
    > [!NOTE]
    > Özellik değerleri bağlamında "devralır" terimi bağımlılık özellikleri için özel bir şey anlamına gelir; özellik sisteminin WPF çerçeve düzeyi özelliği [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nedeniyle alt öğelerin üst öğelerden gerçek bağımlılık özelliği değerini devralabileceği anlamına gelir. Yönetilen kod türü ve türemiş türler aracılığıyla üye devralma ile doğrudan ilgisi yoktur. Ayrıntılar [için, Bkz. Özellik Değeri Devralma.](property-value-inheritance.md)  
  
- Veri bağlama özelliklerinin raporlanması (<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>, <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>). Varsayılan olarak, çerçevedeki bağımlılık özellikleri tek yönlü bağlama davranışıyla veri bağlamayı destekler. Bunun için herhangi bir senaryo yoksa veri bağlamayı devre dışı kılabilirsiniz (esnek ve genişletilebilir olmaları amaçlandı, varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API'lerde bu tür özelliklerin çok fazla örneği yoktur). Bir denetimin davranışlarını bileşen parçaları arasında birbirine bağlayan (bir<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> örnektir) veya iki yönlü bağlamanın kullanıcılar için yaygın ve beklenen senaryo olduğu<xref:System.Windows.Controls.TextBox.Text%2A> (bir örnektir) özellikleri için bağlamayı iki yönlü bir varsayılana ayarlayabilirsiniz. Veri bağlama ile ilgili meta verileri değiştirmek yalnızca varsayılanı etkiler; varsayılan her zaman değiştirilebilir bir bağlama temelinde. Bağlama modları ve genel olarak bağlama hakkında ayrıntılı bilgi için [Veri Bağlama Genel Bakış'a](../../../desktop-wpf/data/data-binding-overview.md)bakın.  
  
- Özelliklerin günlük leilgili uygulamaları veya hizmetleri tarafından günlüğe indirilip günlüğe indirilmeyeceğini bildirme (<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>). Genel öğeler için günlük leme varsayılan olarak etkinleştirilir, ancak belirli kullanıcı giriş denetimleri için seçici olarak etkinleştirilir. Bu özellik, günlük uygulaması da dahil olmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] üzere günlük hizmetleri tarafından okunması amaçlanmıştır ve genellikle gezinti adımlarında kalıcı olması gereken listeler deki kullanıcı seçimleri gibi kullanıcı denetimleri üzerinde ayarlanır. Günlük hakkında daha fazla bilgi için [Gezintiye Genel Bakış'a](../app-development/navigation-overview.md)bakın.  
  
<a name="Reading_FrameworkPropertyMetadata"></a>
## <a name="reading-frameworkpropertymetadata"></a>Okuma ÇerçevesiEmlakMetadata  
 Yukarıda bağlı özelliklerin her biri, <xref:System.Windows.FrameworkPropertyMetadata> hemen taban sınıfına <xref:System.Windows.UIPropertyMetadata>eklenen belirli özelliklerdir. Bu özelliklerin her `false` biri varsayılan olarak olacaktır. Bu özelliklerin değerini bilmenin önemli olduğu bir özellik için meta veri isteği, döndürülen meta verileri <xref:System.Windows.FrameworkPropertyMetadata>(döndürülen meta verileri) olarak dökmeye çalışmalı ve gerektiğinde tek tek özelliklerin değerlerini denetlemelidir.  
  
<a name="Specifying_Metadata"></a>
## <a name="specifying-metadata"></a>Meta verileri belirtme  
 Meta verileri yeni bir bağımlılık özelliği kaydına uygulamak amacıyla yeni bir meta veri örneği oluşturduğunuzda, hangi meta <xref:System.Windows.PropertyMetadata> veri sınıfının <xref:System.Windows.FrameworkPropertyMetadata>kullanılacağı seçeneğiniz vardır: taban veya türemiş bazı sınıf. Genel olarak, özellikle <xref:System.Windows.FrameworkPropertyMetadata>mülkünüzün özellik sistemi yle herhangi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir etkileşimi varsa ve düzen ve veri bağlama gibi işlevler varsa kullanmalısınız. Daha karmaşık senaryolar için başka bir <xref:System.Windows.FrameworkPropertyMetadata> seçenek, üyeleri taşınan ekstra bilgi ile kendi meta veri raporlama sınıfı oluşturmak için elde etmektir. Veya uygulamanızın <xref:System.Windows.PropertyMetadata> <xref:System.Windows.UIPropertyMetadata> özellikleri için destek derecesini kullanabilir veya iletişim kurabilirsiniz.  
  
 Varolan özellikler<xref:System.Windows.DependencyProperty.AddOwner%2A> <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> (veya arama) için, her zaman özgün kayıt tarafından kullanılan meta veri türü ile geçersiz kılmanız gerekir.  
  
 Bir <xref:System.Windows.FrameworkPropertyMetadata> örnek oluşturuyorsanız, bu meta verileri çerçeve özelliği özelliklerini bildiren belirli özellikler için değerlerle doldurmanın iki yolu vardır:  
  
1. Parametreye <xref:System.Windows.FrameworkPropertyMetadata> izin veren `flags` yapıcı imzayı kullanın. Bu parametre numaralandırma bayraklarının <xref:System.Windows.FrameworkPropertyMetadataOptions> istenilen tüm birleşik değerleri ile doldurulmalıdır.  
  
2. Bir parametre olmadan imzalardan birini kullanın ve sonra her raporlama `true` Boolean özelliğini istenen her karakteristik değişiklik için ayarlayın. <xref:System.Windows.FrameworkPropertyMetadata> `flags` Bunu yaparsanız, bu bağımlılık özelliğine sahip öğeler oluşturulmadan önce bu özellikleri ayarlamanız gerekir; Boolean `flags` özellikleri, parametreden kaçınma ve meta verileri doldurma ya da bu davranışına izin vermek için okuma-yazma özelliğidir, ancak meta verilerin özellik kullanımından önce etkili bir şekilde mühürlenmiş olması gerekir. Bu nedenle, meta veriler istendikten sonra özellikleri ayarlamaya çalışmak geçersiz bir işlem olacaktır.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>
## <a name="framework-property-metadata-merge-behavior"></a>Çerçeve Özellik Meta veri birleştirme davranışı  
 Çerçeve özelliği meta verilerini geçersiz kaldığınızda, farklı meta veri özellikleri birleştirilir veya değiştirilir.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>birleştirilir. Yeni <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>bir , bu geri arama meta verilerde depolanır eklerseniz. Geçersiz kılmada bir <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> belirtmezseniz, değeri <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> meta verilerde belirtilen en yakın atadan bir başvuru olarak yükseltilir.  
  
- Gerçek özellik sistemi <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> davranışı, hiyerarşideki tüm meta veri sahipleri için uygulamaların korunması ve bir tabloya eklenmesidir ve özellik sistemi tarafından yürütme sırası en derinden türetilmiş sınıfın geri aramaları ilk çağrılması dır. Devralınan geri aramalar, bunları meta verilere yerleştiren sınıfa ait olduğunu sayarak yalnızca bir kez çalıştırılır.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>değiştirilir. Geçersiz kılmada bir <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> belirtmezseniz, değeri <xref:System.Windows.PropertyMetadata.DefaultValue%2A> meta verilerde onu belirten en yakın atadan gelir.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>uygulamaları değiştirilir. Yeni <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>bir , bu geri arama meta verilerde depolanır eklerseniz. Geçersiz kılmada bir <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> belirtmezseniz, değeri <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> meta verilerde belirtilen en yakın atadan bir başvuru olarak yükseltilir.  
  
- Özellik sistemi davranışı, yalnızca <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> hemen meta verilerde çağrılan olmasıdır. Hiyerarşideki diğer <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> uygulamalara yapılan atıflar korunur.  
  
- Numaralandırma <xref:System.Windows.FrameworkPropertyMetadataOptions> bayrakları bitwise VEYA işlemi olarak birleştirilir.  Belirtirseniz, <xref:System.Windows.FrameworkPropertyMetadataOptions>özgün seçenekler üzerine yazılmamış.  Bir seçeneği değiştirmek için, ilgili <xref:System.Windows.FrameworkPropertyMetadata>özelliği ' ye ayarlayın. Örneğin, <xref:System.Windows.FrameworkPropertyMetadata> özgün nesne bayrağı <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType> ayarlarsa, bunu ' <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> `false`ayarı yaparak değiştirebilirsiniz.  
  
 Bu davranış, türetilmiş meta veri sınıfları tarafından <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>uygulanır ve geçersiz kılınabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Bağımlılık Özelliği Meta Verisi](dependency-property-metadata.md)
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
