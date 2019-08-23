---
title: Çerçeve Özelliği Meta Verileri
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: c08cf28880d86331e3b561f1749333d401ba903e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964210"
---
# <a name="framework-property-metadata"></a>Çerçeve Özelliği Meta Verileri
Çerçeve özelliği meta verileri seçenekleri, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] mimaride WPF çerçeve düzeyinde olduğu düşünülen nesne öğelerinin özellikleri için raporlanır. Genel olarak WPF framework düzeyi atama, işleme, veri bağlama ve özellik sistemi işlevselliklerindeki gibi özelliklerin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sunu API 'leri ve yürütülebilir dosyalar tarafından işlenmesini gerektirir. Çerçeve özelliği meta verileri, belirli öğe özelliklerinin özelliğe özgü özelliklerini belirlemede bu sistemler tarafından sorgulanır.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu başlığında bağımlılık özelliklerini, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıflarda var olan bağımlılık özellikleri tüketicisinin perspektifinden anladığınızı ve [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md)konusunu okuduğunuzu varsaymaktadır. Ayrıca Read [Dependency özelliği meta verilerini](dependency-property-metadata.md)de kullanmalısınız.  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>Çerçeve özelliği meta verileri tarafından Iletilen Özellikler  
 Çerçeve özelliği meta verileri aşağıdaki kategorilere ayrılabilir:  
  
- Öğeyi etkileyen düzen özellikleri (<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>). Özelliği bu ilgili yönleri etkiliyorsa meta verilerde bu bayrakları ayarlayabilir ve ayrıca belirli işleme davranışını ve düzene yönelik bilgileri sağlamak <xref:System.Windows.FrameworkElement.MeasureOverride%2A> için sınıfınıza <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> yöntemleri de  /  uygulayabilirsiniz sistemin. Genellikle, bu tür bir uygulama, özellik meta verilerinde bu düzen özelliklerinden herhangi birinin doğru olduğu ve yalnızca bu ındoğrulamaların yeni bir düzen geçişi istediğini gerektirdiği bağımlılık özelliklerindeki Özellik doğrulamaları olup olmadığını denetler.  
  
- Bir öğenin (<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>) üst öğesini etkileyen düzen özelliklerini raporlama. Bu bayrakların varsayılan <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> olarak ayarlandığı bazı örnekler ve <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>.  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. Varsayılan olarak, bağımlılık özellikleri değerleri almayacaktır. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A>Devralmanın, bazı denetim birleştirme senaryolarında gerekli olan görsel ağaca da gitmesini sağlar.  
  
    > [!NOTE]
    > Özellik değerleri bağlamındaki "Inherits" terimi, bağımlılık özelliklerine özgü bir şey anlamına gelir; Bu, alt öğelerin, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sisteminin WPF framework düzeyi özelliği nedeniyle üst öğeden gerçek bağımlılık özelliği değerini devraldığı anlamına gelir. Türetilmiş türler aracılığıyla doğrudan yönetilen kod türü ve üyeleri devralma ile hiçbir şey yapmaz. Ayrıntılar için bkz. [özellik değeri devralma](property-value-inheritance.md).  
  
- Raporlama veri bağlama özellikleri (<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>, <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>). Varsayılan olarak, Framework 'ün bağımlılık özellikleri, tek yönlü bağlama davranışı ile veri bağlamayı destekler. Veri bağlamayı devre dışı bırakabilirsiniz (esnek ve Genişletilebilir olmaları amaçlanan için, varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API 'lerde bu tür özelliklerden pek çok örnek yoktur). Bağlama, bir denetimin davranışlarını bileşen parçaları (<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> bir örnektir) veya iki yönlü bağlamanın kullanıcılar için ortak ve beklenen senaryo (<xref:System.Windows.Controls.TextBox.Text%2A> Örneğin, bir örnektir) arasında birbirine bağlayan özellikler için iki yönlü bir varsayılana sahip olacak şekilde ayarlayabilirsiniz. Veri bağlama ile ilgili meta verilerin değiştirilmesi yalnızca varsayılanı etkiler; bağlama başına temelinde, varsayılan olarak her zaman değiştirilebilir. Bağlama modları ve genel olarak bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md).  
  
- Özelliklerin günlük kaydını (<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>) destekleyen uygulamalar veya hizmetler tarafından mi bir de erişilebilir olacağını bildirme. Genel öğeler için, günlüğe kaydetme varsayılan olarak etkinleştirilmez, ancak belirli kullanıcı girdisi denetimleri için seçmeli olarak etkinleştirilir. Bu özelliğin günlüğe kaydetme işlemi de dahil olmak üzere [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] günlüğe kaydetme hizmetleri tarafından okunması amaçlanmıştır ve genellikle, gezinti adımlarında kalıcı olması gereken listeler içindeki kullanıcı seçimleri gibi Kullanıcı denetimleri üzerinde ayarlanır. Günlük hakkında daha fazla bilgi için bkz. [gezintiye genel bakış](../app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>FrameworkPropertyMetadata okunuyor  
 Yukarıda bağlantılı özelliklerden her biri, <xref:System.Windows.FrameworkPropertyMetadata> ilk temel sınıfına <xref:System.Windows.UIPropertyMetadata>eklediği özel özelliklerdir. Bu özelliklerin `false` her biri varsayılan olarak olacaktır. Bu özelliklerin değerini bilmenin önemli olduğu bir özellik için meta veri isteği, döndürülen meta verileri öğesine <xref:System.Windows.FrameworkPropertyMetadata>dönüştürmeyi denemeli ve sonra her bir özelliğin değerlerini gerektiği gibi denetlemelidir.  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>Meta verileri belirtme  
 Yeni bir bağımlılık özelliği kaydına meta veri uygulama amaçları için yeni bir meta veri örneği oluşturduğunuzda kullanılacak meta veri sınıfını seçebilirsiniz: temel <xref:System.Windows.PropertyMetadata> veya gibi <xref:System.Windows.FrameworkPropertyMetadata>bir türetilmiş sınıf. Genellikle, özellikle özelliğinde özellik sistemi <xref:System.Windows.FrameworkPropertyMetadata>ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen ve veri bağlama gibi işlevlerle etkileşim varsa, kullanmanız gerekir. Daha karmaşık senaryolar için başka bir seçenek de, üyelerine <xref:System.Windows.FrameworkPropertyMetadata> daha fazla bilgi içeren kendi meta veri raporlama sınıfınızı oluşturmak için ' den türetmektir. Ya da uygulamanızın özelliklerine <xref:System.Windows.PropertyMetadata> yönelik <xref:System.Windows.UIPropertyMetadata> destek derecesini iletmek için veya kullanabilirsiniz.  
  
 Var olan Özellikler (<xref:System.Windows.DependencyProperty.AddOwner%2A> veya <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> çağrı) için, özgün kayıt tarafından kullanılan meta veri türüyle her zaman geçersiz kılmalısınız.  
  
 Bir <xref:System.Windows.FrameworkPropertyMetadata> örnek oluşturuyorsanız, bu meta verileri çerçeve özelliği özellikleriyle iletişim kuran belirli özellikler için değerlerle doldurmanın iki yolu vardır:  
  
1. <xref:System.Windows.FrameworkPropertyMetadata> Bir`flags` parametreye izin veren Oluşturucu imzasını kullanın. Bu parametre, <xref:System.Windows.FrameworkPropertyMetadataOptions> sabit listesi bayraklarının tüm istenen Birleşik değerleriyle doldurulmalıdır.  
  
2. Bir `flags` parametre olmadan imzalardan birini kullanın ve her bir raporlama Boolean <xref:System.Windows.FrameworkPropertyMetadata> özelliğini istediğiniz her bir özellik değişikliği `true` için olarak ayarlayın. Bunu yaparsanız, bu bağımlılık özelliğine sahip herhangi bir öğe oluşturulmadan önce bu özellikleri ayarlamanız gerekir; Boolean özellikleri, `flags` parametreyi önlemenin ve meta verileri hala dolduran bu davranışa izin vermek için okuma-yazma ' dır. ancak meta verilerin özellik kullanılmadan önce etkin bir şekilde mühürlenmesi gerekir. Bu nedenle, meta veriler istendiğinde özellikleri ayarlamaya çalışmak geçersiz bir işlem olur.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>Çerçeve özelliği meta verileri birleştirme davranışı  
 Çerçeve özelliği meta verilerini geçersiz kıldığınızda, farklı meta veri özellikleri birleştirilir veya değiştirilmiştir.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>birleştirilir. Yeni <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>bir eklerseniz, bu geri çağırma meta verilerde depolanır. Geçersiz kılmada bir <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> belirtmezseniz, <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> değeri meta verilerde belirtilen en yakın üst öğesinden bir başvuru olarak yükseltilir.  
  
- İçin <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> gerçek özellik sistemi davranışı, hiyerarşideki tüm meta veri sahipleri için olan uygulamalar, özellik sistemi tarafından yürütme sırası, en derin türetilmiş sınıfın geri çağırmaları İlk olarak çağrılır. Devralınan geri çağrılar yalnızca bir kez çalışır ve bu, meta verilere yerleştirilmiş sınıfa ait olduğu şekilde sayımlardır.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>değiştirilmiştir. Geçersiz kılmada bir <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> belirtmezseniz, <xref:System.Windows.PropertyMetadata.DefaultValue%2A> değeri meta verilerde belirtilen en yakın üst öğesinden gelir.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>uygulamalar değiştirilmiştir. Yeni <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>bir eklerseniz, bu geri çağırma meta verilerde depolanır. Geçersiz kılmada bir <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> belirtmezseniz, <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> değeri meta verilerde belirtilen en yakın üst öğesinden bir başvuru olarak yükseltilir.  
  
- Özellik sistemi davranışı yalnızca <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> en anlık meta verilerde çağrılır. Hiyerarşideki diğer <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> uygulamalar için başvuru korunmaz.  
  
- <xref:System.Windows.FrameworkPropertyMetadataOptions> Numaralandırma bayrakları bit düzeyinde veya işlem olarak birleştirilir.  Belirtirseniz <xref:System.Windows.FrameworkPropertyMetadataOptions>, özgün seçeneklerin üzerine yazılmaz.  Bir seçeneği değiştirmek için üzerinde <xref:System.Windows.FrameworkPropertyMetadata>ilgili özelliği ayarlayın. Örneğin, özgün <xref:System.Windows.FrameworkPropertyMetadata> nesne <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType> bayrağı ayarlarsa, öğesini olarak `false`ayarlayarak <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> değiştirebilirsiniz.  
  
 Bu davranış tarafından <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>uygulanır ve türetilmiş meta veri sınıflarında geçersiz kılınabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Bağımlılık Özelliği Meta Verisi](dependency-property-metadata.md)
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
