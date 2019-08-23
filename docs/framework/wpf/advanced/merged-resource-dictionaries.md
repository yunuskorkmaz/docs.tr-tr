---
title: Birleştirilmiş Kaynak Sözlükleri
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: 466a18a58acfebf6d779a1d0eba3d2637743806e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911719"
---
# <a name="merged-resource-dictionaries"></a>Birleştirilmiş Kaynak Sözlükleri
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]kaynaklar birleştirilmiş bir kaynak sözlüğü özelliğini destekler. Bu özellik, derlenen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulama dışında bir uygulamanın kaynak bölümünü tanımlamak için bir yol sağlar. Kaynaklar daha sonra uygulamalar arasında paylaşılabilir ve ayrıca yerelleştirme için daha kolay yalıtılabilir.  
  
## <a name="introducing-a-merged-resource-dictionary"></a>Birleştirilmiş kaynak sözlüğüne giriş  
 Biçimlendirme ' de, bir sayfada birleştirilmiş bir kaynak sözlüğü tanıtmak için aşağıdaki sözdizimini kullanın:  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 Öğesinde, genellikle bir kaynak koleksiyonundaki tüm öğeler için gerekli olan bir [x:Key yönergesi yok.](../../xaml-services/x-key-directive.md) <xref:System.Windows.ResourceDictionary> Ancak <xref:System.Windows.ResourceDictionary> koleksiyon<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> içindeki başka bir başvuru, bu birleştirilmiş kaynak sözlüğü senaryosu için ayrılmış özel bir durumdur. Birleştirilmiş bir kaynak sözlüğü tanıtan bir [x:Key yönergesi olamaz.](../../xaml-services/x-key-directive.md) <xref:System.Windows.ResourceDictionary> Genellikle, <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> koleksiyon <xref:System.Windows.ResourceDictionary> içerisindeki her biri bir <xref:System.Windows.ResourceDictionary.Source%2A> özniteliği belirtir. Değeri <xref:System.Windows.ResourceDictionary.Source%2A> , birleştirilecek kaynak dosyasının konumunu [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] çözen bir olmalıdır. Öğesinin [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] hedefi, kök öğesi <xref:System.Windows.ResourceDictionary> gibi başka [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir dosya olmalıdır.  
  
> [!NOTE]
> Bu, bir birleştirilmiş sözlük olarak belirtilen, <xref:System.Windows.ResourceDictionary> belirtilmesine <xref:System.Windows.ResourceDictionary.Source%2A>alternatif olarak veya belirtilen kaynaktan eklenen kaynakların yanı sıra bir birleştirilmiş sözlük olarak belirtilen kaynakları tanımlamak için geçerlidir. Ancak, bu yaygın bir senaryo değildir; birleştirilmiş sözlüklerin ana senaryosu, dış dosya konumlarından kaynakları birleştirmelidir. Bir sayfa için biçimlendirme dahilinde kaynakları belirtmek istiyorsanız, genellikle bunları birleştirilmiş sözlüklerde değil Main <xref:System.Windows.ResourceDictionary> içinde tanımlamanız gerekir.  
  
## <a name="merged-dictionary-behavior"></a>Birleştirilmiş sözlük davranışı  
 Birleştirilmiş bir Sözlükteki kaynaklar, birleştirildikleri ana kaynak sözlüğü kapsamından hemen sonra gelen kaynak arama kapsamındaki bir konum kaplar. Bir kaynak anahtarının her bir sözlük içinde benzersiz olması gerekse de, birleştirilmiş sözlüklerde bir anahtar birden çok kez bulunabilir. Bu durumda, döndürülen kaynak, <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> koleksiyonda sırayla bulunan son sözlükten gelir. <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> Koleksiyon içinde[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]tanımlanmışsa, koleksiyondaki birleştirilmiş sözlüklerin sırası, biçimlendirmede belirtilen öğelerin sıralıyordu. Birincil sözlükte ve aynı zamanda birleştirilmiş bir sözlükte tanımlanmış bir anahtar varsa, döndürülen kaynak birincil sözlükten gelir. Bu kapsam kuralları hem statik kaynak başvuruları hem de dinamik kaynak başvuruları için eşit oranda geçerlidir.  
  
### <a name="merged-dictionaries-and-code"></a>Birleştirilmiş sözlükler ve kod  
 Birleştirilmiş sözlükler, kod aracılığıyla bir `Resources` sözlüğe eklenebilir. Her <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> <xref:System.Windows.ResourceDictionary> birözellikiçinvarolanvarsayılan,başlangıçtaboşkoleksiyonözelliğinedesahiptir.`Resources` Kod aracılığıyla birleştirilmiş bir sözlük eklemek için, <xref:System.Windows.ResourceDictionary>istenen birincil öğesine bir başvuru elde edersiniz, <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> özelliğin değerini alır ve içinde <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>bulunan genel `Collection` ' `Add` i çağırın. Eklediğiniz nesne yeni <xref:System.Windows.ResourceDictionary>bir olmalıdır. Kodda, <xref:System.Windows.ResourceDictionary.Source%2A> özelliğini ayarlamayın. Bunun yerine, bir <xref:System.Windows.ResourceDictionary> nesnesi oluşturarak ya da yükleyerek edinmeniz gerekir. <xref:System.Windows.ResourceDictionary> Var olan bir <xref:System.Windows.ResourceDictionary> <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> köke<xref:System.Windows.ResourceDictionary> sahip var olan bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya akışına çağrı yapmak için bir yol yükleme ve ardından dönüş değeri olarak atama.  
  
### <a name="merged-resource-dictionary-uris"></a>Birleştirilmiş kaynak sözlüğü URI 'Leri  
 Bir birleştirilmiş kaynak sözlüğünün nasıl dahil edileceğini kullanabileceğiniz, kullanacağınız [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] biçim tarafından belirtilen çeşitli teknikler vardır. Genel anlamda, bu teknikler iki kategoriye ayrılabilir: projenin bir parçası olarak derlenen kaynaklar ve projenin parçası olarak derlenmeyen kaynaklar.  
  
 Projenin bir parçası olarak derlenen kaynaklar için kaynak konumuna başvuran göreli bir yol kullanabilirsiniz. Göreli yol derleme sırasında değerlendirilir. Kaynağınız, kaynak oluşturma eylemi olarak projenin bir parçası olarak tanımlanmalıdır. Projeye kaynak olarak bir Resource. xaml dosyası eklerseniz, kaynak dosyasını çıkış dizinine kopyalamanız gerekmez, kaynak zaten derlenmiş uygulama içinde yer alır. Içerik oluşturma eylemini de kullanabilirsiniz, ancak dosyaları çıkış dizinine kopyalamanız ve ayrıca kaynak dosyalarını çalıştırılabilir dosyaya aynı yol ilişkisinde dağıtmanız gerekir.  
  
> [!NOTE]
> Katıştırılmış kaynak oluşturma eylemini kullanmayın. Derleme eyleminin kendisi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalarda desteklenir, ancak <xref:System.Windows.ResourceDictionary.Source%2A> çözümü içermez <xref:System.Resources.ResourceManager>ve bu nedenle, bireysel kaynakları akışın dışına ayıramaz. Kaynaklara erişmek için kullandığınız <xref:System.Resources.ResourceManager> sürece, diğer amaçlar için de ekli kaynak kullanmaya devam edebilirsiniz.  
  
 İlgili bir teknik, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya için paket URI 'si kullanmak ve kaynak olarak bu dosyaya başvurmalıdır. Paket URI 'SI, başvurulan derlemelerin ve diğer tekniklerdeki bileşenlere başvuruları sağlar. Paket URI 'Leri hakkında daha fazla bilgi için bkz. [WPF uygulama kaynağı, içerik ve veri dosyaları](../app-development/wpf-application-resource-content-and-data-files.md).  
  
 Projenin bir parçası olarak derlenmediği kaynaklar için, URI çalışma zamanında değerlendirilir. Kaynak dosyasına başvurmak için dosya: veya http: gibi ortak bir URI taşıması kullanabilirsiniz. Derlenmemiş kaynak yaklaşımını kullanmanın dezavantajı, bu dosya: Access 'in ek dağıtım adımları gerektirdiğini ve http: Access 'in Internet güvenlik bölgesini gösterdiği anlamına gelir.  
  
### <a name="reusing-merged-dictionaries"></a>Birleştirilmiş sözlükleri yeniden kullanma  
 Birleştirme için kaynak sözlüğüne herhangi bir geçerli [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]olarak başvurulabildiğinden, birleştirilmiş kaynak sözlüklerini uygulamalar arasında yeniden kullanabilir veya paylaşabilirsiniz. Bunu nasıl yapabileceğiniz, uygulama dağıtım stratejinize ve hangi uygulama modelini izlediğinize bağlı olarak değişir. Yaygın olarak bahsedilen paket URI stratejisi, bir derleme başvurusunu paylaşarak geliştirme sırasında birden fazla proje genelinde birleştirilmiş bir kaynağı daha fazla kaynak için bir yol sağlar. Bu senaryoda, kaynaklar istemci tarafından hala dağıtılır ve uygulamalardan en az biri başvurulan derlemeyi dağıtmalıdır. Ayrıca, http protokolünü kullanan dağıtılmış bir URI aracılığıyla birleştirilmiş kaynaklara başvurmak mümkündür.  
  
 Birleştirilmiş sözlükleri yerel uygulama dosyaları olarak veya yerel paylaşılan depolama alanına yazmak, bir diğer olası birleştirilmiş sözlük/uygulama dağıtım senaryosudur.  
  
### <a name="localization"></a>Yerelleştirme  
 Yerelleştirilmesi gereken kaynaklar birincil sözlüklerde birleştirilmiş sözlüklerde yalıtılmışsa ve gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]olarak tutuluyorsa, bu dosyalar ayrı olarak yerelleştirilebilecek. Bu teknik, uydu kaynak derlemelerinin yerelleştirilmesi için hafif bir alternatiftir. Ayrıntılar için bkz. [WPF Genelleştirme ve yerelleştirme genel bakış](wpf-globalization-and-localization-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.ResourceDictionary>
- [XAML Kaynakları](xaml-resources.md)
- [Kaynaklar ve Kod](resources-and-code.md)
- [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları](../app-development/wpf-application-resource-content-and-data-files.md)
