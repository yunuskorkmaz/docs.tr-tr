---
title: Çerçeve Özelliği Meta Verileri
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: d968bc7a3033bd994590520c5cd5062d3c212b4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547468"
---
# <a name="framework-property-metadata"></a>Çerçeve Özelliği Meta Verileri
Framework özellik meta veri seçenekleri WPF framework düzeyde olarak kabul nesne öğelerin özellikleri için bildirilen [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] mimarisi. Genel olarak, işleme, veri bağlama gibi bu özellikleri WPF çerçeve düzeyi ataması kapsar ve özellik sistem iyileştirmelerini tarafından işlenmesini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sunu [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] ve yürütülebilir. Çerçeve özellik meta verileri, belirli öğe özelliklerinin özelliğe özgü özellikleri belirlemek için bu sistemler tarafından sorgulanır.  
  
 
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu bağımlılık özellikleri varolan bağımlılık özelliklerinin tüketicisi açısından anladığınızı varsayar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıfları ve okuma [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Ayrıca okumalısınız [bağımlılık özelliği meta verileri](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>Framework özellik meta verileri ile İletilenleri  
 Çerçeve özellik meta verileri aşağıdaki kategorilere ayrılabilir:  
  
-   Bir öğeyi etkileyen yerleşim özelliklerini raporlama (<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>). Bu bayrakların özelliği ilgili yönleri etkiler ve ayrıca uygulama meta verilerde ayarlayabilir <xref:System.Windows.FrameworkElement.MeasureOverride%2A>  /  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> özel işleme davranışını ve düzeni bilgileri sağlamak için sınıfı yöntemleri Sistem. Genellikle, burada bu düzeni özelliklerden herhangi birini özellik meta verilerinde true ve yalnızca o geçersiz kılmalar yeni bir düzen geçişi istediğinde bağımlılık özelliklerinde özellik geçersiz kılmalar için gibi bir uygulama denetler.  
  
-   Bir öğenin üst öğesinin etkileyen yerleşim özelliklerini raporlama (<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>). Bu bayrak varsayılan olarak ayarlanmış olduğu bazı örnekler <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> ve <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>.  
  
-   <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. Varsayılan olarak, bağımlılık özellikleri değerlerini devralmaz. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A> Ayrıca bazı denetim birleştirme senaryolar için gerekli olan bir görsel ağaç içine seyahat devralma izlediğiniz sağlar.  
  
    > [!NOTE]
    >  Terim "özellik değerleri anlamına gelir bağımlılık özellikleri için belirli bir şey bağlamında devralır"; alt öğeler bir WPF çerçeve düzeyi yeteneğini nedeniyle üst öğelerden fiili bağımlılık özelliği değerinin devrettiği anlamına gelir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistemi. Yönetilen kod türü ve üyeler devralma türetilmiş türler yoluyla ile doğrudan ilgisi vardır. Ayrıntılar için bkz [özellik değeri devralma](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
-   Veri bağlama özelliklerini raporlama (<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>, <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>). Varsayılan olarak, bağımlılık özellikleri Framework'te tek yönlü bağlama davranışı ile veri bağlamayı destekler. Doğabilecek hiçbir senaryoda olsaydı veri bağlama devre dışı bırakabilir (esnek ve Genişletilebilir olacak şekilde yönelik olduğundan, birçok örnekleri gibi özellikleri varsayılan yok [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]). Varsayılan bağlamayı, bileşen parçalarında denetim davranışlarını birbirine bağlayan özellikler için iki yönlü bir bağlama ayarlayabilir (<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> örneğidir) veya çift yönlü bağlamanın kullanıcılar için ortak ve beklenen senaryo olduğu (<xref:System.Windows.Controls.TextBox.Text%2A> örnek). Veri bağlama ile ilgili meta verileri değiştirme, yalnızca varsayılan etkiler; Varsayılan değer her zaman değiştirilebilir bir bağlama başına temelinde. Genel olarak bağlama ve bağlama modları hakkında daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   Uygulamalar veya günlük kaydı Destek Hizmetleri tarafından özellikleri günlük kaydının tutulup tutulmamasını raporlama (<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>). Genel öğeler için günlük kaydı varsayılan olarak etkin değildir, ancak belirli bir kullanıcı giriş denetimleri için seçmeli olarak etkinleştirilir. Bu özellik de dahil olmak üzere günlük kaydı hizmetleri tarafından okunacak şekilde tasarlanmıştır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] günlüğe kaydetme, uygulama ve genellikle gezinti adımlarında kalıcı listeler içindeki kullanıcı seçimleri gibi kullanıcı denetimlerinde özel olarak ayarlayın. Günlük hakkında daha fazla bilgi için bkz: [Gezinti genel bakış](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>FrameworkPropertyMetadata Okuma  
 Yukarıdaki bağlı özelliklerin her biri olan belirli özellikler, <xref:System.Windows.FrameworkPropertyMetadata> hemen kendi temel sınıfının ekler <xref:System.Windows.UIPropertyMetadata>. Bu özelliklerin her biri olacak `false` varsayılan olarak. Bu özellikler değerini bilerek olduğu önemli bir özellik için meta veri isteği döndürülen meta yayınlanamıyor denemelidir <xref:System.Windows.FrameworkPropertyMetadata>ve gerektiği gibi tek tek özellikleri değerlerini kontrol edin.  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>Meta veri belirtme  
 Meta verileri için yeni bir bağımlılık özelliği kaydı uygulama yeni bir meta veri örneği amacıyla oluşturduğunuzda, hangi meta veri sınıfını kullanmak için seçenekleriniz vardır: temel <xref:System.Windows.PropertyMetadata> veya türetilmiş bir sınıf gibi <xref:System.Windows.FrameworkPropertyMetadata>. Genel olarak, kullanmanız gereken <xref:System.Windows.FrameworkPropertyMetadata>, özellikle, herhangi bir özellik sistemi etkileşimi özelliğine sahipse ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen ve veri bağlama gibi işlevleri. Öğesinden türetilen için daha karmaşık senaryolar için başka bir seçenek olan <xref:System.Windows.FrameworkPropertyMetadata> kendi meta verileri oluşturmak için raporlama sınıfını ek bilgilerle üyelerinde taşınan. Veya kullanabileceğinize <xref:System.Windows.PropertyMetadata> veya <xref:System.Windows.UIPropertyMetadata> uygulamanızın özellikleri için destek derecesini iletişim kurmak için.  
  
 Var olan özellikleri (<xref:System.Windows.DependencyProperty.AddOwner%2A> veya <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> çağrısı), her zaman özgün kayıt tarafından kullanılan meta veri türüyle geçersiz kılmalısınız.  
  
 Oluşturuyorsanız, bir <xref:System.Windows.FrameworkPropertyMetadata> örneği, bu meta verileri çerçeve özelliği özellikleriyle iletişim belirli özelliklerine ilişkin değerleri ile doldurmanın iki yolu vardır:  
  
1.  Kullanım <xref:System.Windows.FrameworkPropertyMetadata> sağlayan Oluşturucusu imza bir `flags` parametresi. Bu parametre, istenen tüm birleşik değerlerle doldurulmalıdır <xref:System.Windows.FrameworkPropertyMetadataOptions> numaralandırma bayrakları.  
  
2.  İmzaları birini kullanın bir `flags` parametresi ve her raporlama Boolean özelliğini ayarlayın <xref:System.Windows.FrameworkPropertyMetadata> için `true` her özellik değiştirmesi istenen için. Bunu yaparsanız, bu bağımlılık özelliği ile herhangi bir öğe oluşturulmadan önce bu özellikleri ayarlamanız gerekir; Boole özellikleri önleme davranışına izin vermek için okuma-yazma `flags` parametre ve meta verileri hala doldurmak ancak meta veri özelliği kullanılmadan önce etkili bir şekilde korumalı hale getirilmelidir. Bu nedenle, meta verileri talep sonra özellikleri ayarlama girişimi geçersiz bir işlem olacaktır.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>Framework özellik meta verileri birleştirme davranışı  
 Çerçeve özellik meta verileri geçersiz kıldığınızda, farklı meta verilerin özellikleri birleştirilmiş değiştirildi ya.  
  
-   <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> birleştirilir. Yeni bir eklerseniz <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, bu geri çağırma meta verilerinde depolanır. Belirtmezseniz, bir <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> değerini geçersiz kılar <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> meta verilerde belirtilen en yakın üst içinden bir başvuru olarak yükseltilir.  
  
-   Gerçek özellik sistem davranışı <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> uygulamaları hiyerarşideki tüm meta veri sahipleri korunur ve bir tabloya eklenen için geri çağırmaları en derinde türetilmiş sınıf olan özellik sistemi tarafından yürütme sırasını sahip değildir önce çağrılır. Devralınan geri çağırmalar yalnızca bir kez, meta verilerde yerleştiren sınıfı tarafından sahip olunan olarak sayım çalıştırın.  
  
-   <xref:System.Windows.PropertyMetadata.DefaultValue%2A> değiştirilir. Belirtmezseniz, bir <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> değerini geçersiz kılar <xref:System.Windows.PropertyMetadata.DefaultValue%2A> meta verilerde belirtilen en yakın üst öğesinden gelir.  
  
-   <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> uygulamaları değiştirilir. Yeni bir eklerseniz <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, bu geri çağırma meta verilerinde depolanır. Belirtmezseniz, bir <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> değerini geçersiz kılar <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> meta verilerde belirtilen en yakın üst içinden bir başvuru olarak yükseltilir.  
  
-   Özellik sistem yalnızca davranıştır <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> hemen meta verilerde çağrılır. Başvuru diğer <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> hiyerarşi uygulamalarında korunur.  
  
-   Bayraklarını <xref:System.Windows.FrameworkPropertyMetadataOptions> numaralandırma bit düzeyinde OR işlemi olarak birleştirilir.  Belirtirseniz <xref:System.Windows.FrameworkPropertyMetadataOptions>, özgün seçenekleri geçersiz kılınmaz.  Bir seçeneği değiştirmek için ilgili özelliği ayarlayın <xref:System.Windows.FrameworkPropertyMetadata>. Örneğin, varsa özgün <xref:System.Windows.FrameworkPropertyMetadata> nesne kümeleri <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType> bayrağını ayarlayarak, değiştirebilirsiniz <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> için `false`.  
  
 Bu davranış tarafından uygulanan <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>ve türetilmiş meta veri sınıflarında geçersiz kılınabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.DependencyProperty.GetMetadata%2A>  
 [Bağımlılık Özelliği Meta Verisi](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [Bağımlılık Özelliklerine Genel Bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Özel Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
