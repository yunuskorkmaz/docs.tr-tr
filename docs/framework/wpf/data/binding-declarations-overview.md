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
ms.openlocfilehash: bc3a139db80066c9cad5199c7734fe66a8639400
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460035"
---
# <a name="binding-declarations-overview"></a>Bağlama Bildirimlerine Genel Bakış

Bu konuda, bağlamayı bildirebilmeniz için farklı yollar ele alınmaktadır.

<a name="Prereq"></a>

## <a name="prerequisites"></a>Prerequisites

Bu konuyu okumadan önce, biçimlendirme uzantılarının kavram ve kullanımı hakkında bilgi sahibi olmanız önemlidir. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](../advanced/markup-extensions-and-wpf-xaml.md).

Bu konu, veri bağlama kavramlarını kapsamaz. Veri bağlama kavramlarıyla ilgili bir tartışma için bkz. [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md).

<a name="BindinginXAML"></a>

## <a name="declaring-a-binding-in-xaml"></a>XAML 'de bağlama bildirme

Bu bölümde, XAML 'de bir bağlamanın nasıl bildirildiği açıklanmaktadır.

<a name="MarkupExtensionSyntax"></a>

### <a name="markup-extension-usage"></a>Biçimlendirme uzantısı kullanımı

<xref:System.Windows.Data.Binding>, biçimlendirme uzantısıdır. Bağlamayı bildirmek için bağlama uzantısını kullandığınızda, bildirim, `Binding` anahtar sözcüğünü izleyen ve virgüllerle (,) ayrılmış bir dizi yan tümce oluşur. Bağlama bildirimindeki yan tümceler herhangi bir sırada olabilir ve birçok olası bileşim vardır. Yan tümceler ad *=* *değer* çiftleridir; burada *ad* <xref:System.Windows.Data.Binding> özelliğinin adıdır ve *değer* özellik için ayarladığınız değerdir.

Biçimlendirme içinde bağlama bildirimi dizeleri oluştururken, bir hedef nesnenin belirli bağımlılık özelliğine eklenmelidir. Aşağıdaki örnek, <xref:System.Windows.Data.Binding.Source%2A> ve <xref:System.Windows.Data.Binding.Path%2A> özelliklerini belirterek bağlama uzantısı kullanılarak <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> özelliğinin nasıl bağlanacağını gösterir.

[!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]

<xref:System.Windows.Data.Binding> sınıfının özelliklerinin çoğunu bu şekilde belirtebilirsiniz. Bağlama uzantısı ve bağlama uzantısı kullanılarak ayarlanamaz <xref:System.Windows.Data.Binding> özelliklerinin bir listesi hakkında daha fazla bilgi için [bağlama biçimlendirme uzantısına](../advanced/binding-markup-extension.md) genel bakış bölümüne bakın.

<a name="ObjectElementSyntax"></a>

### <a name="object-element-syntax"></a>Nesne öğesi sözdizimi

Nesne öğesi sözdizimi, bağlama bildirimi oluşturmak için bir alternatiftir. Çoğu durumda, biçimlendirme uzantısı ya da nesne öğesi söz dizimi kullanmanın belirli bir avantajı yoktur. Ancak, biçimlendirme uzantısının senaryonuzu desteklemediği durumlarda (örneğin, özellik değerinin, hiçbir tür dönüştürmesi bulunmayan bir dize olmayan türde olması gibi), nesne öğesi söz dizimini kullanmanız gerekir.

Aşağıdaki, hem nesne öğesi sözdiziminin hem de biçimlendirme uzantısı kullanımının bir örneğidir:

[!code-xaml[BindConversionMarkup#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]

Örnek, uzantı sözdizimini kullanarak bir bağlama bildirerek <xref:System.Windows.Controls.TextBlock.Foreground%2A> özelliğini bağlar. <xref:System.Windows.Controls.TextBlock.Text%2A> özelliği için bağlama bildirimi nesne öğesi sözdizimini kullanır.

Farklı terimler hakkında daha fazla bilgi için bkz. [XAML sözdizimi ayrıntılı](../advanced/xaml-syntax-in-detail.md).

<a name="MBandPB"></a>

### <a name="multibinding-and-prioritybinding"></a>MultiBinding ve PriorityBinding

<xref:System.Windows.Data.MultiBinding> ve <xref:System.Windows.Data.PriorityBinding> XAML uzantısı söz dizimini desteklemez. Bu nedenle, XAML 'de bir <xref:System.Windows.Data.MultiBinding> veya <xref:System.Windows.Data.PriorityBinding> bildirirken nesne öğesi sözdizimini kullanmanız gerekir.

<a name="BindinginCode"></a>

## <a name="creating-a-binding-in-code"></a>Kod içinde bağlama oluşturma

Bağlama belirtmenin başka bir yolu da kodda <xref:System.Windows.Data.Binding> nesne üzerinde doğrudan Özellikler ayarlanmektir. Aşağıdaki örnek, bir <xref:System.Windows.Data.Binding> nesnesinin nasıl oluşturulduğunu ve koddaki özelliklerin nasıl kullanılacağını gösterir.  Bu örnekte, `TheConverter` <xref:System.Windows.Data.IValueConverter> arabirimini uygulayan bir nesnedir.

[!code-csharp[BindConversion#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
[!code-vb[BindConversion#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]

Bağladığınız nesne bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> ise, <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>kullanmak yerine doğrudan nesneniz üzerinde `SetBinding` yöntemini çağırabilirsiniz. Bir örnek için bkz. [kodda bağlama oluşturma](how-to-create-a-binding-in-code.md).

<a name="Path_Syntax"></a>

## <a name="binding-path-syntax"></a>Bağlama yolu sözdizimi

Bağlamak istediğiniz kaynak değeri belirtmek için <xref:System.Windows.Data.Binding.Path%2A> özelliğini kullanın:

- En basit durumda, <xref:System.Windows.Data.Binding.Path%2A> Özellik değeri, bağlama için kullanılacak kaynak nesnenin özelliğinin adıdır, örneğin, `Path=PropertyName`.

- Özelliğin alt özellikleri, ile benzer bir sözdizimi ile belirtilebilir C#. Örneğin, yan tümce `Path=ShoppingCart.Order` nesnenin veya özelliğin `ShoppingCart`alt özellik `Order` bağlamayı ayarlar.

- Ekli özelliğe bağlamak için iliştirilmiş özelliğin çevresine parantez koyun. Örneğin, ekli özelliği <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>bağlamak için sözdizimi `Path=(DockPanel.Dock)`.

- Bir özelliğin Dizin oluşturucular, dizin oluşturucunun uygulandığı özellik adından sonra köşeli ayraç içinde belirtilebilir. Örneğin, yan tümce `Path=ShoppingCart[0]`, özelliğinin iç dizin oluşturma işleminin "0" sabit dizesini nasıl işleyimine karşılık gelen dizine bağlamayı ayarlar. İç içe dizinleyiciler de desteklenir.

- Dizin oluşturucular ve alt özellikler bir `Path` yan tümcesinde karışık olabilir; Örneğin, `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`

- Dizin oluşturucular içinde, virgülle ayrılmış birden çok dizin oluşturucu parametresi olabilir (,). Her parametrenin türü parantez ile belirtilebilir. Örneğin, `sys` `System` ad alanına eşlendiği `Path="[(sys:Int32)42,(sys:Int32)24]"`sahip olabilirsiniz.

- Kaynak bir koleksiyon görünümü olduğunda, geçerli öğe eğik çizgiyle (/) belirtilebilir. Örneğin, yan tümce `Path=/` görünümdeki geçerli öğeye bağlamayı ayarlar. Kaynak bir koleksiyon olduğunda, bu söz dizimi varsayılan koleksiyon görünümünün geçerli öğesini belirtir.

- Özellik adları ve eğik çizgiler, Koleksiyonlar olan özellikleri çapraz gezmek için birleştirilebilir. Örneğin, `Path=/Offices/ManagerName`, aynı zamanda bir koleksiyon olan bir `Offices` özelliğini içeren kaynak koleksiyonun geçerli öğesini belirtir. Geçerli öğe bir `ManagerName` özelliği içeren bir nesnedir.

- İsteğe bağlı olarak, bir nokta (.) yolu geçerli kaynağa bağlamak için kullanılabilir. Örneğin, `Text="{Binding}"` `Text="{Binding Path=.}"`eşdeğerdir.

### <a name="escaping-mechanism"></a>Kaçış mekanizması

- Dizin oluşturucular ([]) içinde, giriş işareti karakteri (^) sonraki karakteri çıkar.

- XAML 'de <xref:System.Windows.Data.Binding.Path%2A> ayarlarsanız, XML dil tanımına özel olan belirli karakterler de (XML varlıkları kullanarak) kaçış yapmanız gerekir:

  - "&" Karakterinden kaçınmak için `&` kullanın.

  - ">" Bitiş etiketini atlamak için `>` kullanın.

- Ayrıca, biçimlendirme uzantısı söz dizimini kullanarak bir öznitelikte tüm bağlamayı açıklamanız durumunda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işaretleme uzantısı ayrıştırıcısına özel olan (ters eğik çizgi \\) karakterler kullanmanız gerekir:

  - Ters eğik çizgi (\\), kaçış karakteridir.

  - Eşittir işareti (=) özellik değerinden özellik adını ayırır.

  - Virgül (,) özellikleri ayırır.

  - Sağ küme ayracı (}), biçimlendirme uzantısının sonu.

<a name="Default"></a>

## <a name="default-behaviors"></a>Varsayılan davranışlar

Bildirimde belirtilmemişse varsayılan davranış aşağıdaki gibidir.

- Bağlama kaynak değeri ile bağlama hedefi değeri arasında tür dönüştürmesi yapmaya çalışan bir varsayılan dönüştürücü oluşturulur. Bir dönüştürme yapılamaz, varsayılan dönüştürücü `null`döndürür.

- <xref:System.Windows.Data.Binding.ConverterCulture%2A>ayarlanmamışsa, bağlama altyapısı bağlama hedef nesnesinin `Language` özelliğini kullanır. XAML 'de, bu varsayılan olarak "en-US" ya da bir değer açıkça ayarlandıysa, sayfanın kök öğesinden (veya herhangi bir öğeden) değeri devralır.

- Bağlama zaten bir veri bağlamına sahip olduğu sürece (örneğin, bir üst öğeden gelen devralınan veri bağlamı) ve bu bağlam tarafından döndürülen herhangi bir öğe veya koleksiyon, daha fazla yol değişikliği gerekmeden bağlama için uygundur bağlama bildiriminde hiçbir yan tümce bulunamaz: `{Binding}` bu genellikle bağlamanın bir koleksiyon üzerinde çalıştığı veri stili için bir bağlamanın belirtilme yoludur. Daha fazla bilgi için [bağlama kaynaklarına genel bakış](binding-sources-overview.md)konusunun "bağlama kaynağı olarak kullanılan tüm nesneler" bölümüne bakın.

- Varsayılan <xref:System.Windows.Data.Binding.Mode%2A>, bağlanmakta olan bağımlılık özelliğine bağlı olarak tek yönlü ve iki yönlü farklılık gösterir. Bağlamalarınızın istenen davranışa sahip olduğundan emin olmak için bağlama modunu her zaman açıkça bildirebilirsiniz. Genel olarak, <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> ve <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType>gibi kullanıcı tarafından düzenlenebilir denetim özellikleri varsayılan olarak iki yönlü bağlamalara, diğer özelliklerin çoğu tek yönlü bağlamalara varsayılan olarak.

- Varsayılan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değeri, bağlı bağımlılık özelliğine göre <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> ve <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> arasında değişir. Bağımlılık özelliklerinin çoğu için varsayılan değer <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> özelliğinin varsayılan <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>değeri vardır.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
- [Veri Bağlama](../advanced/optimizing-performance-data-binding.md)
- [PropertyPath XAML Söz Dizimi](../advanced/propertypath-xaml-syntax.md)
