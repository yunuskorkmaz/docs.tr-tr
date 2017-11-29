---
title: Kaynaklar ve Kod
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
- keys [WPF], using objects as
- resources [WPF], accessing from procedural code
- procedural code [WPF], creating resources with
- procedural code [WPF], accessing resources from
- resources [WPF], creating with procedural code
ms.assetid: c1cfcddb-e39c-41c8-a7f3-60984914dfae
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1177f7eeb2b6184ea6ae0a021730658913a4794b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="resources-and-code"></a>Kaynaklar ve Kod
Bu genel bakışta nasıl yoğunlaşır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kaynakları erişilen veya kod kullanılarak oluşturulan yerine [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sözdizimi. Genel kaynak kullanımı ve kaynaklardan hakkında daha fazla bilgi için bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sözdizimi açısından bkz [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
  
  
<a name="accessing"></a>   
## <a name="accessing-resources-from-code"></a>Koddan kaynaklara erişim  
 Üzerinden tanımlanmışsa kaynakları tanımlayan anahtarlarını [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kaynak kodda istenmişse belirli kaynakları almak için de kullanılır. Koddan bir kaynağı almanın en basit yolu çağırmaktır <xref:System.Windows.FrameworkElement.FindResource%2A> veya <xref:System.Windows.FrameworkElement.TryFindResource%2A> uygulamanızdaki çerçeve düzeyi nesnelerinden yöntemi. Bu yöntemleri arasındaki davranış farkı İstenen anahtar bulunamazsa olur. <xref:System.Windows.FrameworkElement.FindResource%2A>bir özel durum oluşturur; <xref:System.Windows.FrameworkElement.TryFindResource%2A> verir ancak bir özel durum oluşturmaz `null`. Her yöntem giriş parametresi olarak kaynak anahtarını alır ve gevşek yazılmış bir nesne döndürür. Genellikle, bir kaynak anahtarı bir dizedir, ancak bazen dize olmayan kullanımları vardır; bkz: [nesneleri anahtar olarak kullanma](#objectaskey) ayrıntıları bölümü. Genellikle, kaynak isterken ayarlıyorsanız özelliği tarafından gerekli olan türü döndürülen nesneyi dönüştürürsünüz. Kod kaynağı çözünürlüğü için arama mantığı dinamik kaynak başvurusu ile aynıdır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] durumda. Kaynaklar için arama arama öğeden başlar, sonra mantıksal ağacındaki art arda üst öğeler devam eder. Arama ve sonraki sürümleri uygulama kaynakları, temalar ve sistem kaynaklarını gerekirse devam eder. Bir kaynak için bir kod istek düzgün gelen yüklenen kaynak sözlüğünden sonra yapılmış kaynak sözlüklerindeki çalışma zamanı değişiklikleri hesaba katmayacak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], için ve ayrıca gerçek zamanlı sistem kaynak değişiklikleri.  
  
 Aşağıdaki bir kaynak anahtarını bulan ve döndürülen değer olarak uygulanan bir özellik ayarlamak için kullandığı bir kısa bir kod örneğidir bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisi.  
  
 [!code-csharp[PropertiesOvwSupport#ResourceProceduralGet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#resourceproceduralget)]
 [!code-vb[PropertiesOvwSupport#ResourceProceduralGet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#resourceproceduralget)]  
  
 Kaynak başvuru atamak için alternatif bir yöntem <xref:System.Windows.FrameworkElement.SetResourceReference%2A>. Bu yöntemi iki parametre alır: olduğu kaynak değeri atanabilir öğesi örneği üzerinde mevcut olan belirli bağımlılık özelliği için kaynak tanımlayıcısını ve anahtar. İşlevsel olarak, bu yöntem aynıdır ve dönüş değerlerinin herhangi bir atama gerektirmeyen avantajı vardır.  
  
 İçeriğine erişmek için kaynaklarına programlı olarak erişmek için hala başka bir yol olduğu <xref:System.Windows.FrameworkElement.Resources%2A> özelliği bir sözlük olarak. Bu özellik tarafından içerilen sözlük erişim de mevcut Koleksiyonlara, verilen bir anahtar adının zaten koleksiyonu ve diğer sözlük/toplama işlemleri alınmışsa denetleyin yeni kaynaklar nasıl ekleyebileceğiniz olur. Yazıyorsanız bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasını tamamen kodda, ayrıca tüm koleksiyon kodda oluşturabilir, anahtar atayabilir ve tamamlanmış koleksiyonu atamak <xref:System.Windows.FrameworkElement.Resources%2A> oluşturulmuş bir öğenin özellik. Bu sonraki bölümde açıklanacaktır.  
  
 Verilen herhangi içinde dizin <xref:System.Windows.FrameworkElement.Resources%2A> dizini, ancak belirli bir anahtar kullanarak koleksiyonu kaynağa bu şekilde erişmenin kaynak çözünürlüğünün normal çalışma zamanı kurallarını izlemeyeceğini farkında olması. Yalnızca o belirli koleksiyona erişiyorsunuz. Geçerli bir nesne anahtarda bulunursa kaynak arama kapsamı kök veya uygulama yapmayacaktır. Ancak, tam olarak anahtar için arama kapsamını daha kısıtlı olduğundan bu yaklaşım bazı durumlarda performans yararları olabilir. Bkz: <xref:System.Windows.ResourceDictionary> kaynak sözlüğü ile doğrudan çalışma konusunda daha fazla ayrıntı için sınıf.  
  
<a name="creating"></a>   
## <a name="creating-resources-with-code"></a>Kod ile kaynakları oluşturma  
 Tüm oluşturmak istiyorsanız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama kodundaki ayrıca kod bu uygulamadaki tüm kaynakları oluşturmak olmak isteyebilirsiniz. Bunu başarmak için yeni bir oluşturma <xref:System.Windows.ResourceDictionary> örneği ve art arda çağrılar kullanarak sözlük tüm kaynakları eklemek <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>. Ardından, <xref:System.Windows.ResourceDictionary> böylece ayarlamak için oluşturulan <xref:System.Windows.FrameworkElement.Resources%2A> sayfa kapsamda olan bir öğeyi özellikte veya <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>. Ayrıca sürdürebilirsiniz <xref:System.Windows.ResourceDictionary> bir öğeye eklemeden tek başına nesne olarak. Ancak, bunu yaparsanız, genel bir sözlük değilmiş gibi öğe anahtarı tarafından içindeki kaynaklara erişmesi gerekir. A <xref:System.Windows.ResourceDictionary> iliştirilmemiş bir öğe olarak `Resources` özelliği öğe ağacının bir parçası olarak mevcut değil ve hiçbir tarafından kullanılan bir arama sırası kapsamında olan <xref:System.Windows.FrameworkElement.FindResource%2A> ve ilgili yöntemler.  
  
<a name="objectaskey"></a>   
## <a name="using-objects-as-keys"></a>Nesneleri anahtar olarak kullanma  
 Çoğu kaynak kullanımları bir dize olacak şekilde kaynak anahtarı ayarlar. Ancak, çeşitli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri kasıtlı olarak kullanmayın bir dize türü anahtarları belirtmek için bunun yerine bu parametre bir nesnedir. Nesne tarafından anahtarlanmış kaynağa sahip olma yeteneği tarafından kullanılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stili ve tema desteği. Aksi durumda stili olmayan bir denetim için varsayılan stil haline gelen Temalar içindeki stillerin her tarafından Anahtarlanan <xref:System.Type> uygulanması gereken denetimi. Türe göre anahtarlı her denetim türünün varsayılan örnekleri üzerinde çalışan güvenilir bir arama mekanizması sağlar ve türü yansıma tarafından algılanır ve türetilmiş bir tür Aksi takdirde varsayılan stil yok olmasına rağmen türetilen sınıflar stil eklemek için kullanılır. Belirleyebileceğiniz bir <xref:System.Type> tanımlanan bir kaynak için anahtar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanarak [x: Type işaretleme uzantısı](../../../../docs/framework/xaml-services/x-type-markup-extension.md). Benzer uzantılar destekleyen diğer dize olmayan anahtar kullanımları için mevcut [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gibi özellikleri [ComponentResourceKey Biçimlendirme Uzantısı](../../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
