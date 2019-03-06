---
title: Freezable Nesnelerine Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], description
- unfreezing Freezable objects [WPF]
- classes [WPF], Freezable
ms.assetid: 89c71692-4f43-4057-b611-67c6a8a863a2
ms.openlocfilehash: 9331c892b0c0abccf2ea8700d46fa4180a7225ed
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375850"
---
# <a name="freezable-objects-overview"></a>Freezable Nesnelerine Genel Bakış
Bu konu, etkili bir şekilde kullanmak ve oluşturmak üzere açıklar <xref:System.Windows.Freezable> uygulama performansını iyileştirmeye yardımcı olabilecek özel özellikleri sağlayan nesne. Freezable nesneleri Fırçalar, kalemler, dönüştürmeleri, geometri ve animasyonları örneklerindendir.  
  
<a name="whatisafreezable"></a>   
## <a name="what-is-a-freezable"></a>Freezable nedir?  
 A <xref:System.Windows.Freezable> iki durumlu nesnesi özel bir türdür: çözülmüş ve donmuş. Çözülmüş, bir <xref:System.Windows.Freezable> herhangi bir nesne gibi davranır. Dondurulmuş, bir <xref:System.Windows.Freezable> artık değiştirilebilir.  
  
 A <xref:System.Windows.Freezable> sağlayan bir <xref:System.Windows.Freezable.Changed> nesne herhangi bir değişiklik olduğunda gözlemcileri bildirmek üzere olay. Dondurma bir <xref:System.Windows.Freezable> kaynaklar üzerinde değişiklik bildirimleri harcama artık gerektiğinden, performansı geliştirebilir. Dondurulmuş <xref:System.Windows.Freezable> çözülmüş bir yandan iş parçacıkları arasında paylaşılabilir <xref:System.Windows.Freezable> olamaz.  
  
 Ancak <xref:System.Windows.Freezable> sınıfına sahip birçok uygulama, en <xref:System.Windows.Freezable> nesneler [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] grafik alt sistemi ile ilişkilidir.  
  
 <xref:System.Windows.Freezable> Sınıfı, belirli grafik sistem nesnelerin kullanımını kolaylaştırır ve uygulama performansının artırılmasına yardımcı olabilir. Devralınan tür örnekleri, <xref:System.Windows.Freezable> dahil <xref:System.Windows.Media.Brush>, <xref:System.Windows.Media.Transform>, ve <xref:System.Windows.Media.Geometry> sınıfları. Yönetilmeyen kaynakları içerdiğinden, sistem bu nesneleri yapılan değişiklikleri izlemek ve özgün nesneye bir değişiklik olduğunda ardından ilgili yönetilmeyen kaynaklarını güncelleştirmeniz gerekir. Aslında grafik sistem nesnesini değiştirmez bile değiştirmeniz durumunda sistem hala bazı izleme nesnesi kaynaklarını ayırmanız gerekir.  
  
 Örneğin, oluşturduğunuz düşünün bir <xref:System.Windows.Media.SolidColorBrush> fırça ve düğmenin arka plan boyama için kullanın.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]  
  
 Düğme işlendiğinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafik alt sistemi piksel bir düğmenin görünümünü oluşturmak için bir grup boyamak için sağlanan bilgileri kullanır. Tek renk Fırçası düğme nasıl boyanacağını açıklamak için kullanılan olsa da, tek renk Fırçası gerçekten boyama yapmaz. Grafik sistem düğme ve fırça için hızlı, düşük düzey nesneleri oluşturur ve gerçekten ekrandaki nesnelere olur.  
  
 Fırça değiştirmek olsaydı, alt düzey nesneleri yeniden oluşturulması gerekir. Ne fırça karşılık gelen oluşturulan, alt düzey nesneleri bulmak için ve değişiklik yapıldığında, onları güncelleştirme olanağı sunar freezable sınıftır. Bu özellik etkinleştirildiğinde, fırça "Çözülmüş" olarak kabul edilir  
  
 Freezable'nın <xref:System.Windows.Freezable.Freeze%2A> yöntemi kendi kendini güncelleştirme özelliği devre dışı bırakmanızı sağlar. "Dondurulmuş" veya değiştirilemeyen fırçanın hale getirmek için bu yöntemi kullanabilirsiniz.  
  
> [!NOTE]
>  Dondurulmuş her Freezable nesne. Üretilmesini önlemek için bir <xref:System.InvalidOperationException>, Freezable nesnenin değerini kontrol edin <xref:System.Windows.Freezable.CanFreeze%2A> özelliği, bu dondurma çalışmadan önce dondurulmuş olup olmadığını belirlemek için.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]  
  
 Freezable değiştirmek, artık ihtiyacınız olduğunda dondurmayı performans avantajlar sağlar. Bu örnekte fırça dondurmak için olsaydı, değişiklikleri izlemek artık grafik sistemi gerekir. Fırça değişmez bildiğinden grafik sistemi diğer iyileştirmeler de yapabilirsiniz.  
  
> [!NOTE]
>  Kolaylık olması için açıkça dondurun sürece freezable nesneleri çözülmüş olarak kalır.  
  
<a name="frozenfreezables"></a>   
## <a name="using-freezables"></a>Freezable'ı kullanma  
 Bir çözülmüş kullanarak freezable başka türde bir nesne gibi kullanmaktır. Aşağıdaki örnekte, rengi bir <xref:System.Windows.Media.SolidColorBrush> düğmenin arka boyamak için kullanılan sonra sarı kırmızı değiştirilir. Grafik sistemi düğmeyi sarı kırmızı ekranın bir sonraki yenilenmesinde otomatik olarak değiştirmek için arka planda çalışır.  
  
 [!code-csharp[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
 [!code-vb[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]  
  
### <a name="freezing-a-freezable"></a>Freezable dondurma  
 Yapmak için bir <xref:System.Windows.Freezable> değiştirilemeyen, arama, <xref:System.Windows.Freezable.Freeze%2A> yöntemi. Freezable nesneleri içeren bir nesne dondurma, bu nesneler de dondurulmuş. Örneğin, dondurma, bir <xref:System.Windows.Media.PathGeometry>, rakamları ve içerdiği kesimleri çok dondurulmuş olması.  
  
 Bir Freezable **olamaz** aşağıdakilerden biri doğruysa, dondurulmuş:  
  
-   Animasyonlu veya veri ilişkili özellikleri.  
  
-   Dinamik bir kaynak tarafından ayarlanan özellikler var. (Bkz [XAML kaynakları](xaml-resources.md) dinamik kaynaklar hakkında daha fazla bilgi için.)  
  
-   İçerdiği <xref:System.Windows.Freezable> nelze zmrazit alt nesneler.  
  
 Bu koşullar false ise ve değiştirmek istemediğiniz <xref:System.Windows.Freezable>, daha önce açıklanan performans avantajlarını elde etmek için dondurun.  
  
 Freezable'nın arama sonra <xref:System.Windows.Freezable.Freeze%2A> yöntemi, artık değiştirilebilir. Dondurulmuş değiştirmeye nesne neden bir <xref:System.InvalidOperationException> oluşturulması için. Şu fırçanın dondurulmuş olup sonra değiştirme girişimi nedeniyle, aşağıdaki kod bir özel durum oluşturur.  
  
 [!code-csharp[freezablesample_procedural#ExceptionExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
 [!code-vb[freezablesample_procedural#ExceptionExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]  
  
 Bu özel durum önlemek için kullanabileceğiniz <xref:System.Windows.Freezable.IsFrozen%2A> belirlemek için yöntemi olup olmadığını bir <xref:System.Windows.Freezable> dondurulmuş.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 Önceki kod örneğinde bir dondurulmuş nesnesini kullanarak değiştirilebilir bir kopyası yapılır <xref:System.Windows.Freezable.Clone%2A> yöntemi. Sonraki bölümde, kopyalamayı daha ayrıntılı olarak açıklanır.  
  
 **Not** çünkü dondurulmuş freezable hareketlendirilemeyebilir, animasyon sistemi değiştirilebilir klonlar, otomatik olarak oluşturacak dondurulmuş <xref:System.Windows.Freezable> nesnelerinin kendileri ile animasyon çalıştığınızda bir <xref:System.Windows.Media.Animation.Storyboard>. Kopyalayarak ek yükü nedeniyle performans ortadan kaldırmak için animasyon eklemek istiyorsanız, çözülmüş bir nesne bırakın. Görsel Taslaklar ile animasyon ekleme hakkında daha fazla bilgi için bkz. [görsel taslaklara genel bakış](../graphics-multimedia/storyboards-overview.md).  
  
### <a name="freezing-from-markup"></a>Biçimlendirmeden dondurma  
 Dondurmak için bir <xref:System.Windows.Freezable> nesne kullandığınız biçimlendirme içinde bildirilen `PresentationOptions:Freeze` özniteliği. Aşağıdaki örnekte, bir <xref:System.Windows.Media.SolidColorBrush> sayfa kaynağı bildirildi ve donmuş. Ardından, bir düğmenin arka planı ayarlamak için kullanılır.  
  
 [!code-xaml[FreezableSample#FreezeFromMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]  
  
 Kullanılacak `Freeze` özniteliği, sunum seçenekleri ad alanına eşleme gerekir: `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`. `PresentationOptions` Bu ad alanı eşlemesi için önerilen ön eki şöyledir:  
  
```  
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"   
```  
  
 Bu öznitelik tüm XAML okuyucular tanınmadığı kullanmanız önerilir [mc: Ignorable özniteliği](mc-ignorable-attribute.md) işaretlemek için `Presentation:Freeze` olarak Ignorable özniteliği:  
  
```  
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
mc:Ignorable="PresentationOptions"  
```  
  
 Daha fazla bilgi için [mc: Ignorable özniteliği](mc-ignorable-attribute.md) sayfası.  
  
### <a name="unfreezing-a-freezable"></a>"Freezable'ı"Dondurmama"  
 Bir kez dondurulmuş, bir <xref:System.Windows.Freezable> hiçbir zaman değiştirilebilir veya çözülmüş; ancak kullanarak çözülmüş bir kopya oluşturabilirsiniz <xref:System.Windows.Freezable.Clone%2A> veya <xref:System.Windows.Freezable.CloneCurrentValue%2A> yöntemi.  
  
 Aşağıdaki örnekte, düğmenin arka plan fırça ile ayarlanır ve bu fırça ardından dondurulmuş. Fırça kullanarak çözülmüş bir kopya yapılmadı <xref:System.Windows.Freezable.Clone%2A> yöntemi. Kopya değiştirilebilir ve düğmenin arka plan sarı kırmızı ile değiştirmek için kullanılır.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
> [!NOTE]
>  Kullandığınız kopya yönteminden bağımsız olarak, animasyonları hiçbir zaman yeni kopyalanan <xref:System.Windows.Freezable>.  
  
 <xref:System.Windows.Freezable.Clone%2A> Ve <xref:System.Windows.Freezable.CloneCurrentValue%2A> yöntemleri üretmek freezable derin kopya. Freezable'nın diğer freezable nesneleri dondurulmuş içeriyorsa, bunlar da kopyalandı ve değiştirilebilir yapılır. Örneğin, dondurulmuş kopyalarsanız <xref:System.Windows.Media.PathGeometry> değiştirilebilir hale getirmek için rakamları ve içerdiği segmentleri kopyalanır ve yapılan değiştirilebilir.  
  
<a name="createyourownfreezableclass"></a>   
## <a name="creating-your-own-freezable-class"></a>Freezable sınıfınızı oluşturma  
 Türetilen bir sınıf <xref:System.Windows.Freezable> aşağıdaki özellikleri elde etti.  
  
-   Özel durumlar: salt okunur (donduruldu) ve yazılabilir bir durumda.  
  
-   İş parçacığı güvenliği: dondurulmuş <xref:System.Windows.Freezable> iş parçacıkları arasında paylaşılabilir.  
  
-   Ayrıntılı değişiklik bildirimi: Diğer aksine <xref:System.Windows.DependencyObject>s, Freezable nesneleri sağlar değişiklik bildirimleri alt özellik değerleri değiştiğinde.  
  
-   Kolay kopyalama: Freezable sınıfı ayrıntılı kopyaları oluşturan çeşitli yöntemler zaten uygulamıştır.  
  
 A <xref:System.Windows.Freezable> bir tür <xref:System.Windows.DependencyObject>ve bu nedenle bağımlılık özelliği sistem kullanır. Sınıf özelliklerinin bağımlılık özellikleri olması gerekmez, ancak bağımlılık özellikleri kullanmak zorunda yazma çünkü kod miktarını azaltır <xref:System.Windows.Freezable> sınıfı aklınızda bağımlılık özellikleriyle tasarlanmıştır. Bağımlılık özelliği sistemi hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md).  
  
 Her <xref:System.Windows.Freezable> öğesinin alt sınıfı geçersiz kılması gerekir <xref:System.Windows.Freezable.CreateInstanceCore%2A> yöntemi. Sınıfınız için onunla ilişkili tüm verileri bağımlılık özellikleri kullanıyorsa, işiniz bitmiştir.  
  
 Bağımlılık özelliği olmayan veri üyeleri sınıfınız varsa, aşağıdaki yöntemleri geçersiz kılmanız gerekir:  
  
-   <xref:System.Windows.Freezable.CloneCore%2A>  
  
-   <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>  
  
-   <xref:System.Windows.Freezable.GetAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.FreezeCore%2A>  
  
 Ayrıca erişme ve bağımlılık özellikleri olmayan veri üyelerine yazma için aşağıdaki kurallara uymanız gerekir:  
  
-   Tüm başındaki [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] bağımlılık özelliği olmayan veri üyeleri okuyan, çağrı <xref:System.Windows.Freezable.ReadPreamble%2A> yöntemi.  
  
-   Bağımlılık özelliği olmayan veri üyeleri Yazar herhangi bir API'yi başlangıcında, çağrı <xref:System.Windows.Freezable.WritePreamble%2A> yöntemi. (Çağırdıktan sonra <xref:System.Windows.Freezable.WritePreamble%2A> içinde bir [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], ek bir çağrı yapmak gerekmez <xref:System.Windows.Freezable.ReadPreamble%2A> de bağımlılık özelliği olmayan veri üyelerini okuyorsanız.)  
  
-   Çağrı <xref:System.Windows.Freezable.WritePostscript%2A> bağımlılık özelliği olmayan veri üyelerine yazma yöntemleri çıkmadan önce yöntemi.  
  
 Sınıfınıza olan bağımlılık özelliği veri üyeleri içerip içermediğini <xref:System.Windows.DependencyObject> nesnelerini ayrıca çağırmalısınız <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> yöntemi, kendi değerlerden birine üye ayarlamak bile her değiştirdiğinizde `null`.  
  
> [!NOTE]
>  Her başlamak çok önemli olduğu <xref:System.Windows.Freezable> geçersiz kılmanız taban uygulamasını çağrısıyla yöntemi.  
  
 Özel bir örneği için <xref:System.Windows.Freezable> sınıfı [özel animasyon örnek](https://go.microsoft.com/fwlink/?LinkID=159981).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Freezable>
- [Özel animasyon örneği](https://go.microsoft.com/fwlink/?LinkID=159981)
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [Özel Bağımlılık Özellikleri](custom-dependency-properties.md)
