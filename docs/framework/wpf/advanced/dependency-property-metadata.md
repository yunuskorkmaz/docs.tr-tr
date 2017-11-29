---
title: "Bağımlılık Özelliği Meta Verisi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- APIs [WPF], metadata
- dependency properties [WPF], metadata
- metadata [WPF], for dependency properties
- overriding metadata [WPF]
ms.assetid: d01ed009-b722-41bf-b82f-fe1a8cdc50dd
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 69f7a5af655586a62776a8c470f2e1c9811f91d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="dependency-property-metadata"></a>Bağımlılık Özelliği Meta Verisi
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Özellik sistemi ne bildirilen bir özellik yansıma aracılığıyla hakkında veya genel olabilir ötesine gider sistem raporlama meta verileri içeren [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] özellikleri. Meta veri bağımlılık özelliği bir bağımlılık özelliği tanımlayan bir sınıf tarafından da bir benzersiz olarak atanabilir için bağımlılık özelliği için farklı bir sınıf eklendiğinde değiştirilebilir ve özellikle devralan tüm türetilmiş sınıfları tarafından geçersiz kılınabilir bağımlılık özelliği tanımlayıcı temel sınıfından.  
  
 
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu bağımlılık özellikleri varolan bağımlılık özelliklerinin tüketicisi açısından anladığınızı varsayar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sınıfları ve okuma [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Bu konudaki örnekleri takip etmek için ayrıca anlamanız gereken [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve nasıl yazıldığını bilmeniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.  
  
<a name="dp_metadata_contents"></a>   
## <a name="how-dependency-property-metadata-is-used"></a>Bağımlılık özelliği meta verileri nasıl kullanılır  
 Bağımlılık özelliği meta verileri, bir bağımlılık özelliği özelliklerini incelemek için sorgulanabilir bir nesne olarak bulunmaktadır. Verilen bağımlılık özelliği işlerken bu meta veriler Ayrıca sık özellik sistemi tarafından erişilebilir. Meta veri nesnesi bir bağımlılık özelliği için aşağıdaki bilgi türlerini içerebilir:  
  
-   Yerel değerin, stil, devralma, vb. bağımlılık özelliği için başka bir değer belirlenebilir, bağımlılık özelliği için varsayılan değer. Varsayılan değerleri bağımlılık özelliklerinin değerlerini atarken özellik sistemi tarafından kullanılan öncelik nasıl katılan ilişkin kapsamlı hakkında bilgi için bkz [bağımlılık özelliği değeri önceliği](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).  
  
-   Zorlama ya da değişiklik bildirimi davranışları sahibi-tür başına temelinde etkileyen geri çağırma uygulamaları başvurular. Başvuruları, izin verilen erişim kapsamı içinde olmadıkça gerçek başvurular meta verilerini alma genellikle mümkün değildir bu geri aramalar genellikle ortak olmayan erişim düzeyiyle tanımlanan unutmayın. Bağımlılık özelliği geri çağrıları hakkında daha fazla bilgi için bkz: [bağımlılık özelliği geri çağrıları ve doğrulama](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
-   Söz konusu bağımlılık özelliği bir WPF çerçeve düzeyi özelliği olarak değerlendirilir, meta veri bilgileri ve WPF çerçeve düzeyi gibi hizmetler için durumu rapor WPF çerçeve düzeyi bağımlılık özelliği özellikleriyle içerebilir Düzen motoru ve özellik devralma mantığı. Bağımlılık özelliği meta verileri bu yönünün hakkında daha fazla bilgi için bkz: [Framework özellik meta verileri](../../../../docs/framework/wpf/advanced/framework-property-metadata.md).  
  
<a name="APIs"></a>   
## <a name="metadata-apis"></a>Meta veri API'leri  
 Özellik sistemi tarafından kullanılan meta veri bilgilerinin çoğunu raporları türü <xref:System.Windows.PropertyMetadata> sınıfı. Bağımlılık özellikleri özellik sistemi ile kaydedilen ve yeniden kendilerini sahipleri olarak ekleme veya temel sınıf bağımlılık devralınan meta veriyi geçersiz kılmak ek türleri için belirtilebilir meta veri örnekleri isteğe bağlı olarak belirtilmiş özellik tanımı. (Burada özelliği kayıt belirtmiyor meta verileri, varsayılan durumlarda <xref:System.Windows.PropertyMetadata> Bu sınıf için varsayılan değerlerle oluşturulur.) Kayıtlı meta veri olarak döndürülür <xref:System.Windows.PropertyMetadata> çağırdığınızda çeşitli <xref:System.Windows.DependencyProperty.GetMetadata%2A> bir bağımlılık özellikten meta verileri alma üzerinde aşırı bir <xref:System.Windows.DependencyObject> örneği.  
  
 <xref:System.Windows.PropertyMetadata> Sınıfı sonra türetilen WPF çerçeve düzeyi sınıflar gibi mimari bölümler için daha özel meta verilerini sağlamak için. <xref:System.Windows.UIPropertyMetadata>animasyon raporlama, ekler ve <xref:System.Windows.FrameworkPropertyMetadata> önceki bölümde belirtildiği WPF çerçeve düzeyi özellikleri sağlar. Bağımlılık özellikleri kayıtlı olduğunda bunlar bunlarla kaydedilebilir <xref:System.Windows.PropertyMetadata> türetilmiş sınıfları. Meta veriler ne zaman incelenir, temel <xref:System.Windows.PropertyMetadata> türü olası dönüştürülür türetilen sınıflar, böylece daha belirli özellikler inceleyebilirsiniz.  
  
> [!NOTE]
>  İçinde belirtilen özellik özelliklere <xref:System.Windows.FrameworkPropertyMetadata> bu belgede "bayrakları" olarak adlandırılır. Özellik kayıtlar bağımlılık olarak kullanmak için yeni meta veri örnekleri oluşturduğunuzda ya da meta verileri geçersiz kılar flagwise numaralandırma kullanarak bu değerleri belirtin <xref:System.Windows.FrameworkPropertyMetadataOptions> ve sonra büyük olasılıkla Birleştirilmiş numaralandırmadeğerlerinisağlayın<xref:System.Windows.FrameworkPropertyMetadata> Oluşturucusu. Ancak, oluşturulan sonra bu seçenek özelliklere içinde sunulan bir <xref:System.Windows.FrameworkPropertyMetadata> oluşturma numaralandırma değeri yerine Boole özellikleri dizisi olarak. Her koşullu denetlemek Boolean özellikler etkinleştirmeniz yerine bir maskesi bilgi almak için bir flagwise numaralandırma değeri uygulama gerek ilgilendiğiniz. Oluşturucusu birleştirilmiş kullanan <xref:System.Windows.FrameworkPropertyMetadataOptions> gerçek oluşturulan meta verileri daha sezgisel meta verileri Sorgulama olmak için ayrık özellikleri sunar ancak Oluşturucusu imza uzunluğu makul, korumak için.  
  
<a name="override_or_subclass"></a>   
## <a name="when-to-override-metadata-when-to-derive-a-class"></a>Meta verileri, geçersiz kılmak ne zaman bir sınıf türetin zamanı  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Özellik sistemi tamamen yeniden uygulanan olmasını gerek kalmadan bazı bağımlılık özellikleri özelliklerini değiştirmek için özellikler kurulan. Bu, bağımlılık özelliği için özellik meta verileri farklı bir örneğine belirli bir türü üzerinde mevcut olduğundan oluşturarak elde edilir. Unutmayın en varolan bağımlılık özellikleri sanal özellikleri olmayan bakıldığında bu nedenle kesinlikle "bunları devralınan sınıflarda yeniden uygulamak" yalnızca var olan üye gölgeleme tarafından gerçekleştirilmesi.  
  
 Senaryo, varolan bağımlılık özellikleri özelliklerini değiştirerek bir türünde bir bağımlılık özelliği elde edemiyor için etkinleştirmek çalışıyorsanız, ardından türetilmiş bir sınıf oluşturmak gerekli olabilir ve ardından özel bir bağımlılık özelliği bildirmek için üzerinde türetilmiş sınıf. Özel bir bağımlılık özelliği tarafından tanımlanan bağımlılık özellikleri için aynı şekilde davranır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]. Özel bağımlılık özellikleri hakkında daha fazla ayrıntı için bkz: [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
 Bir önemli geçersiz kılınamaz bir bağımlılık özelliği değer türü özelliğidir. Yaklaşık davranışı bir bağımlılık özelliği devralma varsa gerektirir, ancak farklı bir tür için gerektirir, özel bir bağımlılık özelliği uygulamak ve tür dönüştürmeleri veya diğer özelliklerinden belki bağlantı gerekir uygulama özel sınıfınızın. Ayrıca, varolan değiştirilemiyor <xref:System.Windows.ValidateValueCallback>, bu geri çağırma kayıt alanında ve meta verilerini içinde değil varolduğundan.  
  
<a name="scenarios"></a>   
## <a name="scenarios-for-changing-existing-metadata"></a>Var olan meta verileri değiştirmeye yönelik senaryolar  
 Varolan bir bağımlılık özelliğinin meta verileri ile çalışıyorsanız, bağımlılık özelliği meta verileri değiştirme yaygın bir senaryo varsayılan değer değiştirmektir. Özellik sistem geri aramaları ekleme veya değiştirme daha gelişmiş bir senaryodur. Bağımlılık özellikleri arasındaki farklı kalmalarına türetilmiş bir sınıf uygulanmasını varsa, bunu yapmak isteyebilirsiniz. Hem kod hem de bildirim kullanımını destekleyen bir programlama modeli sahip olmanın koşulları özellikleri herhangi bir sırada ayarlanan etkinleştirmelisiniz biridir. Bu nedenle herhangi bir bağımlı özellik tam zamanında bağlamı olmadan ayarlanmış olması gerekir ve bir ayar siparişi gibi bir oluşturucuda bulunabilir bilerek kullanır. Özellik sistemi bu yönünün hakkında daha fazla bilgi için bkz: [bağımlılık özelliği geri çağrıları ve doğrulama](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md). Doğrulama geri çağırmaları meta verilerinin bir parçası değildir; Bunlar, bağımlılık özelliği tanımlayıcı parçasıdır. Bu nedenle, meta verileri geçersiz kılarak doğrulamalarının değiştirilemez.  
  
 Bazı durumlarda varolan bağımlılık özellikleri WPF çerçeve düzeyi özellik meta verileri seçenekleri değiştirmek isteyebilirsiniz. Bu seçenekler düzen sistemi gibi başka bir WPF çerçeve düzeyi işlem WPF çerçeve düzeyi özellikleri hakkında bilinen belirli koşulları iletişim kurar.  Ayar seçenekleri genellikle yapılır yalnızca yeni bir bağımlılık özelliği kaydederken, ancak bir parçası olarak WPF çerçeve düzeyi özellik meta verileri değiştirmeye mümkündür bir <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> veya <xref:System.Windows.DependencyProperty.AddOwner%2A> çağırın. Belirli değerleri kullanın ve daha fazla bilgi için bkz: [Framework özellik meta verileri](../../../../docs/framework/wpf/advanced/framework-property-metadata.md). Bu seçenekler için yeni kayıtlı bağımlılık özelliği ayarlanmalıdır nasıl ilgili daha fazla bilgi için bkz: [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
<a name="dp_override_metadata"></a>   
### <a name="overriding-metadata"></a>Meta verileri geçersiz kılma  
 Meta verileri geçersiz kılma amacı, böylelikle öncelikle, türü üzerinde mevcut olduğundan, bağımlılık özelliği için uygulanan çeşitli meta verileri türetilmiş davranışlarını değiştirme fırsatına sahip olursunuz. Bunun nedeni daha ayrıntılı olarak açıklanmıştır [meta veri](#dp_metadata_contents) bölümü. Bazı kod örnekleri dahil olmak üzere daha fazla bilgi için bkz: [bağımlılık özelliği için geçersiz meta veriler](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md).  
  
 Özellik meta veriler sağladı kayıt çağrısı sırasında bir bağımlılık özelliği için (<xref:System.Windows.DependencyProperty.Register%2A>). Bununla birlikte, çoğu durumda, bu bağımlılık özelliği devraldığı sınıfı için türe özgü meta veriler sağlamak isteyebilir. Bunu çağırarak yapmak <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> yöntemi.  Bir örnek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], <xref:System.Windows.FrameworkElement> sınıftır ilk kaydeder türü <xref:System.Windows.UIElement.Focusable%2A> bağımlılık özelliği. Ancak <xref:System.Windows.Controls.Control> sınıfı meta verilerini buradan değiştirme kendi ilk varsayılan değer sağlamak bağımlılık özelliği için geçersiz kılar `false` için `true`ve aksi durumda özgün yeniden kullanır <xref:System.Windows.UIElement.Focusable%2A> uygulaması.  
  
 Meta veriler geçersiz kıldığınızda, farklı meta verilerin özellikleri birleştirilmiş değiştirildi ya.  
  
-   <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>birleştirilir. Yeni bir eklerseniz <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, bu geri çağırma meta verilerinde depolanır. Belirtmezseniz, bir <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> değerini geçersiz kılar <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> meta verilerde belirtilen en yakın üst içinden bir başvuru olarak yükseltilir.  
  
-   Gerçek özellik sistem davranışı <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> hiyerarşideki tüm meta veri sahipleri için uygulamaları korunur ve en çok türetilen sınıfın geri aramalar önce çağrılır olmasına, özellik sistemi tarafından yürütme sırasını içeren bir tablo eklenir.  
  
-   <xref:System.Windows.PropertyMetadata.DefaultValue%2A>değiştirilir. Belirtmezseniz, bir <xref:System.Windows.PropertyMetadata.DefaultValue%2A> değerini geçersiz kılar <xref:System.Windows.PropertyMetadata.DefaultValue%2A> meta verilerde belirtilen en yakın üst öğesinden gelir.  
  
-   <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>uygulamaları değiştirilir. Yeni bir eklerseniz <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, bu geri çağırma meta verilerinde depolanır. Belirtmezseniz, bir <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> değerini geçersiz kılar <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> meta verilerde belirtilen en yakın üst içinden bir başvuru olarak yükseltilir.  
  
-   Özellik sistem yalnızca davranıştır <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> hemen meta verilerde çağrılır. Başvuru diğer <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> hiyerarşi uygulamalarında korunur.  
  
 Bu davranış tarafından uygulanan <xref:System.Windows.PropertyMetadata.Merge%2A>ve türetilmiş meta veri sınıflarında geçersiz kılınabilir.  
  
#### <a name="overriding-attached-property-metadata"></a>Ekli özellik meta verileri geçersiz kılma  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ekli özellikler bağımlılık özellikleri olarak uygulanır. Bu ayrıca hangi belirli sınıfları kılabilirsiniz özellik meta verilerini sahip oldukları anlamına gelir. Bağlı bir özellik için kapsam konuları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] herhangi olan genellikle <xref:System.Windows.DependencyObject> bunlarda ayarlı iliştirilmiş bir özellik olabilir. Bu nedenle, herhangi bir <xref:System.Windows.DependencyObject> sınıfının bir örneğini ayarlanabilir gibi türetilmiş bir sınıf herhangi ekli özellik için meta veriler kılabilirsiniz. Varsayılan değerler geri aramalar veya WPF çerçeve düzeyi karakteristiğini raporlama özellikleri geçersiz kılabilirsiniz. Ekli özelliğe, sınıfının bir örneğini ayarlarsanız, özellikleri uygulama özellik meta verileri geçersiz kılar. Örneğin, varsayılan değer sağlayacak şekilde, geçersiz kılma değeri sınıfınızı örneklerinde ekli özellik değeri olarak bildirilen her özellik Aksi takdirde ayarlanmamıştır geçersiz kılabilirsiniz.  
  
> [!NOTE]
>  <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> Özelliği ekli özellikler için ilgili değildir.  
  
<a name="dp_add_owner"></a>   
### <a name="adding-a-class-as-an-owner-of-an-existing-dependency-property"></a>Varolan bir bağımlılık özelliğinin sahibi olarak sınıf ekleme  
 Bir sınıf kendisini zaten, kullanarak kayıtlı bir bağımlılık özelliğinin sahibi olarak ekleyebilirsiniz <xref:System.Windows.DependencyProperty.AddOwner%2A> yöntemi. Bu, ilk olarak kayıtlı bir bağımlılık özelliği için farklı bir tür kullanmak için sınıf sağlar. Ekleme sınıfına genellikle türetilmiş bir sınıf ilk sahibi olarak bu bağımlılık özelliği kayıtlı türü değil. Etkili bir şekilde, bu ve "bir bağımlılık özellik uygulama özgün sahibi sınıfı olmadan devralmak için" türetilmiş sınıflarının ve aynı true sınıfı hiyerarşisinde olmasına ekleme sınıf sağlar. Ayrıca, ekleme sınıfı (ve de tüm türetilen sınıflar) türe özgü meta veriler özgün bağımlılık özelliği için sağlayabilir.  
  
 Kendisini sahibi olarak özellik sistem yardımcı yöntemler ekleme yanı sıra, ekleme sınıfına ek genel üyeler kendisini bağımlılık özelliği yapmak için bildirmelidir] özellik sistemi kod ve biçimlendirme maruz ile tam Katılımcısı . Varolan bir bağımlılık özelliği ekler bir sınıfın yeni bir özel bağımlılık özelliği tanımlayan bir sınıf yaptığı gibi bu bağımlılık özelliği için nesne modeli gösterme durum aynı sorumlulukları vardır. İlk kez kullanıma sunmak için bu tür bir bağımlılık özelliği tanımlayıcı alanı üyesidir. Bu alan olmalıdır bir `public static readonly` türü alan <xref:System.Windows.DependencyProperty>, dönüş değerini atanan <xref:System.Windows.DependencyProperty.AddOwner%2A> çağırın. Tanımlamak için ikinci üye [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] "sarmalayıcı" özelliği. Sarmalayıcı kodu, bağımlılık özelliği işlemek daha uygun yapar (çağrıları kaçının <xref:System.Windows.DependencyObject.SetValue%2A> her zaman ve bu çağrıyı yalnızca bir kez sarmalayıcı içinde yapabilir). Sarmalayıcı aynı özel bir bağımlılık özelliği kaydetme varsa nasıl onu uygulanması için uygulanır. Bağımlılık özelliği uygulama hakkında daha fazla bilgi için bkz: [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) ve [bağımlılık özelliği için bir sahibi türü eklemek](../../../../docs/framework/wpf/advanced/how-to-add-an-owner-type-for-a-dependency-property.md).  
  
#### <a name="addowner-and-attached-properties"></a>AddOwner ve ekli özellikler  
 Çağırabilirsiniz <xref:System.Windows.DependencyProperty.AddOwner%2A> iliştirilmiş bir özellik olarak sahibi sınıfı tarafından tanımlanan bir bağımlılık özelliği için. Genellikle bunu yapmak için daha önce ekli özelliğe bağlı olmayan bağımlılık özelliği olarak kullanıma sunmak için nedenidir. Ardından açığa çıkarır <xref:System.Windows.DependencyProperty.AddOwner%2A> dönüş değeri olarak bir `public static readonly` alan bağımlılık özelliği tanımlayıcı olarak kullanılacak ve böylece özelliği üyeler tablosunda görünür ve bağlı olmayan bir özelliğini destekleyen uygun "sarmalayıcı" özelliklerini tanımlar sınıfınızda kullanımı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.PropertyMetadata>  
 <xref:System.Windows.DependencyObject>  
 <xref:System.Windows.DependencyProperty>  
 <xref:System.Windows.DependencyProperty.GetMetadata%2A>  
 [Bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Çerçeve özellik meta verileri](../../../../docs/framework/wpf/advanced/framework-property-metadata.md)
