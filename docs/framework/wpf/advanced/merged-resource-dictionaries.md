---
title: Birleştirilmiş Kaynak Sözlükleri
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: f8549dedc9c6f37fb8a06a376351ed96b808bfd4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572931"
---
# <a name="merged-resource-dictionaries"></a>Birleştirilmiş Kaynak Sözlükleri
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kaynakları, birleştirilmiş kaynak sözlük özelliğini desteklemez. Bu özellik, kaynaklar bölümünü tanımlamak için bir yol sağlar. bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dışında derlenmiş uygulama [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulama. Kaynaklar ardından uygulamalar arasında paylaşılabilir ve ayrıca daha rahat yerelleştirme için yalıtılır.  
  
## <a name="introducing-a-merged-resource-dictionary"></a>Birleştirilmiş kaynak sözlüğünü ile tanışın  
 Biçimlendirme içinde bir sayfa ile birleştirilmiş kaynak sözlüğünü tanıtmak için aşağıdaki sözdizimini kullanın:  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 Unutmayın <xref:System.Windows.ResourceDictionary> öğesi yok bir [x: Key yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md), genellikle bir kaynak koleksiyondaki tüm öğeler için gerekli olduğu. Ancak başka bir <xref:System.Windows.ResourceDictionary> içinde başvuru <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> koleksiyondur bu birleştirilmiş kaynak sözlüğü senaryosu için ayrılmış bir özel durum. <xref:System.Windows.ResourceDictionary> Birleştirilmiş sunan kaynak sözlüğü sahip bir [x: Key yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md). Genellikle, her <xref:System.Windows.ResourceDictionary> içinde <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> koleksiyonu belirtir bir <xref:System.Windows.ResourceDictionary.Source%2A> özniteliği. Değerini <xref:System.Windows.ResourceDictionary.Source%2A> olmalıdır bir [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] birleştirilecek kaynak dosyasının konumunu çözümleyen. Hedef, söz konusu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başka olmalıdır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası ile <xref:System.Windows.ResourceDictionary> , kök öğesi olarak.  
  
> [!NOTE]
>  İçindeki kaynakları tanımlamak için yasal bir <xref:System.Windows.ResourceDictionary> belirtilen birleştirilmiş bir sözlük belirtmek için alternatif olarak ya da <xref:System.Windows.ResourceDictionary.Source%2A>, veya ek olarak belirtilen kaynaktan hangi kaynakları dahil edilir. Ancak, bu yaygın bir senaryo değildir; Ana birleştirilmiş sözlükler dış dosya konumları kaynaklardan birleştirmeyi senaryodur. Bir sayfa için biçimlendirme içinde kaynakları belirtmek istiyorsanız, genellikle bu ana tanımlamalıdır <xref:System.Windows.ResourceDictionary> birleştirilmiş sözlükler içinde değil.  
  
## <a name="merged-dictionary-behavior"></a>Birleştirilmiş sözlük davranışı  
 Birleştirilmiş sözlük kaynaklarında hemen sonra bunlar birleştirilir ana kaynak sözlüğü kapsamı olan kaynak arama kapsamını bir konumda kaplar. Kaynak anahtarı herhangi tek bir sözlük dahilinde benzersiz olmalıdır, ancak bir anahtar birleştirilmiş sözlükler kümesi içinde birden çok kez bulunabilir. Bu durumda, döndürülen kaynak sırayla bulunan son sözlükten gelir <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> koleksiyonu. Varsa <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> koleksiyon olarak tanımlandı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], birleştirilmiş sözlükler koleksiyondaki sırasını biçimlendirmede sağlanan öğelerin sırasını kaldırılır. Bir anahtar birincil sözlüğündeki ve birleştirilmiş bir sözlükte tanımlı ise döndürülen kaynak birincil sözlükten duruma gelir. Bu kapsama kuralları eşit olarak statik kaynak başvurularını ve dinamik kaynak için başvurular uygulanır.  
  
### <a name="merged-dictionaries-and-code"></a>Birleştirilmiş sözlükler ve kod  
 Birleştirilmiş sözlükler eklenebilir bir `Resources` kod aracılığıyla sözlük. Varsayılan, başlangıçta boş <xref:System.Windows.ResourceDictionary> için bulunduğunu `Resources` özelliğine de sahip başlangıçta boş bir varsayılan <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> koleksiyon özelliği. Kod aracılığıyla bir birleştirilmiş sözlük eklemek için istenen birincil başvuru elde <xref:System.Windows.ResourceDictionary>, Al, <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> özellik değeri ve çağrı `Add` genel `Collection` içinde bulunan <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>. Eklediğiniz nesne yeni bir olmalıdır <xref:System.Windows.ResourceDictionary>. Kod içinde ayarlamayın <xref:System.Windows.ResourceDictionary.Source%2A> özelliği. Bunun yerine, almalısınız bir <xref:System.Windows.ResourceDictionary> nesne oluşturma ya da bir yükleniyor. Var olan bir yükleme için tek yönlü <xref:System.Windows.ResourceDictionary> çağrılacak <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> var olan bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sahip dosya akışı bir <xref:System.Windows.ResourceDictionary> köküne, ardından <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> dönüş değerine <xref:System.Windows.ResourceDictionary>.  
  
### <a name="merged-resource-dictionary-uris"></a>Birleştirilmiş kaynak sözlüğü URI'leri  
 Birleştirilmiş kaynak sözlüğünü içeren tarafından belirtilen öğrenmek için çeşitli teknikler vardır [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] kullanacağınız biçimi. Genel anlamda bu teknikler iki kategoriye ayrılabilir: projenin bir parçası derlenmiş kaynaklar ve projenin bir parçası derlenmemiş kaynaklar.  
  
 Projenin bir parçası derlenen kaynaklar için kaynak konuma başvuran bir göreli yol kullanabilirsiniz. Göreli yol, derleme sırasında değerlendirilir. Kaynak bir kaynak derleme eylemi olarak projenin bir parçası olarak tanımlanması gerekir. Kaynak Proje kaynak .xaml dosyasını dahil ederseniz, kaynak dosyasının çıkış dizinine Kopyala gerekmez, kaynak önceden derlenmiş uygulama içinde bulunur. İçerik yapı eylemini de kullanabilirsiniz, ancak sonra çıktı dizinine dosyaları kopyalayın ve ayrıca aynı yol ilişkisinde kaynak dosyaları yürütülebilir dosyaya dağıtmanız gerekir.  
  
> [!NOTE]
>  Gömülü kaynak derleme eylemini kullanmayın. Yapı eylemi için desteklenen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar ancak çözünürlüğünü <xref:System.Windows.ResourceDictionary.Source%2A> birleşmez <xref:System.Resources.ResourceManager>ve böylece akış dışında ayrı kaynak ayıramazsınız. Ayrıca kullandığınız sürece diğer amaçlar için hala gömülü kaynak kullanabilirsiniz <xref:System.Resources.ResourceManager> kaynaklara erişmek için.  
  
 İlgili bir teknik bir paketi URI'si için kullanılacak olan bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya ve kaynak olarak başvurduğu. Pack URI'si başvurulan derlemelerin ve diğer teknikleri bileşenleri başvurular sağlar. Paketi bir URI'leri hakkında daha fazla bilgi için bkz. [WPF Uygulama kaynağı, içerik ve veri dosyalarını](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).  
  
 Projenin bir parçası derlenmemiş kaynaklar için URI'yi çalışma zamanında değerlendirilir. Ortak bir URI taşıma gibi dosya kullanabilirsiniz: http: kaynak dosyasına başvuruda bulunmak için. Derlenmemiş kaynak yaklaşımı kullanılarak dezavantajı dosyasıdır: ek dağıtım adımları ve http erişimi gerektirir: erişim Internet güvenlik bölgesi anlamına gelir.  
  
### <a name="reusing-merged-dictionaries"></a>Birleştirilmiş sözlükler yeniden kullanma  
 Yeniden kullanabilir veya birleştirmek için kaynak sözlüğü herhangi başvurulabilir olduğundan, birleştirilmiş kaynak sözlükleri uygulamalar arasında paylaşma geçerli [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]. Tam olarak bunu nasıl yapacağınız uygulama dağıtım stratejinizde bağlıdır ve hangi uygulama modelini izleyin. Yukarıda sözü edilen paketi URI stratejisi genellikle birleştirilmiş bir kaynak birden çok projede geliştirme sırasında bir bütünleştirilmiş kod başvurusu paylaşarak kaynak için bir yol sağlar. Bu senaryoda istemci tarafından hala kaynaklar dağıtılır ve uygulamaları en az biri başvurulan derleme dağıtmanız gerekir. Http protokolünü kullanan dağıtılmış bir URI aracılığıyla birleştirilmiş kaynaklara başvuran da mümkündür.  
  
 Birleştirilmiş sözlükler yerel uygulama dosyaları veya başka bir olası birleştirilmiş sözlük yerel paylaşılan depolamaya yazma / uygulama dağıtım senaryosu.  
  
### <a name="localization"></a>Yerelleştirme  
 Yerelleştirilebilecek kaynakları birincil sözlüklerine birleştirilir ve gevşek'olarak tutulan sözlüklere yalıtılmış olması durumunda [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bu dosyaları ayrı olarak yerelleştirilebilir. Bu teknik, yerelleştirme uydu kaynak derlemeleri için basit bir alternatiftir. Ayrıntılar için bkz [WPF genelleştirmesi ve yerelleştirmesine genel bakış](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.ResourceDictionary>
- [XAML Kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md)
- [Kaynaklar ve Kod](../../../../docs/framework/wpf/advanced/resources-and-code.md)
- [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
