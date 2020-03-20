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
ms.openlocfilehash: 2917c9d15a6195c2d67781d6b2cfb0a5f1c136d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187165"
---
# <a name="resources-and-code"></a>Kaynaklar ve Kod
Bu genel bakış, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kaynakların sözdizimi yerine [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kod kullanılarak nasıl erişilebildiği veya oluşturulabileceği üzerinde yoğunlaşmışolur. Sözdizimi açısından genel kaynak kullanımı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve kaynakları hakkında daha fazla bilgi için [Bkz. XAML Kaynakları.](xaml-resources.md)  

<a name="accessing"></a>
## <a name="accessing-resources-from-code"></a>Koddan Kaynaklara Erişim  
 Kaynaklar tanımlanıyorsa tanımlayan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] anahtarlar, kaynağı kod olarak talep ederseniz belirli kaynakları almak için de kullanılır. Bir kaynağı koddan almanın en basit yolu, uygulamanızdaki çerçeve düzeyindeki nesnelerden ya da <xref:System.Windows.FrameworkElement.FindResource%2A> <xref:System.Windows.FrameworkElement.TryFindResource%2A> yöntemi aramaktır. Bu yöntemler arasındaki davranış farkı, istenen anahtar bulunamazsa ne olacağıdır. <xref:System.Windows.FrameworkElement.FindResource%2A>bir istisna getirir; <xref:System.Windows.FrameworkElement.TryFindResource%2A> bir özel durum yükseltmez, ancak döndürür. `null` Her yöntem kaynak anahtarını giriş parametresi olarak alır ve gevşek bir şekilde yazılan nesneyi döndürür. Genellikle, kaynak anahtarı bir dizedir, ancak zaman zaman nonstring kullanımları vardır; ayrıntılar için [Nesneleri Keys olarak kullanma](#objectaskey) bölümüne bakın. Genellikle, döndürülen nesneyi kaynağı isterken ayarladığınız özelliğin gerektirdiği türe atarsınız. Kod kaynağı çözümlemesi için arama mantığı dinamik [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kaynak başvuru örneğiyle aynıdır. Kaynak arama sı çağrı öğesinden başlar, ardından mantıksal ağaçtaki ardışık üst öğeler devam edin. Arama, gerekirse uygulama kaynaklarına, temalara ve sistem kaynaklarına doğru devam eder. Kaynak için bir kod isteği, kaynak sözlüklerinden yüklenen [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kaynak sözlüklerinden sonra yapılmış olabilecek çalışma zamanı değişikliklerini ve ayrıca gerçek zamanlı sistem kaynak değişikliklerini düzgün bir şekilde hesaba katar.  
  
 Aşağıda, anahtara göre bir kaynak bulan ve olay işleyicisi olarak uygulanan <xref:System.Windows.Controls.Primitives.ButtonBase.Click> bir özellik ayarlamak için döndürülen değeri kullanan kısa bir kod örneği verilmiştir.  
  
 [!code-csharp[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#resourceproceduralget)]
 [!code-vb[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#resourceproceduralget)]  
  
 Kaynak başvurusu atamak için alternatif <xref:System.Windows.FrameworkElement.SetResourceReference%2A>bir yöntem. Bu yöntem iki parametre alır: kaynak anahtarı ve kaynak değerinin atanması gereken öğe örneğinde bulunan belirli bir bağımlılık özelliği için tanımlayıcı. İşlevsel olarak, bu yöntem aynıdır ve iade değerlerinin herhangi bir döküm gerektirmeyen avantajı vardır.  
  
 Yine de kaynaklara programlı olarak erişmenin <xref:System.Windows.FrameworkElement.Resources%2A> başka bir yolu da, bir sözlük olarak özelliğin içeriğine erişmektir. Bu özelliğin içerdiği sözlüklere erişmek, varolan koleksiyonlara yeni kaynaklar eklemenin, koleksiyonda belirli bir anahtar adının zaten alınıp alınıp alınıp alınmadığını ve diğer sözlük/toplama işlemlerine nasıl ekleyebileceğinizdir. Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamayı tamamen kodla yazıyorsanız, tüm koleksiyonu kod halinde oluşturabilir, anahtarları atayabilir ve tamamlanmış koleksiyonu <xref:System.Windows.FrameworkElement.Resources%2A> yerleşik bir öğenin özelliğine atayabilirsiniz. Bu bir sonraki bölümde açıklanacaktır.  
  
 Dizin olarak belirli <xref:System.Windows.FrameworkElement.Resources%2A> bir anahtar kullanarak belirli bir koleksiyon içinde dizin ekleyebilirsiniz, ancak kaynağa bu şekilde erişimin normal çalışma zamanı kaynak çözümleme kurallarına uymadığını unutmayın. Yalnızca belirli bir koleksiyona erişebiliyorsun. İstenen anahtarda geçerli bir nesne bulunamazsa, kaynak araması kapsamı köke veya uygulamaya geçmeyecek. Ancak, anahtar için arama kapsamı daha kısıtlı olduğundan, bu yaklaşım bazı durumlarda tam olarak performans avantajları olabilir. Kaynak <xref:System.Windows.ResourceDictionary> sözlüğüyle doğrudan nasıl çalışacağınız hakkında daha fazla bilgi için sınıfa bakın.  
  
<a name="creating"></a>
## <a name="creating-resources-with-code"></a>Kodla Kaynak Oluşturma  
 Tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamayı kod halinde oluşturmak istiyorsanız, bu uygulamada kod içinde herhangi bir kaynak da oluşturmak isteyebilirsiniz. Bunu başarmak için yeni <xref:System.Windows.ResourceDictionary> bir örnek oluşturun ve ardışık çağrıları kullanarak <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>tüm kaynakları bir biri ardına gelen çağrıları kullanarak sözlükte ekleyin. Daha sonra, <xref:System.Windows.ResourceDictionary> böylece bir <xref:System.Windows.FrameworkElement.Resources%2A> sayfa kapsamında mevcut bir öğe veya . <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> Ayrıca, bir <xref:System.Windows.ResourceDictionary> öğeye eklemeden bağımsız bir nesne olarak koruyabilirsiniz. Ancak, bunu yaparsanız, genel bir sözlük gibi, öğe anahtarı ile içindeki kaynaklara erişmelisiniz. Bir <xref:System.Windows.ResourceDictionary> öğe `Resources` özelliğine bağlı olmayan bir öğe ağacının bir parçası olarak var olmaz ve ve tarafından <xref:System.Windows.FrameworkElement.FindResource%2A> ve ilgili yöntemler tarafından kullanılabilecek bir arama sırasına hiçbir kapsamı vardır.  
  
<a name="objectaskey"></a>
## <a name="using-objects-as-keys"></a>Nesneleri Anahtar Olarak Kullanma  
 Çoğu kaynak kullanımı, kaynağın anahtarını bir dize olarak ayarlar. Ancak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çeşitli özellikler kasıtlı olarak anahtarları belirtmek için bir dize türü kullanmayın, bunun yerine bu parametre bir nesnedir. Kaynağın bir nesne tarafından anahtarlanması [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliği stil ve temalı destek tarafından kullanılır. Başka bir şekilde tarz olmayan bir denetim için varsayılan stil haline gelen <xref:System.Type> temalardaki stillerin her biri, başvurmaları gereken denetimin her biri tarafından anahtarlanır. Türe göre anahtarlı olmak, her denetim türünün varsayılan örnekleriüzerinde çalışan güvenilir bir arama mekanizması sağlar ve türemiş türde varsayılan bir stil olmasa bile, yansıma tarafından algılanabilir ve türemiş sınıfları şekillendirmek için kullanılabilir. [X:Type Markup](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)Extension'ı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanarak tanımlanan bir kaynak için bir <xref:System.Type> anahtar belirtebilirsiniz. [BileşenKaynak Anahtar Biçimlendirme Uzantısı](componentresourcekey-markup-extension.md)gibi özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] destekleyen diğer nonstring anahtar kullanımları için benzer uzantılar vardır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kaynakları](xaml-resources.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
