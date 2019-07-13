---
title: Bağımlılık Özelliği Meta Verisi
ms.date: 03/30/2017
helpviewer_keywords:
- APIs [WPF], metadata
- dependency properties [WPF], metadata
- metadata [WPF], for dependency properties
- overriding metadata [WPF]
ms.assetid: d01ed009-b722-41bf-b82f-fe1a8cdc50dd
ms.openlocfilehash: 66628e8cc1e56bff2227721d6f6b3e511be7453e
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860053"
---
# <a name="dependency-property-metadata"></a>Bağımlılık Özelliği Meta Verisi
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Ne bildirilen bir özellik üzerinden erişiyorsanız hakkında veya genel olabilir ötesine giden sistem raporlama bir meta veri özellik sistemi içerir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] özellikleri. Meta verileri için bir bağımlılık özelliği bir bağımlılık özelliği tanımlayan bir sınıf tarafından da bir benzersiz bir şekilde atanabilir bağımlılık özelliği için farklı bir sınıf eklendiğinde değiştirilebilir ve özellikle devralan tüm türetilmiş sınıfları tarafından geçersiz kılınabilir bağımlılık özelliği tanımlayan temel sınıf.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, üzerinde bir tüketici mevcut bağımlılık özellikleri perspektifinden bağımlılık özellikleri anladığınızı varsayar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıfları ve okuma [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md). Bu konudaki örnekleri izlemek için de anlamanız gereken [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve nasıl yazıldığını bilmeniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.  
  
<a name="dp_metadata_contents"></a>   
## <a name="how-dependency-property-metadata-is-used"></a>Bağımlılık özelliği meta verileri nasıl kullanılır  
 Bağımlılık özelliği meta verisi bağımlılık özelliği özelliklerini incelemek için sorgulanabilir bir nesne olarak bulunmaktadır. Herhangi bir verilen bağımlılık özelliği işlenmesi sırasında bu meta veriler Ayrıca özellik sistemi tarafından sık erişilebilir. Bağımlılık özelliği için meta veri nesnesi, aşağıdaki bilgi türlerini içerebilir:  
  
- Yerel değer, stil, devralma, vb. bağımlılık özelliği için başka bir değer belirlenebilir, bağımlılık özelliği için varsayılan değer. Bağımlılık özellikleri için değerleri atarken özellik sistemi tarafından kullanılan öncelikli nasıl varsayılan değerleri katılan bir tam açıklaması için bkz [bağımlılık özelliği değer önceliği](dependency-property-value-precedence.md).  
  
- Sahibi-tür başına temelinde zorlama veya değişiklik bildirimi davranışlarını etkileyen geri çağırma uygulamaları başvurular. İzin verilen erişim kapsamındaki başvuruları sürece meta verilerinden gerçek başvurular alma genellikle mümkün olmadığından bu geri aramalarda genellikle bir ortak olmayan erişim düzeyiyle tanımlandığına dikkat edin. Bağımlılık özelliği geri aramaları hakkında daha fazla bilgi için bkz. [bağımlılık özelliği geri aramaları ve doğrulama](dependency-property-callbacks-and-validation.md).  
  
- Söz konusu bağımlılık özelliği bir WPF çerçeve düzeyi özelliği olarak kabul edilir, meta veri bilgileri ve durum WPF çerçeve düzeyi gibi hizmetler için rapor WPF çerçeve düzeyi bağımlılık özelliği özellikleriyle içerebilir Yerleşim altyapısı ve özellik devralma mantığı. Bağımlılık özelliği meta verisi bu yönü hakkında daha fazla bilgi için bkz. [çerçeve özelliği meta verileri](framework-property-metadata.md).  
  
<a name="APIs"></a>   
## <a name="metadata-apis"></a>Meta veri API'leri  
 Özellik sistemi tarafından kullanılan meta veri bilgilerini çoğunu rapor türü <xref:System.Windows.PropertyMetadata> sınıfı. Bağımlılık özellikleri, özellik sistemi ile kayıtlı ve yeniden kendilerini sahip olarak ekleyebilir ya da bunların temel sınıf bağımlılığı devralır meta verileri geçersiz kılma ek türleri için belirtilebilir meta veri örnekleri isteğe bağlı olarak belirtilir özellik tanımı. (Burada özelliği kayıt belirtmiyor meta verileri, varsayılan durumlarda <xref:System.Windows.PropertyMetadata> o sınıf için varsayılan değerlerle oluşturulur.) Kayıtlı meta veriler olarak döndürülür <xref:System.Windows.PropertyMetadata> çağırdığınızda çeşitli <xref:System.Windows.DependencyProperty.GetMetadata%2A> bir bağımlılık özelliği meta verilerini al üzerinde aşırı bir <xref:System.Windows.DependencyObject> örneği.  
  
 <xref:System.Windows.PropertyMetadata> Sınıfı ardından türetilen mimari bölümlerinin kenarlık WPF framework düzey sınıflar gibi daha belirli meta verilerini sağlamak için. <xref:System.Windows.UIPropertyMetadata> animasyon raporlama, ekler ve <xref:System.Windows.FrameworkPropertyMetadata> önceki bölümde belirtilen WPF çerçeve düzeyi özellikleri sağlar. Bağımlılık özellikleri kaydettiğinizde, bunlar ile kaydedilebilir <xref:System.Windows.PropertyMetadata> türetilmiş sınıflar. Meta veriler, incelenir, temel <xref:System.Windows.PropertyMetadata> türü potansiyel olarak yayımlanabilir türetilmiş sınıfları, böylece daha belirli özelliklerini inceleyebilirsiniz.  
  
> [!NOTE]
>  İçinde belirtilen özelliği özellikleriyle <xref:System.Windows.FrameworkPropertyMetadata> bu belgede "bayraklar" olarak adlandırılır. Bağımlılık olarak kullanmak için yeni meta veri örnekleri özelliği kayıtları oluşturmak ya da meta verileri geçersiz kılar flagwise numaralandırması kullanarak bu değerleri belirtin <xref:System.Windows.FrameworkPropertyMetadataOptions> ve sonra büyük olasılıkla bitişik numaralandırmadeğerlerinisağlayın<xref:System.Windows.FrameworkPropertyMetadata> Oluşturucusu. Ancak, oluşturulan sonra şu seçeneği özelliklere içinde sunulan bir <xref:System.Windows.FrameworkPropertyMetadata> oluşturma numaralandırma değeri yerine Boole özellikleri bir dizi olarak. Boole özellikleri denetlemenizi her koşullu etkinleştirmek yerine bilgi almak için flagwise numaralandırma değeri için bir maske uygulamanıza gerek ilgilendiğiniz. Oluşturucu birleştirilmiş kullanan <xref:System.Windows.FrameworkPropertyMetadataOptions> gerçek oluşturulan meta verileri daha sezgisel meta verileri sorgulama yapmak için ayrı özellikleri gösterir ancak Oluşturucu imzası uzunluğunu makul, tutulabilmesi için.  
  
<a name="override_or_subclass"></a>   
## <a name="when-to-override-metadata-when-to-derive-a-class"></a>Meta verileri, geçersiz kılma ne zaman bir sınıf türetin  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Özellik sistemi tamamen yeniden uygulanmış olması için bağımlılık özellikleri özelliklerinden bazıları gerek kalmadan değiştirmek için özellikler kurulan. Bu işlem, belirli bir tür üzerinde mevcut olduğundan, bağımlılık özelliği için özellik meta verileri farklı bir örneği oluşturularak gerçekleştirilir. En mevcut bağımlılık özellikleri sanal özellikler değildir, bu nedenle NET olarak söylemek gerekirse "devralınan sınıflar üzerinde yeniden uygularken" yalnızca varolan bir üye gölgeleme tarafından gerçekleştirilmesi dikkat edin.  
  
 Senaryo türü üzerinde bir bağımlılık özelliği mevcut bağımlılık özellikleri özelliklerini değiştirerek elde edilemez etkinleştirmek üzere çalışıyorsanız, bunu daha sonra türetilmiş bir sınıf oluşturmak gerekli olabilir ve sonra özel bir bağımlılık özelliği bildirmek için türetilen. Özel bağımlılık özelliği tarafından tanımlanan bağımlılık özellikleri için aynı şekilde davranır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API'leri. Özel bağımlılık özellikleri hakkında daha fazla ayrıntı için bkz. [özel bağımlılık özellikleri](custom-dependency-properties.md).  
  
 Bir önemli geçersiz kılamaz bir bağımlılık özelliği değer türü özelliğidir. Yaklaşık davranışı bir bağımlılık özelliği devralan varsa gerektirir, ancak farklı bir tür için gerekli, özel bağımlılık özelliği uygulama ve belki de özellikleri tür dönüştürme veya diğer aracılığıyla bağlamanız gerekir Özel sınıfınıza mantığınız. Ayrıca, mevcut bir değiştirilemiyor <xref:System.Windows.ValidateValueCallback>, bu geri çağırma kaydı alan ve meta verileri içinde değil bulunmaktadır.  
  
<a name="scenarios"></a>   
## <a name="scenarios-for-changing-existing-metadata"></a>Var olan meta verileri değiştirme senaryoları  
 Mevcut bir bağımlılık özelliği meta verileri ile çalışıyorsanız, bağımlılık özelliği meta verileri değiştirme sık karşılaşılan bir senaryodur varsayılan değer değiştirmektir. Özellik sistemi geri çağırmaları ekleme veya değiştirme daha gelişmiş bir senaryodur. Bağımlılık özellikleri farklı birbiriyle türetilmiş bir sınıfın uygulamanız varsa, bunu yapmak isteyebilirsiniz. Hem kod hem de bildirim kullanımını destekleyen bir programlama modeli yaşama koşullular herhangi bir sırada ayarlanan özellikler etkinleştirmelisiniz biridir. Bu nedenle herhangi bir bağımlı özellik just-in-time bağlamı olmadan ayarlanmış olması gerekir ve bir ayar sırası gibi bir oluşturucuda bulunabilir bilmenin güvenemezsiniz. Özellik sistemi bu yönü hakkında daha fazla bilgi için bkz. [bağımlılık özelliği geri aramaları ve doğrulama](dependency-property-callbacks-and-validation.md). Doğrulama geri çağırmaları meta veri parçası olmadığını unutmayın. Bunlar, bağımlılık özelliği tanımlayıcı parçasıdır. Bu nedenle, doğrulama geri çağırmaları meta verileri geçersiz kılma tarafından değiştirilemez.  
  
 Bazı durumlarda varolan bağımlılık özellikleri WPF çerçeve düzeyi özelliği meta verileri seçenekleri değiştirmek isteyebilirsiniz. Bu seçenekler, WPF düzen sistemi gibi diğer WPF framework düzeyinde işlemler için çerçeve düzeyi özellikleri hakkında bilinen belirli koşullar iletişim kurar.  Ayar seçenekleri genellikle yapılır yalnızca yeni bir bağımlılık özelliği kaydederken, ancak bir parçası olarak WPF çerçeve düzeyi özelliği meta verileri değiştirmek mümkündür bir <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> veya <xref:System.Windows.DependencyProperty.AddOwner%2A> çağırın. İçin belirli değerleri kullanın ve daha fazla bilgi için bkz. [çerçeve özelliği meta verileri](framework-property-metadata.md). Bu seçenekler için yeni kaydettiğiniz bağımlılık özelliği ayarlanmalıdır nasıl ilgili daha fazla bilgi için bkz. [özel bağımlılık özellikleri](custom-dependency-properties.md).  
  
<a name="dp_override_metadata"></a>   
### <a name="overriding-metadata"></a>Meta verileri geçersiz kılma  
 Meta verileri geçersiz kılma amacı, böylelikle öncelikle, türünüz üzerinde mevcut olduğundan, bağımlılık özelliği için uygulanan çeşitli meta verileri türetilmiş davranışlarını değiştirme olanağına sahiptir. Bunun nedeni, daha ayrıntılı olarak açıklanmıştır [meta verileri](#dp_metadata_contents) bölümü. Bazı kod örnekleri dahil olmak üzere daha fazla bilgi için bkz. [bağımlılık özelliği meta verileri geçersiz kılma](how-to-override-metadata-for-a-dependency-property.md).  
  
 Özellik meta veriler sağladı kayıt aramasında bir bağımlılık özelliği için (<xref:System.Windows.DependencyProperty.Register%2A>). Ancak, çoğu durumda, bu bağımlılık özelliği devraldığında sınıfınız için türe özgü meta veriler sağlamak isteyebilirsiniz. Bunu çağırarak yapmak <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> yöntemi.  Bir örnek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API'leri <xref:System.Windows.FrameworkElement> sınıfı, ilk kaydeden türü <xref:System.Windows.UIElement.Focusable%2A> bağımlılık özelliği. Ancak <xref:System.Windows.Controls.Control> sınıfı ondan değiştirme kendi varsayılan başlangıç değeri sağlamak bağımlılık özelliği için meta verileri geçersiz kılar `false` için `true`, aksi takdirde özgün yeniden kullanır <xref:System.Windows.UIElement.Focusable%2A> uygulaması.  
  
 Meta verileri geçersiz kılma, farklı bir meta veri özelliklerini birleştirilmiş değiştirildi veya olan.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> birleştirilir. Yeni bir eklerseniz <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, bu geri çağırma meta verilerinde depolanır. Belirtmezseniz, bir <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> değerini geçersiz kılma olarak <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> meta verilerinde belirtilen en yakın üst nesneden bir başvuru olarak yükseltilir.  
  
- Gerçek özellik sistemi davranışını <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> hiyerarşideki tüm meta veri sahipleri için uygulamaları korunur ve özellik sistemi tarafından yürütme sırası içeren bir tablo en çok türetilen sınıfın geri çağırmaları önce çağrılır emin olmasına eklenir.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A> değiştirilir. Belirtmezseniz, bir <xref:System.Windows.PropertyMetadata.DefaultValue%2A> değerini geçersiz kılma olarak <xref:System.Windows.PropertyMetadata.DefaultValue%2A> meta verilerinde belirtilen en yakın üst öğesinden gelir.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> uygulamaları değiştirilir. Yeni bir eklerseniz <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, bu geri çağırma meta verilerinde depolanır. Belirtmezseniz, bir <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> değerini geçersiz kılma olarak <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> meta verilerinde belirtilen en yakın üst nesneden bir başvuru olarak yükseltilir.  
  
- Özellik sistemi yalnızca davranıştır <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> hemen meta verilerde çağrılır. Başvuru diğer <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> hiyerarşi uygulamalarında korunur.  
  
 Bu davranış tarafından uygulanan <xref:System.Windows.PropertyMetadata.Merge%2A>ve türetilmiş meta veri sınıflarında geçersiz kılınabilir.  
  
#### <a name="overriding-attached-property-metadata"></a>İliştirilmiş özellik meta verileri geçersiz kılma  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]iliştirilmiş özellikler, bağımlılık özellikleri uygulanır. Bu, ayrıca hangi belirli sınıfları geçersiz kılabilirsiniz özellik meta verilerini sahip oldukları anlamına gelir. Ekli bir özellik için kapsam belirleme konuları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] herhangi olan genellikle <xref:System.Windows.DependencyObject> ekli özelliği kendileri için ayarlanmış olabilir. Bu nedenle, tüm <xref:System.Windows.DependencyObject> türetilmiş sınıf geçersiz kılma herhangi bir ekli özelliği için meta veriler gibi bir sınıf örneği üzerinde ayarlanabilir. Varsayılan değerleri, geri çağırmaları ya da WPF çerçeve düzeyi özelliği raporlama özellikleri geçersiz kılabilirsiniz. Ekli özellik, sınıfın örneğini ayarlarsanız, özellikleri uygulama özelliği meta verileri geçersiz kılar. Örneğin, varsayılan değer, geçersiz kılma değerinizi sınıfınızın örneklerine ekli özellik değeri olarak bildirilen şekilde her özellik Aksi takdirde ayarlanmamıştır geçersiz kılabilirsiniz.  
  
> [!NOTE]
>  <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> Özelliği iliştirilmiş özellikler için uygun değil.  
  
<a name="dp_add_owner"></a>   
### <a name="adding-a-class-as-an-owner-of-an-existing-dependency-property"></a>Mevcut bir bağımlılık özelliği bir sahibi olarak sınıf ekleme  
 Bir sınıfın kendisi sahibi zaten, kullanarak kayıtlı bir bağımlılık özelliği olarak ekleyebilirsiniz <xref:System.Windows.DependencyProperty.AddOwner%2A> yöntemi. Bu, başlangıçta kayıtlı bir bağımlılık özelliği için farklı bir tür kullanmak için sınıf sağlar. Ekleme sınıf genellikle ilk sahibi olarak bu bağımlılık özelliği kayıtlı türü türetilmiş bir sınıf değil. Etkili bir şekilde, bu, sınıf ve "bir bağımlılık özelliği uygulama özgün sahibi sınıfı olmadan devralmak için" türetilmiş sınıfları ve aynı gerçek sınıf hiyerarşisinde olmasına ekleme sınıfı sağlar. Ardından eklenmesi, sınıf ekleme (ve tüm türetilmiş sınıfları) özgün bağımlılık özelliği için türe özgü meta veriler sağlayabilir.  
  
 Kendisini sahibi olarak özelliği sistem yardımcı yöntemler ekleme yanı sıra, ekleme sınıfına ek ortak üyeleri kendisine bağımlılık özelliği yapmak için bildirmelidir] özellik sistemi ile hem kod hem de biçimlendirme maruz kalma riskinizi tam bir katılımcı . Mevcut bir bağımlılık özelliği ekleyen bir sınıf, yeni özel bağımlılık özelliği tanımlayan bir sınıf olarak sunulan ürünün kendinde gösterme, bağımlılık özelliği için nesne modeli aynı sorumlulukları vardır. İlk kez kullanıma sunmak için bu tür bir bağımlılık özelliği tanımlayıcı alanı üyesidir. Bu alan olmalıdır bir `public static readonly` türü alanını <xref:System.Windows.DependencyProperty>, dönüş değeri olarak atanan <xref:System.Windows.DependencyProperty.AddOwner%2A> çağırın. İkinci üye tanımlamak için [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] "sarmalayıcı" özelliği. Sarmalayıcı, kodda, bağımlılık özelliği işlemek çok daha kolay kılar (çağrıları önlemek <xref:System.Windows.DependencyObject.SetValue%2A> her zaman ve kapsayıcı içinde yalnızca bir kez bu çağrı yapabilirsiniz). Sarmalayıcı, özel bir bağımlılık özelliği kaydettirmekte, nasıl da uygulanması için aynı şekilde uygulanır. Bağımlılık özelliği uygulama hakkında daha fazla bilgi için bkz. [özel bağımlılık özellikleri](custom-dependency-properties.md) ve [bağımlılık özelliği için sahip türü ekleme](how-to-add-an-owner-type-for-a-dependency-property.md).  
  
#### <a name="addowner-and-attached-properties"></a>AddOwner ve ekli özellikler  
 Çağırabilirsiniz <xref:System.Windows.DependencyProperty.AddOwner%2A> ekli özelliği sahibi sınıfı tarafından tanımlanan bir bağımlılık özelliği için. Genellikle bunu nedeni bağlı olmayan bir bağımlılık özelliği olarak daha önce ekli özellik kullanıma sunulmasıdır. Ardından açığa çıkarır <xref:System.Windows.DependencyProperty.AddOwner%2A> dönüş değeri olarak bir `public static readonly` bağımlılık özelliği tanımlayıcı olarak kullanılacak alanı ve özellik üyeler tablosunda görünür ve ekli olmayan bir özelliğini destekleyen uygun bir "sarmalayıcı" özellikleri tanımlar sınıfınıza kullanımı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.PropertyMetadata>
- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Çerçeve Özelliği Meta Verileri](framework-property-metadata.md)
