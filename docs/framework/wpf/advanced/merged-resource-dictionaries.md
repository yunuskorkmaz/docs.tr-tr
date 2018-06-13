---
title: Birleştirilmiş Kaynak Sözlükleri
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: f2dc5bbb96d74533e8e77251185a0b105fc55746
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548060"
---
# <a name="merged-resource-dictionaries"></a>Birleştirilmiş Kaynak Sözlükleri
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kaynakları birleştirilmiş kaynak sözlüğü özelliğini desteklemez. Bu özellik, kaynaklar bölümünü tanımlamak için bir yol sağlar. bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlenmiş dışında uygulama [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulama. Kaynaklar sonra uygulamalar arasında paylaşılabilir ve ayrıca daha rahat yerelleştirme için yalıtılır.  
  
## <a name="introducing-a-merged-resource-dictionary"></a>Birleştirilmiş kaynak sözlüğünü Tanıtımı  
 Biçimlendirme içinde bir sayfaya birleştirilmiş kaynak sözlüğünü tanıtmak için aşağıdaki sözdizimini kullanın:  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 Unutmayın <xref:System.Windows.ResourceDictionary> öğesi yok bir [x: Key yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md), bir kaynak koleksiyondaki tüm öğeleri için genellikle gerekli olduğu. Ancak başka bir <xref:System.Windows.ResourceDictionary> içinde başvuru <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> koleksiyonudur bu birleştirilmiş kaynak sözlüğü senaryosu için ayrılmış özel bir durumdur. <xref:System.Windows.ResourceDictionary> Birleştirilmiş tanıtır kaynak sözlüğü olamaz bir [x: Key yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md). Genellikle, her <xref:System.Windows.ResourceDictionary> içinde <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> koleksiyonunu belirtir bir <xref:System.Windows.ResourceDictionary.Source%2A> özniteliği. Değeri <xref:System.Windows.ResourceDictionary.Source%2A> olması gereken bir [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] birleştirilecek kaynak dosyasının konumunu giderir. Bu hedef [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] başka olmalıdır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası ile <xref:System.Windows.ResourceDictionary> , kök öğesi olarak.  
  
> [!NOTE]
>  İçindeki kaynaklara tanımlamak için yasal bir <xref:System.Windows.ResourceDictionary> belirtilen birleştirilmiş bir sözlük belirtmek için bir alternatif olarak da <xref:System.Windows.ResourceDictionary.Source%2A>, veya hangi kaynak belirtilen kaynaktan içerilen yanı sıra. Ancak, bu yaygın bir senaryo değildir; Birleştirilmiş sözlük için ana senaryo dış dosya konumlarından kaynakları birleştirmektir. Bir sayfa için biçimlendirme içindeki kaynaklara belirtmek istiyorsanız, genellikle bu ana tanımlamanız gerekir <xref:System.Windows.ResourceDictionary> ve birleştirilmiş sözlükler içinde değil.  
  
## <a name="merged-dictionary-behavior"></a>Birleştirilmiş sözlük davranışı  
 Birleştirilmiş sözlük kaynaklarında içine birleştirilmiş ana kaynak sözlüğü kapsamını hemen sonra kaynak arama kapsamı bir konumda kaplar. Kaynak anahtarı herhangi bir tek tek dictionary içinde benzersiz olması gerekse de, bir anahtar birleştirilmiş sözlükler kümesinde birden çok kez yer alabilir. Bu durumda, döndürülen kaynak sırayla bulunan son sözlükten gelecektir <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> koleksiyonu. Varsa <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> koleksiyonu içinde tanımlanmışsa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], birleştirilmiş sözlükler koleksiyondaki öğelerin sırasını biçimlendirmede sağlanan sırasıdır sonra. Bir anahtar birincil sözlük hem de birleştirilmiş bir sözlük tanımlanmışsa, döndürülen kaynak birincil sözlükten gelecektir. Bu kapsama kuralları eşit olarak statik kaynak başvuruları hem dinamik kaynak başvuruları uygulanır.  
  
### <a name="merged-dictionaries-and-code"></a>Birleştirilmiş sözlükler ve kod  
 Birleştirilmiş sözlük eklenebilir bir `Resources` kod aracılığıyla sözlük. Varsayılan olarak, başlangıçta boş <xref:System.Windows.ResourceDictionary> için bulunduğunu `Resources` özelliği de varsayılan, başlangıçta boş olan <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> koleksiyon özelliği. Kod aracılığıyla birleştirilmiş sözlük eklemek için istenen birincil başvuru elde <xref:System.Windows.ResourceDictionary>, Al, <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> özellik değeri ve arama `Add` genel `Collection` içinde bulunan <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>. Eklediğiniz nesne yeni bir olmalıdır <xref:System.Windows.ResourceDictionary>. Kod içinde ayarlamayın <xref:System.Windows.ResourceDictionary.Source%2A> özelliği. Bunun yerine, edinmelidir bir <xref:System.Windows.ResourceDictionary> tane oluşturarak veya bir yükleme nesne. Var olan yüklemek için tek yönlü <xref:System.Windows.ResourceDictionary> çağırmak için <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> varolan üzerinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sahip dosya akışı bir <xref:System.Windows.ResourceDictionary> köküne, ardından <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> dönüş değeri için <xref:System.Windows.ResourceDictionary>.  
  
### <a name="merged-resource-dictionary-uris"></a>Birleştirilmiş kaynak sözlüğü URI'leri  
 Tarafından belirtilen birleştirilmiş kaynak sözlüğünü içeren ilişkin birçok tekniği vardır [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] kullanacağınız biçimi. Genel anlamda, bu teknikler iki kategoriye ayrılabilir: projenin bir parçası olarak derlenmiş kaynaklar ve projenin bir parçası derlenmemiş kaynaklar.  
  
 Projenin bir parçası olarak derlenmiş kaynaklar için kaynak konuma başvuruyor göreli bir yol kullanabilirsiniz. Göreli yol derlenirken değerlendirilir. Kaynağınız kaynak yapı eylemi projenin bir parçası olarak tanımlanmalıdır. Kaynak olarak proje içinde kaynak .xaml dosyasında eklerseniz, kaynak dosyanın çıkış dizinine Kopyala gerekmez, kaynak önceden derlenmiş uygulama içinde bulunur. İçerik yapı eylemini de kullanabilirsiniz, ancak sonra dosyaları çıkış dizinine kopyalayın ve da aynı yol ilişkisi kaynak dosyalarında yürütülebilir dosyaya dağıtmanız gerekir.  
  
> [!NOTE]
>  Katıştırılmış kaynak yapı eylemi kullanmayın. Yapı eylemi için desteklenen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar ancak çözünürlüğünü <xref:System.Windows.ResourceDictionary.Source%2A> dahil değil <xref:System.Resources.ResourceManager>ve bu nedenle tek tek kaynak akış dışında ayıramazsınız. Ayrıca kullandığınız sürece diğer amaçlar için hala katıştırılmış kaynakları kullanabilirsiniz <xref:System.Resources.ResourceManager> kaynaklara erişmek için.  
  
 İlişkili bir teknik Pack URI kullanmaktır bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya ve kaynak olarak başvurmaktır. Paketi URI bileşenleri başvurulan derlemeler ve diğer teknik başvuru sağlar. Paketi URI'ler hakkında daha fazla bilgi için bkz: [WPF Uygulama kaynağı, içerik ve veri dosyalarını](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).  
  
 Projenin bir parçası derlenmemiş kaynaklar için URI çalışma zamanında değerlendirilir. Sık kullanılan URI taşıma gibi dosya kullanabilirsiniz: veya http: kaynak dosyasına başvurmak için. Derlenmemiş kaynak yaklaşımı kullanmanın olumsuz yanı o dosyadır: erişim gerektiren ek dağıtım adımları ve http: erişim Internet güvenlik bölgesi anlamına gelir.  
  
### <a name="reusing-merged-dictionaries"></a>Birleştirilen sözlükleri yeniden kullanma  
 Yeniden ya da birleştirmek için kaynak sözlüğü herhangi başvurulabilir olduğundan birleştirilmiş kaynak sözlüklerindeki uygulamalar arasında paylaşmak geçerli [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]. Tam olarak bunu nasıl yapacağınız, uygulama dağıtım stratejinizi bağlıdır ve hangi uygulama modelini izleyin. Yukarıda sözü edilen Pack URI stratejisi genellikle birleştirilmiş bir kaynak birden çok projede geliştirme sırasında bir derleme başvurusu paylaşarak kaynak için bir yol sağlar. Bu senaryoda kaynaklar hala istemci tarafından dağıtılan ve uygulamalardan en az biri başvurulan derlemeyi dağıtmanız gerekir. Http protokolünü kullanan dağıtılmış bir URI üzerinden birleştirilmiş kaynaklara başvurmak mümkündür.  
  
 Yerel uygulama dosyaları veya başka bir olası birleştirilmiş sözlük yerel paylaşılan depolama olarak birleştirilmiş sözlükleri yazma / uygulama dağıtım senaryosudur.  
  
### <a name="localization"></a>Yerelleştirme  
 Yerelleştirilmesi gereken kaynaklar birincil sözlükler birleştirilir ve olarak gevşek tutulan sözlükler yalıtılmış olması durumunda [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bu dosyalar ayrı olarak yerelleştirilebilir. Bu teknik, uydu kaynak derlemelerini yerelleştirme için basit bir alternatifidir. Ayrıntılar için bkz [WPF Genelleştirme ve yerelleştirme genel bakış](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.ResourceDictionary>  
 [XAML Kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Kaynaklar ve Kod](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
