---
title: Çerçeve Özelliği Meta Verileri
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: 3e40dfbcbe88f424337ee5a32fb3e3aaaddd68d0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460456"
---
# <a name="framework-property-metadata"></a>Çerçeve Özelliği Meta Verileri
Çerçeve özelliği meta verileri seçenekleri, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] mimarisinde WPF çerçeve düzeyinde olduğu düşünülen nesne öğelerinin özellikleri için raporlanır. Genel olarak WPF framework düzeyi atama, işleme, veri bağlama ve özellik sistemi işlevselliklerindeki gibi özelliklerin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sunum API 'Leri ve yürütülebilir dosyaları tarafından işlenmesini gerektirir. Çerçeve özelliği meta verileri, belirli öğe özelliklerinin özelliğe özgü özelliklerini belirlemede bu sistemler tarafından sorgulanır.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 Bu konu başlığı altında, bağımlılık özelliklerini [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıflarında var olan bağımlılık özellikleri tüketicisinin perspektifinden anladığınızı ve [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md)' ı okuduğunuzu varsaymış olursunuz. Ayrıca Read [Dependency özelliği meta verilerini](dependency-property-metadata.md)de kullanmalısınız.  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>Çerçeve özelliği meta verileri tarafından Iletilen Özellikler  
 Çerçeve özelliği meta verileri aşağıdaki kategorilere ayrılabilir:  
  
- Öğe (<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>) etkileyen düzen özellikleri. Özelliği bu ilgili yönleri etkiliyorsa meta verilerde bu bayrakları ayarlayabilir ve ayrıca, Düzen sistemine belirli işleme davranışını ve bilgilerini sağlamak için sınıfınıza <xref:System.Windows.FrameworkElement.MeasureOverride%2A> / <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> yöntemleri de uygulayabilirsiniz. Genellikle, bu tür bir uygulama, özellik meta verilerinde bu düzen özelliklerinden herhangi birinin doğru olduğu ve yalnızca bu ındoğrulamaların yeni bir düzen geçişi istediğini gerektirdiği bağımlılık özelliklerindeki Özellik doğrulamaları olup olmadığını denetler.  
  
- Bir öğenin üst öğesini etkileyen düzen özellikleri (<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>). Bu bayrakların varsayılan olarak ayarlandığı bazı örnekler <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> ve <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>.  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. Varsayılan olarak, bağımlılık özellikleri değerleri almayacaktır. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A>, devralma 'nin bazı denetim birleştirme senaryolarında gerekli olan görsel ağaca da gitmesini sağlar.  
  
    > [!NOTE]
    > Özellik değerleri bağlamındaki "Inherits" terimi, bağımlılık özelliklerine özgü bir şey anlamına gelir; Bu, alt öğelerin, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sisteminin WPF framework düzeyi özelliği nedeniyle üst öğeden gerçek bağımlılık özelliği değerini devraldığı anlamına gelir. Türetilmiş türler aracılığıyla doğrudan yönetilen kod türü ve üyeleri devralma ile hiçbir şey yapmaz. Ayrıntılar için bkz. [özellik değeri devralma](property-value-inheritance.md).  
  
- Raporlama veri bağlama özellikleri (<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>, <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>). Varsayılan olarak, Framework 'ün bağımlılık özellikleri, tek yönlü bağlama davranışı ile veri bağlamayı destekler. Veri bağlamayı devre dışı bırakabilirsiniz (esnek ve Genişletilebilir olmaları amaçlanan için, varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API 'Lerinde bu tür özelliklerden pek çok örnek yoktur). Bağlamayı, bileşen parçaları (<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> bir örnektir) arasında bir denetimin davranışlarını birbirine bağlayan özellikler için iki yönlü bir varsayılana sahip olacak şekilde ayarlayabilir veya iki yönlü bağlamanın kullanıcılar için ortak ve beklenen senaryo (<xref:System.Windows.Controls.TextBox.Text%2A> bir örnektir) olarak ayarlayabilirsiniz. Veri bağlama ile ilgili meta verilerin değiştirilmesi yalnızca varsayılanı etkiler; bağlama başına temelinde, varsayılan olarak her zaman değiştirilebilir. Bağlama modları ve genel olarak bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md).  
  
- Özelliklerin günlüğe kaydetmeyi (<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>) destekleyen uygulamalar veya hizmetler tarafından mi bir de erişilebilir olacağını bildirme. Genel öğeler için, günlüğe kaydetme varsayılan olarak etkinleştirilmez, ancak belirli kullanıcı girdisi denetimleri için seçmeli olarak etkinleştirilir. Bu özelliğin günlüğe kaydetme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama ve tipik olarak, gezinti adımlarında kalıcı olması gereken listeler içindeki kullanıcı seçimleri gibi kullanıcı denetimlerinde ayarlandığı, bu özelliğin okunması amaçlanmıştır. Günlük hakkında daha fazla bilgi için bkz. [gezintiye genel bakış](../app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>FrameworkPropertyMetadata okunuyor  
 Yukarıda bağlı özelliklerden her biri, <xref:System.Windows.FrameworkPropertyMetadata> <xref:System.Windows.UIPropertyMetadata>kendi temel sınıfına eklediği özel özelliklerdir. Bu özelliklerin her biri varsayılan olarak `false` olacaktır. Bu özelliklerin değerini bilmenin önemli olduğu bir özellik için meta veri isteği, döndürülen meta verileri <xref:System.Windows.FrameworkPropertyMetadata>dönüştürmeyi denemeli ve sonra her bir özelliğin değerlerini gerektiği gibi denetlemelidir.  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>Meta verileri belirtme  
 Yeni bir bağımlılık özelliği kaydına meta veri uygulama amaçları için yeni bir meta veri örneği oluşturduğunuzda kullanılacak meta veri sınıfını seçebilirsiniz: temel <xref:System.Windows.PropertyMetadata> veya <xref:System.Windows.FrameworkPropertyMetadata>gibi bazı türetilmiş sınıflar. Genellikle, özellikle özelliğinde özellik sistemi ve düzen ve veri bağlama gibi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işlevleri ile etkileşim varsa <xref:System.Windows.FrameworkPropertyMetadata>kullanmanız gerekir. Daha karmaşık senaryolar için başka bir seçenek de <xref:System.Windows.FrameworkPropertyMetadata>, üyelerinde daha fazla bilgi içeren kendi meta veri raporlama sınıfınızı oluşturacak şekilde türetmektir. Ya da uygulamanızın özelliklerine yönelik destek derecesini iletmek için <xref:System.Windows.PropertyMetadata> veya <xref:System.Windows.UIPropertyMetadata> kullanabilirsiniz.  
  
 Var olan Özellikler (<xref:System.Windows.DependencyProperty.AddOwner%2A> veya <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> çağrısı) için, her zaman geçersiz kılmalı ve özgün kayıt tarafından kullanılan meta veri türü.  
  
 <xref:System.Windows.FrameworkPropertyMetadata> bir örnek oluşturuyorsanız, bu meta verileri çerçeve özelliği özellikleriyle iletişim kuran belirli özellikler için değerlerle doldurmanın iki yolu vardır:  
  
1. `flags` parametreye izin veren <xref:System.Windows.FrameworkPropertyMetadata> Oluşturucu imzasını kullanın. Bu parametre, <xref:System.Windows.FrameworkPropertyMetadataOptions> numaralandırma bayraklarının tüm istenen Birleşik değerleriyle doldurulmalıdır.  
  
2. `flags` parametresi olmadan imzalardan birini kullanın ve <xref:System.Windows.FrameworkPropertyMetadata> her bir raporlama Boolean özelliğini istediğiniz her özellik değişikliği için `true` olarak ayarlayın. Bunu yaparsanız, bu bağımlılık özelliğine sahip herhangi bir öğe oluşturulmadan önce bu özellikleri ayarlamanız gerekir; Boolean özellikleri, `flags` parametresini önlemenin ve meta verileri hala dolduran bu davranışa izin vermek için okuma-yazma ' dır. ancak meta verilerin özellik kullanılmadan önce etkin bir şekilde mühürlenmesi gerekir. Bu nedenle, meta veriler istendiğinde özellikleri ayarlamaya çalışmak geçersiz bir işlem olur.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>Çerçeve özelliği meta verileri birleştirme davranışı  
 Çerçeve özelliği meta verilerini geçersiz kıldığınızda, farklı meta veri özellikleri birleştirilir veya değiştirilmiştir.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> birleştirildi. Yeni bir <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>eklerseniz, bu geri çağırma meta verilerde depolanır. Geçersiz kılmada bir <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> belirtmezseniz, <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> değeri, meta verilerde belirtilen en yakın üst öğesinden bir başvuru olarak yükseltilir.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> için gerçek özellik sistemi davranışı, hiyerarşideki tüm meta veri sahipleri için uygulamalar, özellik sistemi tarafından yürütme sırası, en derin türetilmiş sınıfın geri çağırmaları çağrıldığında adı. Devralınan geri çağrılar yalnızca bir kez çalışır ve bu, meta verilere yerleştirilmiş sınıfa ait olduğu şekilde sayımlardır.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A> değiştirilmiştir. Geçersiz kılmada bir <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> belirtmezseniz, <xref:System.Windows.PropertyMetadata.DefaultValue%2A> değeri, meta verilerde belirtilen en yakın üst öğesinden gelir.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> uygulamalar değiştirilmiştir. Yeni bir <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>eklerseniz, bu geri çağırma meta verilerde depolanır. Geçersiz kılmada bir <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> belirtmezseniz, <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> değeri, meta verilerde belirtilen en yakın üst öğesinden bir başvuru olarak yükseltilir.  
  
- Özellik sistemi davranışı yalnızca anlık Meta verilerdeki <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> çağrılır. Hiyerarşideki diğer <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> uygulamalarına başvuru korunmaz.  
  
- <xref:System.Windows.FrameworkPropertyMetadataOptions> numaralandırması bayrakları bit düzeyinde veya işlem olarak birleştirilir.  <xref:System.Windows.FrameworkPropertyMetadataOptions>belirtirseniz, özgün seçeneklerin üzerine yazılmaz.  Bir seçeneği değiştirmek için <xref:System.Windows.FrameworkPropertyMetadata>ilgili özelliği ayarlayın. Örneğin, özgün <xref:System.Windows.FrameworkPropertyMetadata> nesnesi <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType> bayrağını ayarlarsa, `false`<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> ayarlayarak bunu değiştirebilirsiniz.  
  
 Bu davranış <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>tarafından uygulanır ve türetilmiş meta veri sınıflarında geçersiz kılınabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Bağımlılık Özelliği Meta Verisi](dependency-property-metadata.md)
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
