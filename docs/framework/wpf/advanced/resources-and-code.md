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
ms.openlocfilehash: d36d30dd336bbe50b192b10a6a60d2c7e382adb8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61981961"
---
# <a name="resources-and-code"></a>Kaynaklar ve Kod
Bu genel bakışta nasıl yoğunlaşır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kaynakları erişilemez veya kod kullanılarak oluşturulan yerine [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] söz dizimi. Genel kaynak kullanımı ve kaynaklardan daha fazla bilgi için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sözdizimi açısından görmek [XAML kaynakları](xaml-resources.md).  

<a name="accessing"></a>   
## <a name="accessing-resources-from-code"></a>Kaynak kodundan erişme  
 Aracılığıyla tanımlanmışsa, kaynakları tanımlayan anahtarları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kaynak kodda istemesi durumunda belirli kaynakları almak için de kullanılır. Bir kaynak koddan almanın en basit yolu çağırmaktır <xref:System.Windows.FrameworkElement.FindResource%2A> veya <xref:System.Windows.FrameworkElement.TryFindResource%2A> uygulamanızdaki framework düzeyi nesnelerinden yöntemi. Davranış bu yöntemler arasında İstenen anahtar bulunamazsa ne olur farktır. <xref:System.Windows.FrameworkElement.FindResource%2A> bir özel durum oluşturur; <xref:System.Windows.FrameworkElement.TryFindResource%2A> döndürür ancak bir özel durum oluşturmaz `null`. Her yöntem giriş parametresi olarak kaynak anahtarı alır ve gevşek yazılmış bir nesne döndürür. Genellikle, bir kaynak anahtarı bir dizedir, ancak bazen dize olmayan kullanımları vardır; bkz: [nesneleri anahtar olarak kullanma](#objectaskey) ayrıntıları bölümü. Genellikle döndürülen nesne kaynak istenirken ayarlama özelliği tarafından gereken türünü dönüştürürsünüz. Kod kaynak çözümleme için arama mantığı dinamik kaynak başvurusu aynıdır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] çalışması. Kaynak Ara çağıran öğeden başlar ve ardından mantıksal ağaçta ardışık üst öğe olmaya devam eder. Arama ve sonraki sürümlerde uygulama kaynaklarını, temalar ve gerekirse, sistem kaynakları devam eder. Kod isteği bir kaynak için düzgün şekilde için gelen yüklenen kaynak sözlüğünden den yapılmış kaynak sözlükleri çalışma zamanı değişiklikleri hesaba katmayacak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], için ve ayrıca gerçek zamanlı sistem kaynağı değişiklikleri.  
  
 Anahtara göre bir kaynak bulur ve döndürülen değer olarak uygulanan bir özelliği ayarlamak için kullandığı bir kısa bir kod örneği verilmiştir bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisi.  
  
 [!code-csharp[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#resourceproceduralget)]
 [!code-vb[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#resourceproceduralget)]  
  
 Bir kaynak başvurusu atamak için alternatif bir yöntem <xref:System.Windows.FrameworkElement.SetResourceReference%2A>. Bu yöntem iki parametre alır: kaynak tanımlayıcı ve anahtar için kaynak değeri atanmalıdır öğesi örneği üzerinde mevcut olan belirli bir bağımlılık özelliği için. İşlevsel olarak, bu yöntem aynıdır ve dönüş değerlerinin herhangi bir atama gerektirmeyen avantajı vardır.  
  
 İçeriğine erişmek için kaynaklarına programlı olarak erişmek için hala başka bir yolu olan <xref:System.Windows.FrameworkElement.Resources%2A> özelliği bir sözlük olarak. Bu özellik tarafından içerilen sözlüğe erişme, ayrıca mevcut koleksiyon, koleksiyon ve diğer sözlük/toplama işlemlerinin belirli bir anahtar adı zaten alınmış olmadığını görmek için onay için yeni kaynaklar nasıl ekleyebileceğiniz yerdir. Yazıyorsanız bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasını tamamen kodda, ayrıca tüm koleksiyon kodda oluşturabilir, anahtarlar atayıncaya ve ardından tamamlanmış koleksiyonu atama <xref:System.Windows.FrameworkElement.Resources%2A> oluşturulmuş bir öğenin özellik. Bu, sonraki bölümde açıklanacaktır.  
  
 İçinde verilen herhangi bir dizine ekleyebilir <xref:System.Windows.FrameworkElement.Resources%2A> koleksiyonu dizin ancak, belirli bir anahtar kullanarak, bu şekilde kaynağa eriştiği kaynak çözüm normal çalışma zamanı kurallarına uymuyor uyumlu. Yalnızca bu belirli bir koleksiyon erişiyor. Geçerli nesne anahtarda bulunduysa kaynak arama kapsamı kök veya uygulama yapmayacaktır. Ancak, tam olarak anahtar için arama kapsamını daha kısıtlı olduğundan bu yaklaşım bazı durumlarda performans avantajlarını olabilir. Bkz: <xref:System.Windows.ResourceDictionary> doğrudan kaynak sözlüğü ile çalışma konusunda daha fazla ayrıntı için sınıf.  
  
<a name="creating"></a>   
## <a name="creating-resources-with-code"></a>Kaynak kodu ile oluşturma  
 Tüm oluşturmak istiyorsanız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama kodundaki ayrıca kodda bu uygulamadaki tüm kaynakları oluşturmak olmak isteyebilirsiniz. Bunu başarmak için yeni bir oluşturma <xref:System.Windows.ResourceDictionary> örneği ve art arda çağrılar kullanarak sözlük tüm kaynakları eklemek <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>. Ardından, <xref:System.Windows.ResourceDictionary> ayarlamak için bu nedenle oluşturulan <xref:System.Windows.FrameworkElement.Resources%2A> bir sayfa kapsamındaki mevcut olan bir öğe üzerinde özellik veya <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>. Aynı zamanda sürdürebilirsiniz <xref:System.Windows.ResourceDictionary> bir öğe ekleme olmadan tek başına nesne olarak. Ancak bunu yaparsanız, genel bir sözlük gibi öğe anahtarı tarafından içindeki kaynaklara erişmesi gerekir. A <xref:System.Windows.ResourceDictionary> iliştirilmemiş öğeye `Resources` özellik öğe ağacında bir parçası olarak mevcut değil ve yok kapsamı tarafından kullanılan arama dizisinde <xref:System.Windows.FrameworkElement.FindResource%2A> ve ilişkili yöntemleri.  
  
<a name="objectaskey"></a>   
## <a name="using-objects-as-keys"></a>Nesneleri anahtar olarak kullanma  
 Çoğu kaynak kullanımları anahtarını kaynağının adını bir dize olacak şekilde ayarlar. Ancak, çeşitli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri kasıtlı olmayan bir dize türü anahtarları belirtmek için kullanın, bunun yerine bu parametre bir nesnedir. Tarafından kullanılan bir nesne tarafından anahtarlanmış kaynağa sahip olma yeteneği [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stili ve Tema oluşturma desteği. Aksi takdirde stili olmayan bir denetim için varsayılan stil haline gelen tema stilleri her tarafından Anahtarlanan <xref:System.Type> uygulanması gereken denetimi. Türü tarafından Anahtarlanan her denetim türü varsayılan örneklerinde çalışan bir güvenilir arama mekanizmayı sağlar ve tür yansıma tarafından algılanır ve varsayılan stil türetilmiş tür sahip olsa da, türetilmiş sınıfların stil eklemek için kullanılır. Belirtebileceğiniz bir <xref:System.Type> içinde tanımlanan bir kaynak için anahtar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanarak [x: Type işaretleme uzantısı](../../xaml-services/x-type-markup-extension.md). Benzer uzantıları destekleyen diğer dize olmayan için anahtar kullanımları mevcut [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gibi özellikleri [ComponentResourceKey işaretleme uzantısı](componentresourcekey-markup-extension.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kaynakları](xaml-resources.md)
- [Stil ve Şablon Oluşturma](../controls/styling-and-templating.md)
