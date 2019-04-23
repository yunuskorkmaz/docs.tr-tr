---
title: Çerçeve Özelliği Meta Verileri
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: 2a20e5a2bdbcbb36f6f06bbbadb2a46743ca5eba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314704"
---
# <a name="framework-property-metadata"></a>Çerçeve Özelliği Meta Verileri
Çerçeve özelliği meta verileri seçenekleri nesne öğelerini WPF framework düzeyde olduğu kabul özelliklerinin raporlanır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] mimarisi. Genel olarak, işleme, veri bağlama gibi özelliklerin WPF çerçeve düzeyi atamasını gerektirir ve özellik sistemi daraltmalar tarafından işlenmesini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sunu [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] ve yürütülebilir dosyalar. Çerçeve özelliği meta verileri, belirli bir öğe özelliklerinin özelliğe özgü özellikleri belirlemek için bu sistemler tarafından sorgulanır.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, üzerinde bir tüketici mevcut bağımlılık özellikleri perspektifinden bağımlılık özellikleri anladığınızı varsayar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıfları ve okuma [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md). Ayrıca okuma [bağımlılık özelliği meta verisi](dependency-property-metadata.md).  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>Çerçeve özelliği meta verileri tarafından İletilenleri  
 Çerçeve özelliği meta verileri aşağıdaki kategorilere ayrılabilir:  
  
-   Bir öğeyi etkileyen düzen özelliklerini raporlama (<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>). Bu bayraklar özellik ilgili yönleri etkiler ve ayrıca uygulama meta verilerinde ayarlayabilir <xref:System.Windows.FrameworkElement.MeasureOverride%2A>  /  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> sınıfınızın belirli bir işleme davranışını ve düzeni bilgileri sağlamak için yöntemleri sistemi. Genellikle, bu tür bir uygulama özelliği geçersiz kılmalar burada bu düzen özelliklerinden herhangi birini özellik meta verilerinde true ve yeni bir düzen geçişi yalnızca o geçersiz kılmalar istediğinde bağımlılık özellikleri için denetler.  
  
-   Bir öğenin üst öğesi etkileyen düzen özelliklerini raporlama (<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>). Bu bayrak varsayılan olarak ayarlanmış olduğu bazı örnekler <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> ve <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>.  
  
-   <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. Varsayılan olarak, bağımlılık özellikleri değerlerini devralmaz. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A> Ayrıca bazı denetim birleştirme senaryolar için gerekli olan bir görsel ağacında seyahat Devralmanın yol sağlar.  
  
    > [!NOTE]
    >  Terim "özellik değerleri anlamına gelir bağımlılık özellikleri için özel bir durum bağlamında devralır"; alt öğeleri nedeniyle WPF çerçeve düzeyi özelliği üst öğelerden gerçek bağımlılık özelliği değer devralabilir geldiğini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistemi. Yönetilen kod türü ve üyeleri devralma yoluyla türetilmiş türler ile doğrudan yapılacak bir şey yok sahiptir. Ayrıntılar için bkz [özellik değeri kalıtımı](property-value-inheritance.md).  
  
-   Raporlama veri bağlama özellikleri (<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>, <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>). Varsayılan olarak, Framework bağımlılık özellikleri ile tek yönlü bağlama davranışı veri bağlamayı destekler. Varsa bir senaryo için gerekli veri bağlama devre dışı bırakabilirsiniz (esnek ve Genişletilebilir olmasını yönelik olduğundan, birçok örnekleri gibi özellikleri varsayılan yok [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]). Varsayılan denetim davranışlarını bağlamayı, bileşen parçalarında birbirine özellikleri için iki yönlü bir bağlama kümesi (<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> bir örnek verilmiştir) veya iki yönlü bir bağlama, kullanıcılar için genel ve beklenen senaryo olduğu (<xref:System.Windows.Controls.TextBox.Text%2A> örneğidir). Veri bağlama ile ilgili meta verileri değiştirme, yalnızca varsayılan etkiler; Varsayılan değer her zaman değiştirilebilir bir bağlama başına temelinde. Bağlama modları ve genel bağlama hakkında daha fazla bilgi için bkz: [Data Binding Overview](../data/data-binding-overview.md).  
  
-   Uygulamalar veya günlük kaydı destekleyen hizmetler tarafından özellikleri günlük kaydının tutulup tutulmamasını raporlama (<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>). Genel öğeler için günlük kaydı varsayılan olarak etkinleştirilmemiştir ancak seçmeli olarak belirli bir kullanıcı girişi denetimlerinden için etkin. Bu özellik dahil olmak üzere, günlük kaydı hizmetleri tarafından okunacak şekilde tasarlanmıştır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] günlük kaydı, uygulama ve genellikle kullanıcı denetimleri gibi Gezinti adımları kalıcı liste içindeki kullanıcı seçimleri ayarlanır. Günlüğü hakkında daha fazla bilgi için bkz. [gezintiye genel bakış](../app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>FrameworkPropertyMetadata Okuma  
 Yukarıdaki bağlı özelliklerin her biri belirli özellikleri olan, <xref:System.Windows.FrameworkPropertyMetadata> anında, temel sınıfına ekler <xref:System.Windows.UIPropertyMetadata>. Bu özelliklerin her biri olacak `false` varsayılan olarak. Bu özelliklerin değerini bilerek olduğu önemli bir özellik için meta veri isteği için döndürülen meta verilere cast aygıtyla <xref:System.Windows.FrameworkPropertyMetadata>ve gerektiği gibi tek tek özellikleri değerlerini kontrol edin.  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>Meta veri belirtme  
 Meta verileri için yeni bir bağımlılık özelliği kaydı uygulama yeni bir meta veri örneği amacıyla oluşturduğunuzda, kullanmak için hangi meta veri sınıfının seçenekleriniz vardır: temel <xref:System.Windows.PropertyMetadata> veya türetilmiş bir sınıf gibi <xref:System.Windows.FrameworkPropertyMetadata>. Genel olarak, kullanmanız gereken <xref:System.Windows.FrameworkPropertyMetadata>özellikle özelliğinizi özellik sistemi herhangi bir etkileşim varsa ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen ve veri bağlama gibi işlevler. Türetmek için daha Gelişmiş senaryolar için başka bir seçenek olan <xref:System.Windows.FrameworkPropertyMetadata> kendi meta verileri raporlama sınıfını ek bilgilerle üyelerinde taşınan. Veya kullanabileceğinize <xref:System.Windows.PropertyMetadata> veya <xref:System.Windows.UIPropertyMetadata> uygulamanızın özellikleri için destek derecesini iletişim kurmak için.  
  
 Mevcut özellikler için (<xref:System.Windows.DependencyProperty.AddOwner%2A> veya <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> çağrısı), her zaman özgün kaydı tarafından kullanılan meta veri türü ile geçersiz kılmanız.  
  
 Oluşturuyorsanız bir <xref:System.Windows.FrameworkPropertyMetadata> örnek, meta verilerin çerçeve özelliği özellikleriyle iletişim kuran belirli özellikleri için değerlerle doldurmak için iki yolu vardır:  
  
1. Kullanım <xref:System.Windows.FrameworkPropertyMetadata> veren Oluşturucu imzasının bir `flags` parametresi. Bu parametre istenen tüm birleştirilmiş değerlerle doldurulacak <xref:System.Windows.FrameworkPropertyMetadataOptions> numaralandırma bayrakları.  
  
2. İmzaları birini bir `flags` parametresi ve her raporlama Boolean özelliğini ayarlayın <xref:System.Windows.FrameworkPropertyMetadata> için `true` her istenen özellik değişiklik için. Bunu yaparsanız, bu bağımlılık özelliği ile herhangi bir öğe oluşturulmadan önce bu özelliklerini ayarlamalısınız; Boole özellikleri önleme davranışına izin vermek için okuma-yazma `flags` parametresi ve meta veriler hala doldurmak, ancak meta veri özelliği kullanılmadan önce etkili bir şekilde korumalı hale getirilmelidir. Bu nedenle, meta verileri istendikten sonra özellikleri ayarlama girişimi geçersiz bir işlem olacaktır.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>Çerçeve özelliği meta verileri birleştirme davranışı  
 Çerçeve özelliği meta verileri geçersiz kıldığınızda, farklı bir meta veri özelliklerini birleştirilmiş değiştirildi veya olan.  
  
-   <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> birleştirilir. Yeni bir eklerseniz <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, bu geri çağırma meta verilerinde depolanır. Belirtmezseniz, bir <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> değerini geçersiz kılma olarak <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> meta verilerinde belirtilen en yakın üst nesneden bir başvuru olarak yükseltilir.  
  
-   Gerçek özellik sistemi davranışını <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> uygulamaları ile en derin bir şekilde türetilen sınıfın geri çağırmaları olan özellik sistemi tarafından yürütme sırası için tüm meta veri sahipler hiyerarşide korunur ve bir tabloya eklenen olduğunu unutmayın önce çağrılır. Meta verilerde yerleştiren sınıfı tarafından sahip olunan olarak sayım devralınan geri çağırmaları yalnızca bir kez çalıştırın.  
  
-   <xref:System.Windows.PropertyMetadata.DefaultValue%2A> değiştirilir. Belirtmezseniz, bir <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> değerini geçersiz kılma olarak <xref:System.Windows.PropertyMetadata.DefaultValue%2A> meta verilerinde belirtilen en yakın üst öğesinden gelir.  
  
-   <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> uygulamaları değiştirilir. Yeni bir eklerseniz <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, bu geri çağırma meta verilerinde depolanır. Belirtmezseniz, bir <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> değerini geçersiz kılma olarak <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> meta verilerinde belirtilen en yakın üst nesneden bir başvuru olarak yükseltilir.  
  
-   Özellik sistemi yalnızca davranıştır <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> hemen meta verilerde çağrılır. Başvuru diğer <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> hiyerarşi uygulamalarında korunur.  
  
-   Bayraklarını <xref:System.Windows.FrameworkPropertyMetadataOptions> numaralandırması bir bit düzeyinde OR işlem birleştirilir.  Belirtirseniz <xref:System.Windows.FrameworkPropertyMetadataOptions>, özgün seçenekleri geçersiz kılınmaz.  Seçeneği değiştirmek için karşılık gelen özelliği ayarlamak <xref:System.Windows.FrameworkPropertyMetadata>. Örneğin, özgün <xref:System.Windows.FrameworkPropertyMetadata> nesne kümeleri <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType> bayrak ayarlayarak, değiştirebilirsiniz <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> için `false`.  
  
 Bu davranış tarafından uygulanan <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>ve türetilmiş meta veri sınıflarında geçersiz kılınabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Bağımlılık Özelliği Meta Verisi](dependency-property-metadata.md)
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
