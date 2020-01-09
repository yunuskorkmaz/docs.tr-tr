---
title: Birleştirilmiş Kaynak Sözlükleri
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: 899955a9f3302e67de4efa0ce0cb6baf6bf0ec5d
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559787"
---
# <a name="merged-resource-dictionaries"></a>Birleştirilmiş Kaynak Sözlükleri
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kaynaklar birleştirilmiş bir kaynak sözlüğü özelliğini destekler. Bu özellik, derlenmiş [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulamasının dışında bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasının kaynak bölümünü tanımlamak için bir yol sağlar. Kaynaklar daha sonra uygulamalar arasında paylaşılabilir ve ayrıca yerelleştirme için daha kolay yalıtılabilir.  
  
## <a name="introducing-a-merged-resource-dictionary"></a>Birleştirilmiş kaynak sözlüğüne giriş  
 Biçimlendirme ' de, bir sayfada birleştirilmiş bir kaynak sözlüğü tanıtmak için aşağıdaki sözdizimini kullanın:  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 <xref:System.Windows.ResourceDictionary> öğesinin bir [X:Key yönergesine](../../../desktop-wpf/xaml-services/xkey-directive.md)sahip olmadığına ve genellikle bir kaynak koleksiyonundaki tüm öğeler için gerekli olduğunu unutmayın. Ancak <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> koleksiyonu içindeki başka bir <xref:System.Windows.ResourceDictionary> başvurusu, bu birleştirilmiş kaynak sözlüğü senaryosu için ayrılmış özel bir durumdur. Birleştirilmiş bir kaynak sözlüğünü tanıtan <xref:System.Windows.ResourceDictionary> bir [X:Key yönergesi](../../../desktop-wpf/xaml-services/xkey-directive.md)olamaz. Genellikle, <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> koleksiyonu içindeki her <xref:System.Windows.ResourceDictionary> bir <xref:System.Windows.ResourceDictionary.Source%2A> özniteliğini belirtir. <xref:System.Windows.ResourceDictionary.Source%2A> değeri, birleştirilecek kaynak dosyasının konumunu çözen bir Tekdüzen Kaynak tanımlayıcısı (URI) olmalıdır. Bu URI 'nin hedefi, kök öğesi <xref:System.Windows.ResourceDictionary> olan başka bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası olmalıdır.  
  
> [!NOTE]
> Birleştirilmiş bir sözlük olarak belirtilen bir <xref:System.Windows.ResourceDictionary> içinde, <xref:System.Windows.ResourceDictionary.Source%2A>belirtilmesine alternatif olarak veya belirtilen kaynaktan dahil edilen kaynakların yanı sıra kaynakları tanımlamak için geçerlidir. Ancak, bu yaygın bir senaryo değildir; birleştirilmiş sözlüklerin ana senaryosu, dış dosya konumlarından kaynakları birleştirmelidir. Bir sayfa için biçimlendirme dahilinde kaynakları belirtmek istiyorsanız, genellikle bunları birleştirilmiş sözlüklerde değil ana <xref:System.Windows.ResourceDictionary> tanımlamanız gerekir.  
  
## <a name="merged-dictionary-behavior"></a>Birleştirilmiş sözlük davranışı  
 Birleştirilmiş bir Sözlükteki kaynaklar, birleştirildikleri ana kaynak sözlüğü kapsamından hemen sonra gelen kaynak arama kapsamındaki bir konum kaplar. Bir kaynak anahtarının her bir sözlük içinde benzersiz olması gerekse de, birleştirilmiş sözlüklerde bir anahtar birden çok kez bulunabilir. Bu durumda, döndürülen kaynak <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> koleksiyonunda sırayla bulunan son sözlükten gelir. <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> koleksiyonu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]tanımlıysa, koleksiyondaki birleştirilmiş sözlüklerin sırası, biçimlendirmede belirtilen öğelerin sıralıyordu. Birincil sözlükte ve aynı zamanda birleştirilmiş bir sözlükte tanımlanmış bir anahtar varsa, döndürülen kaynak birincil sözlükten gelir. Bu kapsam kuralları hem statik kaynak başvuruları hem de dinamik kaynak başvuruları için eşit oranda geçerlidir.  
  
### <a name="merged-dictionaries-and-code"></a>Birleştirilmiş sözlükler ve kod  
 Birleştirilmiş sözlükler kod aracılığıyla bir `Resources` sözlüğüne eklenebilir. Herhangi bir `Resources` özelliği için mevcut olan başlangıçta boş <xref:System.Windows.ResourceDictionary>, varsayılan olarak başlangıçta boş <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> Collection özelliğine sahiptir. Kod aracılığıyla birleştirilmiş bir sözlük eklemek için, istenen birincil <xref:System.Windows.ResourceDictionary>bir başvuru elde edersiniz, <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> özellik değerini alır ve <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>bulunan genel `Collection` üzerinde `Add` çağırın. Eklediğiniz nesne yeni bir <xref:System.Windows.ResourceDictionary>olmalıdır. Kod içinde <xref:System.Windows.ResourceDictionary.Source%2A> özelliğini ayarlamayın. Bunun yerine, bir <xref:System.Windows.ResourceDictionary> nesnesi oluşturarak ya da bir tane yükleyerek edinmeniz gerekir. Bir <xref:System.Windows.ResourceDictionary> köküne sahip mevcut bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya akışında <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> çağırmak için mevcut bir <xref:System.Windows.ResourceDictionary> yüklemek için bir yol, sonra <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> dönüş değerini <xref:System.Windows.ResourceDictionary>olarak atama.  
  
### <a name="merged-resource-dictionary-uris"></a>Birleştirilmiş kaynak sözlüğü URI 'Leri  
 Kullanacağınız Tekdüzen Kaynak tanımlayıcısı (URI) biçimiyle belirtilen bir birleştirilmiş kaynak sözlüğünü dahil etmek için çeşitli teknikler vardır. Genel anlamda, bu teknikler iki kategoriye ayrılabilir: projenin bir parçası olarak derlenen kaynaklar ve projenin parçası olarak derlenmeyen kaynaklar.  
  
 Projenin bir parçası olarak derlenen kaynaklar için kaynak konumuna başvuran göreli bir yol kullanabilirsiniz. Göreli yol derleme sırasında değerlendirilir. Kaynağınız, kaynak oluşturma eylemi olarak projenin bir parçası olarak tanımlanmalıdır. Projeye kaynak olarak bir Resource. xaml dosyası eklerseniz, kaynak dosyasını çıkış dizinine kopyalamanız gerekmez, kaynak zaten derlenmiş uygulama içinde yer alır. Içerik oluşturma eylemini de kullanabilirsiniz, ancak dosyaları çıkış dizinine kopyalamanız ve ayrıca kaynak dosyalarını çalıştırılabilir dosyaya aynı yol ilişkisinde dağıtmanız gerekir.  
  
> [!NOTE]
> Katıştırılmış kaynak oluşturma eylemini kullanmayın. Derleme eyleminin kendisi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar için desteklenir, ancak <xref:System.Windows.ResourceDictionary.Source%2A> çözümlenmesi <xref:System.Resources.ResourceManager>içermez ve bu nedenle tek bir kaynağı akışın dışına ayıramaz. Kaynaklara erişmek için <xref:System.Resources.ResourceManager> kullandığınız sürece, diğer amaçlar için de gömülü kaynağı kullanmaya devam edebilirsiniz.  
  
 İlgili bir teknik, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası için paket URI 'SI kullanmak ve kaynak olarak bu dosyaya başvurmalıdır. Paket URI 'SI, başvurulan derlemelerin ve diğer tekniklerdeki bileşenlere başvuruları sağlar. Paket URI 'Leri hakkında daha fazla bilgi için bkz. [WPF uygulama kaynağı, içerik ve veri dosyaları](../app-development/wpf-application-resource-content-and-data-files.md).  
  
 Projenin bir parçası olarak derlenmediği kaynaklar için, URI çalışma zamanında değerlendirilir. Kaynak dosyasına başvurmak için dosya: veya http: gibi ortak bir URI taşıması kullanabilirsiniz. Derlenmemiş kaynak yaklaşımını kullanmanın dezavantajı, bu dosya: Access 'in ek dağıtım adımları gerektirdiğini ve http: Access 'in Internet güvenlik bölgesini gösterdiği anlamına gelir.  
  
### <a name="reusing-merged-dictionaries"></a>Birleştirilmiş sözlükleri yeniden kullanma  
 Birleştirilecek kaynak sözlüğüne geçerli bir Tekdüzen Kaynak tanımlayıcısı (URI) yoluyla başvurulabildiğinden, birleştirilmiş kaynak sözlüklerini uygulamalar arasında yeniden kullanabilir veya paylaşabilirsiniz. Bunu nasıl yapabileceğiniz, uygulama dağıtım stratejinize ve hangi uygulama modelini izlediğinize bağlı olarak değişir. Yaygın olarak bahsedilen paket URI stratejisi, bir derleme başvurusunu paylaşarak geliştirme sırasında birden fazla proje genelinde birleştirilmiş bir kaynağı daha fazla kaynak için bir yol sağlar. Bu senaryoda, kaynaklar istemci tarafından hala dağıtılır ve uygulamalardan en az biri başvurulan derlemeyi dağıtmalıdır. Ayrıca, http protokolünü kullanan dağıtılmış bir URI aracılığıyla birleştirilmiş kaynaklara başvurmak mümkündür.  
  
 Birleştirilmiş sözlükleri yerel uygulama dosyaları olarak veya yerel paylaşılan depolama alanına yazmak, bir diğer olası birleştirilmiş sözlük/uygulama dağıtım senaryosudur.  
  
### <a name="localization"></a>Yerelleştirme  
 Yerelleştirilmesi gereken kaynaklar birincil sözlüklerde birleştirilmiş sözlüklerde yalıtılmışsa ve gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]olarak tutuluyorsa, bu dosyalar ayrı olarak yerelleştirilebilecek. Bu teknik, uydu kaynak derlemelerinin yerelleştirilmesi için hafif bir alternatiftir. Ayrıntılar için bkz. [WPF Genelleştirme ve yerelleştirme genel bakış](wpf-globalization-and-localization-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.ResourceDictionary>
- [XAML Kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Kaynaklar ve Kod](resources-and-code.md)
- [WPF Uygulama Kaynağı, İçerik ve Veri Dosyaları](../app-development/wpf-application-resource-content-and-data-files.md)
