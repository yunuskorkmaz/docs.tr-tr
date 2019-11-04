---
title: Kaynaklar ve Kod
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys [WPF], using objects as
- resources [WPF], accessing from procedural code
- procedural code [WPF], creating resources with
- procedural code [WPF], accessing resources from
- resources [WPF], creating with procedural code
ms.assetid: c1cfcddb-e39c-41c8-a7f3-60984914dfae
ms.openlocfilehash: 3d504467c137c1e3f494e120217957661f4e75a3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458761"
---
# <a name="resources-and-code"></a>Kaynaklar ve Kod
Bu genel bakış, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kaynaklarına [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] söz dizimi yerine kod kullanarak nasıl erişilebileceğini veya oluşturulandığına yoğunlaşır. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sözdizimi perspektifinden genel kaynak kullanımı ve kaynakları hakkında daha fazla bilgi için bkz. [xaml kaynakları](xaml-resources.md).  

<a name="accessing"></a>   
## <a name="accessing-resources-from-code"></a>Koddan kaynaklara erişme  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aracılığıyla tanımlandıklarında kaynakları tanımlayan anahtarlar, kaynak kodda istekte bulunan belirli kaynakları almak için de kullanılır. Koddan bir kaynağı almanın en kolay yolu, uygulamanızdaki çerçeve düzeyindeki nesnelerden <xref:System.Windows.FrameworkElement.FindResource%2A> veya <xref:System.Windows.FrameworkElement.TryFindResource%2A> yöntemini çağırmanız olabilir. Bu Yöntemler arasındaki davranış farkı, istenen anahtar bulunamazsa ne olur? <xref:System.Windows.FrameworkElement.FindResource%2A> bir özel durum oluşturur; <xref:System.Windows.FrameworkElement.TryFindResource%2A> bir özel durum oluşturmaz, ancak `null`döndürür. Her yöntem, kaynak anahtarını bir giriş parametresi olarak alır ve gevşek yazılmış bir nesne döndürür. Genellikle, kaynak anahtarı bir dizedir, ancak zaman zaman dize olmayan kullanımlar vardır; Ayrıntılar için [nesneleri anahtarlar olarak kullanma](#objectaskey) bölümüne bakın. Genellikle, döndürülen nesneyi, kaynak isteğinde bulunduğunuzu ayarladığınız özelliğin gerektirdiği türe atamalısınız. Kod kaynağı çözümleme için arama mantığı, dinamik kaynak başvurusu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] durumuyla aynıdır. Kaynak araması çağıran öğeden başlar, ardından mantıksal ağaçta ardışık üst öğelere devam eder. Arama, gerektiğinde uygulama kaynakları, Temalar ve sistem kaynakları ile devam eder. Kaynak için bir kod isteği, kaynak sözlüklerinde, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]yüklenen kaynak sözlüğünde daha sonra yapılmış olabilecek ve ayrıca gerçek zamanlı sistem kaynağı değişikliklerinde çalışma zamanı değişiklikleri için uygun şekilde hesaba sahip olur.  
  
 Aşağıda, bir kaynağı anahtara göre bulan ve döndürülen değeri bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisi olarak uygulanan bir özelliği ayarlamak için kullanan kısa bir örnek verilmiştir.  
  
 [!code-csharp[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#resourceproceduralget)]
 [!code-vb[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#resourceproceduralget)]  
  
 Kaynak başvurusunu atamaya yönelik alternatif bir yöntem <xref:System.Windows.FrameworkElement.SetResourceReference%2A>. Bu yöntem iki parametre alır: kaynağın anahtarı ve kaynak değerinin atanması gereken öğe örneğinde bulunan belirli bir bağımlılık özelliği için tanımlayıcı. İşlevsellik, bu yöntem aynıdır ve herhangi bir dönüş değeri ataması gerektirmeyen avantajına sahiptir.  
  
 Yine de kaynaklara programlı bir şekilde erişmenin başka bir yolu da <xref:System.Windows.FrameworkElement.Resources%2A> özelliğinin içeriğine sözlük olarak erişmektedir. Bu özelliğin içerdiği sözlüğe erişmek Ayrıca mevcut koleksiyonlara yeni kaynaklar ekleyebilmesinin yanı sıra, belirli bir anahtar adının koleksiyonda zaten alınmış olup olmadığını ve diğer sözlük/toplama işlemlerini denetleyebilirsiniz. Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasını tamamen kodda yazıyorsanız, kodda tüm koleksiyonu da oluşturabilir, ona anahtar atayabilir ve ardından tamamlanmış koleksiyonu, oluşturulan bir öğenin <xref:System.Windows.FrameworkElement.Resources%2A> özelliğine atayabilirsiniz. Bu, sonraki bölümde açıklanmaktadır.  
  
 Dizin olarak belirli bir anahtar kullanarak herhangi bir verili <xref:System.Windows.FrameworkElement.Resources%2A> koleksiyonu içinde dizin oluşturabilirsiniz, ancak kaynağa bu şekilde erişmenin, kaynak çözümleme 'nin normal çalışma zamanı kurallarını izlemez olduğunu unutmayın. Yalnızca belirli bir koleksiyona erişiyorsunuz. Kaynak arama, istenen anahtarda geçerli bir nesne bulunmazsa, köke veya uygulamaya geçiş yapılmaz. Ancak, bu yaklaşım, anahtar arama kapsamı daha kısıtlandığı için bazı durumlarda performans avantajlarına sahip olabilir. Kaynak sözlüğüyle doğrudan nasıl çalışılacağı hakkında daha fazla ayrıntı için <xref:System.Windows.ResourceDictionary> sınıfına bakın.  
  
<a name="creating"></a>   
## <a name="creating-resources-with-code"></a>Kodla kaynak oluşturma  
 Kodda bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasının tamamını oluşturmak isterseniz, kodda bu uygulamada herhangi bir kaynak oluşturmak da isteyebilirsiniz. Bunu elde etmek için yeni bir <xref:System.Windows.ResourceDictionary> örneği oluşturun ve ardından <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>yapılan birbirini izleyen çağrıları kullanarak tüm kaynakları sözlüğe ekleyin. Ardından, bu nedenle oluşturulan <xref:System.Windows.ResourceDictionary>, bir sayfa kapsamında bulunan bir öğe üzerinde <xref:System.Windows.FrameworkElement.Resources%2A> özelliğini veya <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>ayarlamak için kullanın. Ayrıca, <xref:System.Windows.ResourceDictionary> bağımsız bir nesne olarak bir öğeye eklemeden de koruyabilirsiniz. Ancak bunu yaparsanız, içindeki kaynaklara, genel bir sözlükte olduğu gibi öğe anahtarı ile erişmeniz gerekir. Öğe `Resources` özelliğine eklenmemiş bir <xref:System.Windows.ResourceDictionary>, öğe ağacının bir parçası olarak bulunmaz ve <xref:System.Windows.FrameworkElement.FindResource%2A> ve ilgili yöntemler tarafından kullanılabilecek bir arama dizisinde kapsam içermez.  
  
<a name="objectaskey"></a>   
## <a name="using-objects-as-keys"></a>Nesneleri anahtar olarak kullanma  
 Çoğu kaynak kullanımları, kaynağın anahtarını bir dize olacak şekilde ayarlar. Ancak, çeşitli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri, anahtarları belirtmek için bir dize türü kullanmaz, bunun yerine bu parametre bir nesnedir. Kaynağı bir nesne tarafından anahtarlaştırma özelliği, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stili ve tema desteği tarafından kullanılır. Diğer bir biçimde stilli olmayan bir denetim için varsayılan stil olan temalardaki stiller, her biri için uygulanmaları gereken denetimin <xref:System.Type> anahtarlanır. Türüne göre anahtarlan, her denetim türünün varsayılan örneklerinde çalışacak güvenilir bir arama mekanizması sağlar ve tür, yansıma tarafından algılanır ve türetilmiş türün varsayılan stili olmasa bile, türetilmiş sınıfların stillendirilmesini için kullanılabilir. [X:Type Işaretleme uzantısını](../../xaml-services/x-type-markup-extension.md)kullanarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tanımlanan bir kaynak için <xref:System.Type> anahtarı belirtebilirsiniz. [ComponentResourceKey Biçimlendirme Uzantısı](componentresourcekey-markup-extension.md)gibi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerini destekleyen diğer dize olmayan anahtar kullanımları için de benzer uzantılar vardır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kaynakları](xaml-resources.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
