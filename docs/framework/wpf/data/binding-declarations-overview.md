---
title: Bağlama Bildirimlerine Genel Bakış
description: Windows Presentation Foundation (WPF) içinde uygulama geliştirme için XAML 'de bir bağlama bildirme hakkında bilgi edinin.
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
ms.openlocfilehash: 8d4943de0cacb5fe0b5a0c37a5a68f15243ad528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619643"
---
# <a name="binding-declarations-overview"></a>Bağlama Bildirimlerine Genel Bakış

Bu konuda, bağlamayı bildirebilmeniz için farklı yollar ele alınmaktadır.

<a name="Prereq"></a>

## <a name="prerequisites"></a>Ön koşullar

Bu konuyu okumadan önce, biçimlendirme uzantılarının kavram ve kullanımı hakkında bilgi sahibi olmanız önemlidir. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](../advanced/markup-extensions-and-wpf-xaml.md).

Bu konu, veri bağlama kavramlarını kapsamaz. Veri bağlama kavramlarıyla ilgili bir tartışma için bkz. [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md).

<a name="BindinginXAML"></a>

## <a name="declaring-a-binding-in-xaml"></a>XAML 'de bağlama bildirme

Bu bölümde, XAML 'de bir bağlamanın nasıl bildirildiği açıklanmaktadır.

<a name="MarkupExtensionSyntax"></a>

### <a name="markup-extension-usage"></a>Biçimlendirme uzantısı kullanımı

<xref:System.Windows.Data.Binding>bir biçimlendirme uzantısıdır. Bağlamayı bildirmek için bağlama uzantısını kullandığınızda, bildirim, `Binding` anahtar sözcüğünü izleyen ve virgüllerle (,) ayrılmış bir dizi yan tümce oluşur. Bağlama bildirimindeki yan tümceler herhangi bir sırada olabilir ve birçok olası bileşim vardır. Yan *tümceler ad* = *değer* çiftleridir; burada *ad* , <xref:System.Windows.Data.Binding> özelliğin adıdır ve *değer* özellik için ayarladığınız değerdir.

Biçimlendirme içinde bağlama bildirimi dizeleri oluştururken, bir hedef nesnenin belirli bağımlılık özelliğine eklenmelidir. Aşağıdaki örnek, <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> ve özelliklerini belirterek bağlama uzantısı kullanılarak özelliğin nasıl bağlanacağını gösterir <xref:System.Windows.Data.Binding.Source%2A> <xref:System.Windows.Data.Binding.Path%2A> .

[!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]

<xref:System.Windows.Data.Binding>Bu şekilde sınıfın özelliklerinin çoğunu belirtebilirsiniz. Bağlama uzantısı ve bağlama uzantısı kullanılarak ayarlanamaz özellikler listesi hakkında daha fazla bilgi için <xref:System.Windows.Data.Binding> [bağlama biçimlendirme uzantısına](../advanced/binding-markup-extension.md) genel bakış konusuna bakın.

<a name="ObjectElementSyntax"></a>

### <a name="object-element-syntax"></a>Nesne öğesi sözdizimi

Nesne öğesi sözdizimi, bağlama bildirimi oluşturmak için bir alternatiftir. Çoğu durumda, biçimlendirme uzantısı ya da nesne öğesi söz dizimi kullanmanın belirli bir avantajı yoktur. Ancak, biçimlendirme uzantısının senaryonuzu desteklemediği durumlarda (örneğin, özellik değerinin, hiçbir tür dönüştürmesi bulunmayan bir dize olmayan türde olması gibi), nesne öğesi söz dizimini kullanmanız gerekir.

Aşağıdaki, hem nesne öğesi sözdiziminin hem de biçimlendirme uzantısı kullanımının bir örneğidir:

[!code-xaml[BindConversionMarkup#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]

Örnek, <xref:System.Windows.Controls.TextBlock.Foreground%2A> uzantı sözdizimini kullanarak bir bağlama bildirerek özelliği bağlar. Özelliği için bağlama bildirimi <xref:System.Windows.Controls.TextBlock.Text%2A> nesne öğesi sözdizimini kullanır.

Farklı terimler hakkında daha fazla bilgi için bkz. [XAML sözdizimi ayrıntılı](../advanced/xaml-syntax-in-detail.md).

<a name="MBandPB"></a>

### <a name="multibinding-and-prioritybinding"></a>MultiBinding ve PriorityBinding

<xref:System.Windows.Data.MultiBinding>ve <xref:System.Windows.Data.PriorityBinding> xaml uzantısı söz dizimini desteklemez. Bu nedenle, <xref:System.Windows.Data.MultiBinding> XAML içinde bir veya bir olarak bildirmiyorsanız nesne öğesi sözdizimini kullanmanız gerekir <xref:System.Windows.Data.PriorityBinding> .

<a name="BindinginCode"></a>

## <a name="creating-a-binding-in-code"></a>Kod içinde bağlama oluşturma

Bir bağlama belirtmenin başka bir yolu da doğrudan kodda bir nesne üzerinde Özellikler ayarlamaya yönelik bir yoldur <xref:System.Windows.Data.Binding> . Aşağıdaki örnek, bir nesnesinin nasıl oluşturulduğunu <xref:System.Windows.Data.Binding> ve koddaki özelliklerin nasıl kullanılacağını gösterir.  Bu örnekte, `TheConverter` arabirimini uygulayan bir nesnedir <xref:System.Windows.Data.IValueConverter> .

[!code-csharp[BindConversion#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
[!code-vb[BindConversion#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]

Bağladığınız nesne bir veya ise, <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> `SetBinding` yöntemini kullanmak yerine doğrudan nesneniz üzerinde çağırabilirsiniz <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> . Bir örnek için bkz. [kodda bağlama oluşturma](how-to-create-a-binding-in-code.md).

<a name="Path_Syntax"></a>

## <a name="binding-path-syntax"></a>Bağlama yolu sözdizimi

Bağlamak istediğiniz <xref:System.Windows.Data.Binding.Path%2A> kaynak değeri belirtmek için özelliğini kullanın:

- En basit durumda, <xref:System.Windows.Data.Binding.Path%2A> özellik değeri, bağlama için kullanılacak kaynak nesnenin özelliğinin adıdır `Path=PropertyName` .

- Özelliğin alt özellikleri, C# ' de olduğu gibi benzer bir sözdizimi ile belirtilebilir. Örneğin, yan tümce `Path=ShoppingCart.Order` nesnenin veya özelliğin alt özelliğine bağlamayı ayarlar `Order` `ShoppingCart` .

- Ekli özelliğe bağlamak için iliştirilmiş özelliğin çevresine parantez koyun. Örneğin, ekli özelliğe bağlamak için <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> sözdizimi olur `Path=(DockPanel.Dock)` .

- Bir özelliğin Dizin oluşturucular, dizin oluşturucunun uygulandığı özellik adından sonra köşeli ayraç içinde belirtilebilir. Örnek olarak, yan tümce, `Path=ShoppingCart[0]` özelliğinin iç dizin oluşturma işleminin "0" değişmez dizesini nasıl işleyimine karşılık gelen dizine bağlamayı ayarlar. İç içe dizinleyiciler de desteklenir.

- Dizin oluşturucular ve alt özellikler yan tümce içinde karışık olabilir `Path` ; Örneğin,`Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`

- Dizin oluşturucular içinde, virgülle ayrılmış birden çok dizin oluşturucu parametresi olabilir (,). Her parametrenin türü parantez ile belirtilebilir. Örneğin, `Path="[(sys:Int32)42,(sys:Int32)24]"` `sys` ad alanıyla eşlenmiş olan ' yi kullanabilirsiniz `System` .

- Kaynak bir koleksiyon görünümü olduğunda, geçerli öğe eğik çizgiyle (/) belirtilebilir. Örneğin, yan tümce `Path=/` görünümdeki geçerli öğeye bağlamayı ayarlar. Kaynak bir koleksiyon olduğunda, bu söz dizimi varsayılan koleksiyon görünümünün geçerli öğesini belirtir.

- Özellik adları ve eğik çizgiler, Koleksiyonlar olan özellikleri çapraz gezmek için birleştirilebilir. Örneğin, `Path=/Offices/ManagerName` `Offices` aynı zamanda bir koleksiyon olan bir özelliği içeren kaynak koleksiyonun geçerli öğesini belirtir. Geçerli öğesi, özelliği içeren bir nesnedir `ManagerName` .

- İsteğe bağlı olarak, bir nokta (.) yolu geçerli kaynağa bağlamak için kullanılabilir. Örneğin, `Text="{Binding}"` öğesine eşdeğerdir `Text="{Binding Path=.}"` .

### <a name="escaping-mechanism"></a>Kaçış mekanizması

- Dizin oluşturucular ([]) içinde, giriş işareti karakteri (^) sonraki karakteri çıkar.

- <xref:System.Windows.Data.Binding.Path%2A>Xaml 'de ayarlarsanız, XML dil tanımına özel olan belirli karakterler de (xml varlıkları kullanarak) kaçış yapmanız gerekir:

  - `&amp;`"&" karakterini atlamak için kullanın.

  - `&gt;`">" bitiş etiketini atlamak için kullanın.

- Ayrıca, biçimlendirme uzantısı söz dizimini kullanarak bir öznitelikte tüm bağlamayı açıklamanız halinde, \\ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] biçimlendirme uzantısı ayrıştırıcısına özel olan (ters eğik çizgi kullanarak) karakterler kullanmanız gerekir:

  - Ters eğik çizgi ( \\ ), kaçış karakteridir.

  - Eşittir işareti (=) özellik değerinden özellik adını ayırır.

  - Virgül (,) özellikleri ayırır.

  - Sağ küme ayracı (}), biçimlendirme uzantısının sonu.

<a name="Default"></a>

## <a name="default-behaviors"></a>Varsayılan davranışlar

Bildirimde belirtilmemişse varsayılan davranış aşağıdaki gibidir.

- Bağlama kaynak değeri ile bağlama hedefi değeri arasında tür dönüştürmesi yapmaya çalışan bir varsayılan dönüştürücü oluşturulur. Bir dönüştürme yapılamaz, varsayılan dönüştürücü döndürür `null` .

- <xref:System.Windows.Data.Binding.ConverterCulture%2A>' I ayarlanmamışsa, bağlama altyapısı `Language` bağlama hedefi nesnesinin özelliğini kullanır. XAML 'de, bu varsayılan olarak "en-US" ya da bir değer açıkça ayarlandıysa, sayfanın kök öğesinden (veya herhangi bir öğeden) değeri devralır.

- Bağlama zaten bir veri bağlamına sahip olduğu sürece (örneğin, bir üst öğeden gelen devralınan veri bağlamı) ve bu bağlam tarafından döndürülen herhangi bir öğe veya koleksiyon, daha fazla yol değişikliği gerektirmeden bağlama için uygun olduğunda, bağlama bildiriminde hiçbir yan tümce bulunamaz: `{Binding}` Bu genellikle bağlamanın bir koleksiyon üzerinde çalıştığı, veri stili için bir bağlamanın belirtilme yoludur. Daha fazla bilgi için [bağlama kaynaklarına genel bakış](binding-sources-overview.md)konusunun "bağlama kaynağı olarak kullanılan tüm nesneler" bölümüne bakın.

- Varsayılan değer, <xref:System.Windows.Data.Binding.Mode%2A> bağlanmakta olan bağımlılık özelliğine bağlı olarak tek yönlü ve iki yönlü farklılık gösterir. Bağlamalarınızın istenen davranışa sahip olduğundan emin olmak için bağlama modunu her zaman açıkça bildirebilirsiniz. Genel olarak, ve gibi kullanıcı tarafından düzenlenebilir denetim özellikleri <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType> iki yönlü bağlamalara varsayılan olarak, diğer özelliklerin çoğu tek yönlü bağlamalara varsayılan olarak.

- Varsayılan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değer, <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> Bağımlı bağımlılık özelliğine de göre ve arasında değişir. Bağımlılık özelliklerinin çoğu için varsayılan değer <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> , <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> özelliğin varsayılan değeri olan ' dir <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> .

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
- [Veri Bağlama](../advanced/optimizing-performance-data-binding.md)
- [PropertyPath XAML Sözdizimi](../advanced/propertypath-xaml-syntax.md)
