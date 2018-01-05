---
title: "Freezable Nesnelerine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], description
- unfreezing Freezable objects [WPF]
- classes [WPF], Freezable
ms.assetid: 89c71692-4f43-4057-b611-67c6a8a863a2
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7390181570c6deeea77e5e76493a62e84107286b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="freezable-objects-overview"></a>Freezable Nesnelerine Genel Bakış
Bu konu, etkili bir şekilde kullanmak ve oluşturmak açıklar <xref:System.Windows.Freezable> uygulama performansının artırılmasına yardımcı olan özel özellikleri sağlayan nesne. Fırçalar, kalemler, dönüşümleri, geometri ve animasyonları freezable nesneleri örneklerindendir.  
  
<a name="whatisafreezable"></a>   
## <a name="what-is-a-freezable"></a>Freezable nedir?  
 A <xref:System.Windows.Freezable> , iki durumlu sahip bir nesne özel bir tür: çözülmüş ve dondurulmuş. Çözülmüş, bir <xref:System.Windows.Freezable> herhangi bir nesne gibi davranır görünüyor. Dondurulmuş olduğunda, bir <xref:System.Windows.Freezable> artık değiştirilebilir.  
  
 A <xref:System.Windows.Freezable> sağlayan bir <xref:System.Windows.Freezable.Changed> nesneye herhangi bir değişiklik olduğunda gözlemcileri bildirmek için olay. Dondurma bir <xref:System.Windows.Freezable> , artık kaynaklar üzerinde değişiklik bildirimleri harcamanız gerektiğinden kendi performansını iyileştirebilir. Dondurulmuş <xref:System.Windows.Freezable> bir çözülmüş sırasında iş parçacıkları arasında paylaşılabilir <xref:System.Windows.Freezable> olamaz.  
  
 Ancak <xref:System.Windows.Freezable> sınıfına sahip birçok uygulama, en <xref:System.Windows.Freezable> nesnelerini [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] grafik alt sistemi ile ilişkilidir.  
  
 <xref:System.Windows.Freezable> Sınıfı belirli grafik sistem nesnelerin kullanımını kolaylaştırır ve uygulama performansının artırılmasına yardımcı olabilir. Devralınan türlerine örnek olarak <xref:System.Windows.Freezable> dahil <xref:System.Windows.Media.Brush>, <xref:System.Windows.Media.Transform>, ve <xref:System.Windows.Media.Geometry> sınıfları. Yönetilmeyen kaynakları içerdiğinden, sistem gerekir bu nesneler için değişiklikleri izlemek ve özgün nesne bir değişiklik olduğunda sonra karşılık gelen yönetilmeyen kaynaklarını güncelleştirin. Grafik sistem nesnesini gerçekte değiştirmeyin olsa bile değiştirmeniz durumunda sistemin hala bazı izleme nesnesi kaynaklarını ayırmanız gerekir.  
  
 Örneğin, oluşturduğunuz varsayalım bir <xref:System.Windows.Media.SolidColorBrush> fırça ve bir düğmenin arka planını boyamak için kullanın.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]  
  
 Düğme işlendiğinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafik alt sistemi düğme görünümünü oluşturmak için piksel birtakım boyamak için sağlanan bilgileri kullanır. Düğme boyandığında nasıl tanımlamak için bir düz renk fırça kullanılır ancak düz renk fırça gerçekte boyamayı yapmaz. Grafik sistemi düğme ve fırça için hızlı, düşük düzey nesneleri oluşturur ve ekranınızda gerçekte bu nesneler olduğu.  
  
 Fırça değiştirmek olsaydı, alt düzey bu nesneleri yeniden oluşturulması gerekir. Ne fırça karşılık gelen oluşturulan, alt düzey nesneleri bulmak ve değişiklik yapıldığında güncelleştirmenize olanak verir freezable sınıftır. Bu özellik etkinleştirildiğinde, fırça "çözülmüş." olarak kabul edilir  
  
 Freezable'nın <xref:System.Windows.Freezable.Freeze%2A> yöntemi kendi kendini güncelleştirme özelliği devre dışı bırakmanızı sağlar. "Dondurulmuş" veya değiştirilemeyen hale fırça yapmak için bu yöntemi kullanabilirsiniz.  
  
> [!NOTE]
>  Her Freezable nesne dondurulmuş. Atma önlemek için bir <xref:System.InvalidOperationException>, Freezable nesnenin değerini denetleyin <xref:System.Windows.Freezable.CanFreeze%2A> onu, dondurmayı denemeden önce dondurulmuş olup olmadığını belirlemek için özellik.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]  
  
 Artık freezable değiştirmeniz gerektiğinde, dondurmayı performans avantajı sağlar. Bu örnekte fırça donmasına olsaydı, grafik sistem değişiklikleri izlemek artık gerekir. Fırça değişmeyeceği bildiği için grafik sistemi diğer iyileştirmeleri de yapabilirsiniz.  
  
> [!NOTE]
>  Kolaylık olması için bunları açıkça Dondur sürece freezable nesneler çözülmüş olarak kalır.  
  
<a name="frozenfreezables"></a>   
## <a name="using-freezables"></a>Freezable'ı kullanma  
 Bir çözülmüş freezable herhangi bir nesne türünü kullanarak gibi kullanmaktır. Aşağıdaki örnekte, rengi bir <xref:System.Windows.Media.SolidColorBrush> bir düğmenin arka planını boyamak için kullanılan sonra sarı kırmızı değiştirilir. Grafik sistemi düğmeyi sarı kırmızı için ekranın bir sonraki yenilenmesinde otomatik olarak değiştirmek için arka planda çalışır.  
  
 [!code-csharp[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
 [!code-vb[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]  
  
### <a name="freezing-a-freezable"></a>Freezable dondurma  
 Yapmak için bir <xref:System.Windows.Freezable> değiştirilemeyen, çağrı kendi <xref:System.Windows.Freezable.Freeze%2A> yöntemi. Freezable nesneleri içeren bir nesne dondurmak, bu nesneler de dondurulmuş. Örneğin, freeze, bir <xref:System.Windows.Media.PathGeometry>, rakamları ve içerdiği kesimleri çok dondurulmuş olması.  
  
 Bir Freezable **olamaz** aşağıdakilerden biri doğruysa dondurulmuş:  
  
-   Animasyonlu veya veri ilişkili özellikleri.  
  
-   Dinamik bir kaynak tarafından ayarlanan özellikleri vardır. (Bkz [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md) dinamik kaynaklar hakkında daha fazla bilgi için.)  
  
-   İçerdiği <xref:System.Windows.Freezable> dondurulmuş olamaz alt nesneler.  
  
 Bu koşullar yanlış ise ve değiştirmeyi düşünmüyorsanız <xref:System.Windows.Freezable>, sonra da, daha önce açıklanan performans avantajı kazanmak için dondurmayı.  
  
 Bir kez freezable'nın çağırdığınızda <xref:System.Windows.Freezable.Freeze%2A> yöntemi, artık değiştirilebilir. Dondurulmuş değiştirmeye nesne neden bir <xref:System.InvalidOperationException> oluşturulmasına. Biz dondurulmuş sonra fırça değiştirme girişimi nedeniyle aşağıdaki kod bir özel durum oluşturur.  
  
 [!code-csharp[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
 [!code-vb[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]  
  
 Bu özel durum atma önlemek için kullanabileceğiniz <xref:System.Windows.Freezable.IsFrozen%2A> belirlemek amacıyla yöntemi olup olmadığını bir <xref:System.Windows.Freezable> dondurulmuş.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 Önceki kod örneğinde dondurulmuş nesnesini kullanarak değiştirilebilir bir kopyasını yapıldı <xref:System.Windows.Freezable.Clone%2A> yöntemi. Sonraki bölümde kopyalamayı daha ayrıntılı olarak anlatılmaktadır.  
  
 **Not** çünkü dondurulmuş freezable animasyonlu olamaz, animasyon sistemi değiştirilebilir klonlar, otomatik olarak oluşturacak dondurulmuş <xref:System.Windows.Freezable> nesneleri bunlarla animasyon çalıştığınızda bir <xref:System.Windows.Media.Animation.Storyboard>. Ek yükü kopyalanarak neden performans ortadan kaldırmak için onu animasyon eklemek istiyorsanız, çözülmüş bir nesne bırakın. Film şeritleri ile animasyon ekleme hakkında daha fazla bilgi için bkz: [film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
### <a name="freezing-from-markup"></a>Biçimlendirme gelen dondurma  
 Donmasına bir <xref:System.Windows.Freezable> nesne kullandığınız biçimlendirme içinde bildirilen `PresentationOptions:Freeze` özniteliği. Aşağıdaki örnekte, bir <xref:System.Windows.Media.SolidColorBrush> bir sayfa kaynak olarak bildirilen ve dondurulmuş. Ardından, bir düğmenin arka planını ayarlamak için kullanılır.  
  
 [!code-xaml[FreezableSample#FreezeFromMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]  
  
 Kullanılacak `Freeze` özniteliği, sunu seçenekleri ad alanına eşlemeniz gerekir: `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`. `PresentationOptions`Bu ad alanı eşlemesi için önerilen önekidir:  
  
```  
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"   
```  
  
 Bu öznitelik tüm XAML okuyucuları tanımak için kullanmanız önerilir [mc: yoksayılabilir özniteliği](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) işaretlemek için `Presentation:Freeze` özniteliği olarak yoksayılabilir:  
  
```  
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
mc:Ignorable="PresentationOptions"  
```  
  
 Daha fazla bilgi için bkz: [mc: yoksayılabilir özniteliği](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) sayfası.  
  
### <a name="unfreezing-a-freezable"></a>"Freezable'ı"Dondurmama"  
 Bir kez dondurulmuş bir <xref:System.Windows.Freezable> hiçbir zaman değiştirilebilir veya çözülmüş; Bununla birlikte, kullanarak çözülmüş bir kopya oluşturabilirsiniz <xref:System.Windows.Freezable.Clone%2A> veya <xref:System.Windows.Freezable.CloneCurrentValue%2A> yöntemi.  
  
 Aşağıdaki örnekte, düğmenin arka planı fırça ile ayarlanır ve bu fırça sonra dondurulmuş. Fırça kullanma çözülmüş bir kopyası yapıldıktan <xref:System.Windows.Freezable.Clone%2A> yöntemi. Kopya değiştirilebilir ve düğmenin arka plan kırmızı sarı değiştirmek için kullanılır.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
> [!NOTE]
>  Kullandığınız kopya yönteminden bağımsız olarak, animasyon hiçbir zaman yeni kopyalanır <xref:System.Windows.Freezable>.  
  
 <xref:System.Windows.Freezable.Clone%2A> Ve <xref:System.Windows.Freezable.CloneCurrentValue%2A> yöntemleri freezable derin kopyalarını üretir. Freezable diğer freezable nesneleri dondurulmuş içeriyorsa, bunlar ayrıca kopyalanabilen ve değiştirilebilir yapılır. Örneğin, dondurulmuş kopyalarsanız <xref:System.Windows.Media.PathGeometry> değiştirilebilir hale getirmek için rakamları ve içerdiği kesimleri da kopyalanır ve değiştirilebilir yapılır.  
  
<a name="createyourownfreezableclass"></a>   
## <a name="creating-your-own-freezable-class"></a>Freezable sınıfınızı oluşturma  
 Öğesinden türeyen bir sınıf <xref:System.Windows.Freezable> aşağıdaki özellikleri kazanır.  
  
-   Özel durumlar: salt okunur (dondurulmuş) ve yazılabilir bir durumda.  
  
-   İş parçacığı güvenliği: dondurulmuş <xref:System.Windows.Freezable> iş parçacıkları arasında paylaşılabilir.  
  
-   Ayrıntılı değişiklik bildirimi: diğer aksine <xref:System.Windows.DependencyObject>s, Freezable nesneleri değiştirme bildirimlerini sağlar alt özellik değerlerini değiştirdiğinizde.  
  
-   Kolay kopyalama: Freezable sınıfı derin kopyalar oluşturmak birkaç yöntem zaten uygulamıştır.  
  
 A <xref:System.Windows.Freezable> bir tür <xref:System.Windows.DependencyObject>ve bu nedenle bağımlılık özellik sistemi kullanır. Sınıf özelliklerinin bağımlılık özellikleri olması gerekmez, ancak bağımlılık özellikleri kullanmak zorunda yazma, çünkü kod miktarını azaltır <xref:System.Windows.Freezable> sınıfı bağımlılık özelliklerini göz önüne alarak ile tasarlanmıştır. Bağımlılık özelliği sistemi hakkında daha fazla bilgi için bkz: [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
 Her <xref:System.Windows.Freezable> alt sınıfı geçersiz kılması gerekir <xref:System.Windows.Freezable.CreateInstanceCore%2A> yöntemi. Sınıfınızda tüm verileri için bağımlılık özellikleri kullanıyorsa, tamamlandı.  
  
 Sınıfınızda bağımlılık özelliği olmayan veri üyeleri içeriyorsa, aşağıdaki yöntemleri geçersiz kılmanız gerekir:  
  
-   <xref:System.Windows.Freezable.CloneCore%2A>  
  
-   <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>  
  
-   <xref:System.Windows.Freezable.GetAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.FreezeCore%2A>  
  
 Ayrıca erişme ve bağımlılık özellikleri olmayan veri üyelerine yazmak için aşağıdaki kuralları uymanız gerekir:  
  
-   Herhangi bir başında [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] bağımlılık özelliği olmayan veri üyeleri okur, çağrı <xref:System.Windows.Freezable.ReadPreamble%2A> yöntemi.  
  
-   Bağımlılık özelliği olmayan veri üyelerini yazan herhangi bir API'yi başlangıcında, çağrı <xref:System.Windows.Freezable.WritePreamble%2A> yöntemi. (Çağırdıktan sonra <xref:System.Windows.Freezable.WritePreamble%2A> içinde bir [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], ek bir arama yapmanıza gerek <xref:System.Windows.Freezable.ReadPreamble%2A> Ayrıca bağımlılık özelliği olmayan veri üyelerini okuyorsanız.)  
  
-   Çağrı <xref:System.Windows.Freezable.WritePostscript%2A> bağımlılık özelliği olmayan veri üyeleri için yazma yöntemleri çıkmadan önce yöntemi.  
  
 Sınıfınızda bağımlılık özelliği veri üyelerin içeriyorsa <xref:System.Windows.DependencyObject> nesnelerini ayrıca çağırmalısınız <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> yöntemi değiştirdiğinizde üzerinde kendi değerlerini, üye ayarlamak olsa bile `null`.  
  
> [!NOTE]
>  Her başlamak çok önemlidir <xref:System.Windows.Freezable> kılmanız temel uygulamayı çağrısıyla yöntemi.  
  
 Özel bir örneği için <xref:System.Windows.Freezable> sınıfı için bkz: [özel animasyon örnek](http://go.microsoft.com/fwlink/?LinkID=159981).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Freezable>  
 [Özel animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=159981)  
 [Bağımlılık Özelliklerine Genel Bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Özel Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
