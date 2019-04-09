---
title: Bağlama Bildirimlerine Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- markup extensions [WPF]
- data binding [WPF], declarations
- object element syntax [WPF]
- binding data [WPF], declarations
- syntax [WPF], object elements
- binding declarations [WPF]
ms.assetid: b97fd626-4c0d-4761-872a-2bca5820da2c
ms.openlocfilehash: c0fcbc8054272356c39ba7925041ecef05a0322c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165275"
---
# <a name="binding-declarations-overview"></a>Bağlama Bildirimlerine Genel Bakış
Bu konuda bir bağlama bildirebilirsiniz farklı yolları açıklanmaktadır.  

<a name="Prereq"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda okumadan önce kavram ve biçimlendirme uzantısı kullanımı ile tanıdık önemlidir. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../advanced/markup-extensions-and-wpf-xaml.md).  
  
 Bu konuda, veri bağlama kavramları kapsamaz. Veri bağlama kavramları hakkında bilgi için bkz [Data Binding Overview](data-binding-overview.md).  
  
<a name="BindinginXAML"></a>   
## <a name="declaring-a-binding-in-xaml"></a>XAML bağlamasında bildirme  
 Bu bölümde, XAML bağlamasında bildirmek anlatılmaktadır.  
  
<a name="MarkupExtensionSyntax"></a>   
### <a name="markup-extension-usage"></a>Biçimlendirme uzantısı kullanımı  
 <xref:System.Windows.Data.Binding> bir işaretleme uzantısıdır. Bir bağlama bildirmek için bağlama uzantısının kullandığınızda, bildirimi tümcelerden bir dizi oluşur `Binding` anahtar sözcüğü ve virgül (,) tarafından ayrılır. Bağlama bildirimi yan tümceleri herhangi bir sırada olabilir ve birçok olası eşleştirme birleşimlerini vardır. Yan tümceleri olan *adı*=*değer* çiftlerini nerede *adı* adıdır <xref:System.Windows.Data.Binding> özelliği ve *değer* olduğu özellik için ayarladığınız değeri.  
  
 Bağlama bildirimi dizeleri biçimlendirme içinde oluştururken, hedef nesnenin belirli bir bağımlılık özelliği için bağlanmalıdır. Aşağıdaki örnek nasıl bağlanacağını gösterir <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> bağlama uzantısı kullanarak, belirtme özelliği <xref:System.Windows.Data.Binding.Source%2A> ve <xref:System.Windows.Data.Binding.Path%2A> özellikleri.  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]  
  
 Özelliklerinin çoğunu belirtebilirsiniz <xref:System.Windows.Data.Binding> bu şekilde sınıfı. Listesi hem de bağlama uzantıları hakkında daha fazla bilgi için <xref:System.Windows.Data.Binding> bağlama uzantısı kullanılarak ayarlanamaz özellikleri görmek [Binding Markup Extension](../advanced/binding-markup-extension.md) genel bakış.  
  
<a name="ObjectElementSyntax"></a>   
### <a name="object-element-syntax"></a>Nesne öğesi sözdizimi  
 Nesne öğesi sözdizimi bağlama bildirimi oluşturmak için bir alternatiftir. Çoğu durumda, işaretleme uzantısı ya da nesne öğesi sözdizimi kullanarak belirli bir avantajı yoktur. Ancak, işaretleme uzantısı gibi özellik değeri bir dize olmayan türü için hiçbir tür dönüştürme var olduğunda, senaryonuzun desteklemeyen bir durumda nesne öğesi sözdizimi kullanmanız gerekir.  
  
 Nesne öğesi sözdizimi hem biçimlendirme uzantısı kullanımı örneği verilmiştir:  
  
 [!code-xaml[BindConversionMarkup#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]  
  
 Örnek bağlar <xref:System.Windows.Controls.TextBlock.Foreground%2A> özelliğini uzantısı sözdizimi kullanarak bir bağlama bildirme. Bağlama bildirimi için <xref:System.Windows.Controls.TextBlock.Text%2A> özelliği nesne öğesi sözdizimi kullanır.  
  
 Farklı koşullar hakkında daha fazla bilgi için bkz. [içinde XAML söz dizimi ayrıntı](../advanced/xaml-syntax-in-detail.md).  
  
<a name="MBandPB"></a>   
### <a name="multibinding-and-prioritybinding"></a>MultiBinding ve PriorityBinding  
 <xref:System.Windows.Data.MultiBinding> ve <xref:System.Windows.Data.PriorityBinding> XAML uzantı sözdizimini desteklemez. Bu nedenle, bildirdiğiniz, nesne öğesi sözdizimi kullanmalısınız bir <xref:System.Windows.Data.MultiBinding> veya <xref:System.Windows.Data.PriorityBinding> XAML içinde.  
  
<a name="BindinginCode"></a>   
## <a name="creating-a-binding-in-code"></a>Kod içinde bağlama oluşturma  
 Doğrudan özelliklerini ayarlamak için bir bağlama belirtmenin başka bir yolu olan bir <xref:System.Windows.Data.Binding> kod nesnesi. Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Data.Binding> nesne ve kodda özellikleri belirtin.  Bu örnekte, `TheConverter` uygulayan bir nesnedir <xref:System.Windows.Data.IValueConverter> arabirimi.  
  
 [!code-csharp[BindConversion#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
 [!code-vb[BindConversion#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]  
  
 Dosyalar bağladığınız nesne ise bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> çağırabilirsiniz `SetBinding` yöntemi kullanmak yerine doğrudan nesneniz üzerinde <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>. Bir örnek için bkz. [kod içinde bağlama oluşturma](how-to-create-a-binding-in-code.md).  
  
<a name="Path_Syntax"></a>   
## <a name="binding-path-syntax"></a>Bağlama yolu sözdizimi  
 Kullanım <xref:System.Windows.Data.Binding.Path%2A> özelliği bağlamak istediğiniz kaynak değeri belirtmek için:  
  
-   En basit durumda, <xref:System.Windows.Data.Binding.Path%2A> özellik değeri, özelliğin gibi bağlama için kullanılacak kaynak nesnenin adını `Path=PropertyName`.  
  
-   Bir özelliğin alt özellikleri gibi benzer bir sözdizimi tarafından belirtilebilir C#. Örneğin, yan `Path=ShoppingCart.Order` bağlama alt özelliğini ayarlar `Order` nesne veya özelliğin `ShoppingCart`.  
  
-   Ekli bir özelliğine bağlamak için ekli özellik parantez içine yerleştirin. Örneğin, ekli özelliğe bağlayabileceğiniz şekilde <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, söz dizimi `Path=(DockPanel.Dock)`.  
  
-   Dizin oluşturucular bir özelliğin özellik adı, dizin oluşturucu uygulandığı aşağıdaki köşeli parantez içinde belirtilebilir. Örneğin, yan tümcesi `Path=ShoppingCart[0]` bağlamayı özelliğinizin iç dizin "0" sabit dizesini nasıl işlediğini karşılık gelen dizinini ayarlar. İç içe geçmiş dizin oluşturucular da desteklenir.  
  
-   İçinde dizin oluşturucular ve alt karışabilir bir `Path` yan tümcesi; Örneğin, `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`  
  
-   Dizin oluşturucular içinde virgülle (,) ayırarak, birden çok Dizin Oluşturucu parametreleri olabilir. Her parametre türü, parantez ile belirtilebilir. Örneğin, sahip `Path="[(sys:Int32)42,(sys:Int32)24]"`burada `sys` eşlenmiş `System` ad alanı.  
  
-   Kaynak koleksiyon görünümü olduğunda, geçerli öğenin bir eğik çizgi (/) ile belirtilebilir. Örneğin, yan tümcesi `Path=/` bağlama görünümünde geçerli öğeye ayarlar. Kaynak bir koleksiyon olduğunda, bu sözdizimini varsayılan koleksiyon görünümü geçerli öğesini belirtir.  
  
-   Özellik adlarının ve eğik çizgi koleksiyonları özellikleri geçirmek için birleştirilebilir. Örneğin, `Path=/Offices/ManagerName` içeren kaynak koleksiyonu geçerli öğesini belirtir bir `Offices` ayrıca bir koleksiyon özelliği. İçeren bir nesne kendi geçerli öğesi olan bir `ManagerName` özelliği.  
  
-   İsteğe bağlı olarak, bir nokta (.) yolu geçerli kaynağına bağlamak için kullanılabilir. Örneğin, `Text="{Binding}"` eşdeğerdir `Text="{Binding Path=.}"`.  
  
### <a name="escaping-mechanism"></a>Kaçış mekanizması  
  
-   Oluşturucular ([]) sonraki karakteri inceltme işareti (^) atlar.  
  
-   Ayarlarsanız <xref:System.Windows.Data.Binding.Path%2A> XAML içinde ayrıca XML dil tanımına özel belirli karakter kaçış (XML varlıkları kullanarak) gerekir:  
  
    -   Kullanım `&` karakteri kaçırmak için "&".  
  
    -   Kullanım `>` bitiş etiketi kaçış ">".  
  
-   Özniteliğin biçimlendirme uzantısı sözdizimi kullanarak tüm bağlamasında tanımlıyorsa, ayrıca, kaçış gerekir (ters eğik çizgi kullanarak \\) için özel karakterler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işaretleme uzantısı ayrıştırıcısı:  
  
    -   Ters eğik çizgi (\\) kaçış karakteri.  
  
    -   Eşittir (=) özellik adı, özellik değerinden ayırır.  
  
    -   Özellikleri virgül (,) ayırır.  
  
    -   Sağ küme ayracından (}) bir işaretleme uzantısı sonudur.  
  
<a name="Default"></a>   
## <a name="default-behaviors"></a>Varsayılan davranışları  
 Varsayılan davranış aşağıdaki gibidir belirtilmezse bildiriminde.  
  
-   Varsayılan dönüştürücü bağlama kaynağı ve bağlama hedef değeri arasında bir tür dönüştürmesi yapmak için çalışan oluşturulur. Varsayılan dönüştürücü döndüren bir dönüştürme yapılamazsa `null`.  
  
-   Ayarlanmamış olması halinde <xref:System.Windows.Data.Binding.ConverterCulture%2A>, bağlama altyapısı kullanır `Language` bağlama hedef nesnenin özellik. XAML, bu "en-US" varsayılan olarak veya bir açıkça alındıysa değerin kök öğe (veya herhangi bir öğe) sayfasının devralır.  
  
-   Bağlama sürece zaten bir veri bağlamı (örneğin, bir üst öğeden gelen devralınan veri bağlamından) varsa ve seçtiğiniz öğe veya bu bağlam tarafından iade edilen koleksiyon daha fazla yolu değiştirilmesine gerek kalmadan bağlama için uygun olan bir bildirimi bağlama hiçbir yan tümceye sahip neden: `{Binding}` Bu genellikle bir bağlama verileri, burada bir koleksiyon bağlama gibi stil oluşturma için belirtilen yoludur. Daha fazla bilgi için bkz. "Tüm nesnelerin kaynak olarak kullanılan bir bağlama" bölümünde [bağlama kaynaklarına genel bakış](binding-sources-overview.md).  
  
-   Varsayılan <xref:System.Windows.Data.Binding.Mode%2A> arasında tek yönlü ve çift yönlü bağlı olduğu bağımlılık özelliği bağlı olarak değişir. Bağlama modu, açıkça bağlamanız istenen davranışı olduğundan emin olmak için her zaman bildirebilirsiniz. Genel, kullanıcı tarafından düzenlenebilen denetim özellikleri gibi <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> ve <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType>, diğer özelliklerin çoğu tek yönlü bağlamalar ise iki yönlü bağlamaları için varsayılan.  
  
-   Varsayılan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değeri arasında değişir <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> ve <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> ilişkili bağımlılık özelliği de bağlı olarak. Bağımlılık özelliklerinin çoğu için varsayılan değerdir <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, ancak <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> özelliği varsayılan değerine sahip <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
- [Veri Bağlama](../advanced/optimizing-performance-data-binding.md)
- [PropertyPath XAML Sözdizimi](../advanced/propertypath-xaml-syntax.md)
