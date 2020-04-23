---
title: Denetim için stil oluşturma
description: Windows Presentation Foundation ve .NET Core'da bir denetim stili oluşturmayı ve nasıl başvururduk öğrenin.
author: thraka
ms.author: adegeo
ms.date: 09/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2956dbf93a1d34feca31d3ab10536f5089010189
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "82071271"
---
# <a name="create-a-style-for-a-control-in-wpf"></a>WPF'de denetim için stil oluşturma

Windows Sunu Temeli (WPF) ile varolan bir denetimin görünümünü kendi yeniden kullanılabilir stiliniz ile özelleştirebilirsiniz. Stiller, uygulamanız, pencereler ve sayfalarınız için genel olarak veya doğrudan denetimlere uygulanabilir.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="create-a-style"></a>Stil oluşturma

Bir <xref:System.Windows.Style> veya daha fazla öğeye özellik değerleri kümesi uygulamak için uygun bir yol olarak düşünebilirsiniz. Bir stil, <xref:System.Windows.FrameworkElement> bir öğeden türeyen <xref:System.Windows.FrameworkContentElement> veya bir <xref:System.Windows.Window> öğe <xref:System.Windows.Controls.Button>den türeyen herhangi bir öğe üzerinde kullanabilirsiniz.

Bir stili bildirmenin en yaygın yolu, `Resources` XAML dosyasındaki bölümdekaynak olarak dır. Stiller kaynak olduğundan, tüm kaynaklar için geçerli olan aynı kapsam kurallarına uyarlar. Basitçe söylemek gerekirse, bir stili beyan ettiğiniz yer stilin uygulanabileceği yeri etkiler. Örneğin, uygulama tanımı XAML dosyanızın kök öğesindeki stili bildirirseniz, stil uygulamanızın herhangi bir yerinde kullanılabilir.

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/App.xaml#AppResources)]

Stili uygulamanın XAML dosyalarından birinde bildirirseniz, stil yalnızca bu XAML dosyasında kullanılabilir. Kaynaklar için kapsam kuralları hakkında daha fazla bilgi için [XAML Kaynakları'na](xaml-resources-define.md)bakın.

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowSingleResource.xaml#WindowResources)]

Stil, stilin `<Setter>` uygulandığı öğeler üzerinde özellikleri ayarlayan alt öğelerden oluşur. Yukarıdaki örnekte, stilöz öznitelik üzerinden `TextBlock` `TargetType` türleri uygulamak için ayarlanmış tır. Stil <xref:System.Windows.Controls.Control.FontSize%2A> ve `15` <xref:System.Windows.Controls.Control.FontWeight%2A> ayarlayacaktır `ExtraBold`. Stil `<Setter>` değişiklikleri her özellik için a ekleyin.

## <a name="apply-a-style-implicitly"></a>Bir stili zımni olarak uygulama

A, <xref:System.Windows.Style> birden fazla öğeye özellik değerleri kümesi uygulamak için kullanışlı bir yoldur. Örneğin, aşağıdaki <xref:System.Windows.Controls.TextBlock> öğeleri ve bir penceredeki varsayılan görünümlerini göz önünde bulundurun.

[!code-xaml[TextBlocks](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetTextBlocks)]

![Stil örnek ekran görüntüsü](./media/styles-and-templates-overview/stylingintro-textblocksbefore.png "StylingIntro_TextBlocksBefore")

Her <xref:System.Windows.Controls.Control.FontSize%2A> <xref:System.Windows.Controls.TextBlock> öğeüzerinde doğrudan gibi ve <xref:System.Windows.Controls.Control.FontFamily%2A>, özellikleri ayarlayarak varsayılan görünümü değiştirebilirsiniz. Ancak, öğelerinizin <xref:System.Windows.Controls.TextBlock> bazı özellikleri paylaşmasını istiyorsanız, <xref:System.Windows.Style> XAML dosyanızın `Resources` bölümünde burada gösterildiği gibi bir öğe oluşturabilirsiniz.

[!code-xaml[DefaultTextBlockStyle](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetDefaultTextBlockStyle)]

<xref:System.Windows.Style.TargetType%2A> <xref:System.Windows.Controls.TextBlock> Stilinizin türünü ayarladığınızda ve `x:Key` özniteliği atladığınızda, stil genellikle XAML dosyasının kendisi olan stilkapsamına giren tüm <xref:System.Windows.Controls.TextBlock> öğelere uygulanır.

Şimdi <xref:System.Windows.Controls.TextBlock> öğeler aşağıdaki gibi görünür.

![Stil örnek ekran görüntüsü](./media/styles-and-templates-overview/stylingintro-textblocksbasestyle.png "StylingIntro_TextBlocksBaseStyle")

## <a name="apply-a-style-explicitly"></a>Bir stili açıkça uygulama

Stildeğeri olan `x:Key` bir öznitelik eklerseniz, stil artık tüm öğelere örtülü <xref:System.Windows.Style.TargetType%2A>olarak uygulanmaz. Yalnızca stili açıkça başvuran öğeler, stilin kendilerine uygulanmasını sağlar.

Burada önceki bölümden stil, ancak öznitelik ile `x:Key` ilan edilir.

[!code-xaml[ExplicitStyleDeclare](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleDeclare)]

Stili uygulamak için, <xref:System.Windows.FrameworkElement.Style%2A> burada gösterildiği gibi `x:Key` Statik Kaynak [biçimlendirme uzantısını](../../framework/wpf/advanced/staticresource-markup-extension.md)kullanarak öğedeki özelliği değere ayarlayın.

[!code-xaml[ExplicitStyleReference](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleReference)]

İkinci TextBlock <xref:System.Windows.Controls.TextBlock> öğesi değişmeden kalırken, ilk öğenin stiluygulandığına dikkat edin. Önceki bölümdeki örtük stil özniteliği, anlamı, stilden etkilenen tek öğe stili doğrudan başvuran öğeyi bildiren `x:Key` bir stil olarak değiştirildi.

![Stil örnek ekran görüntüsü](./media/styles-and-templates-overview/create-a-style-explicit-textblock.png "oluşturma-a-stil-açık-metin bloğu")

Bir stil açık veya örtülü olarak uygulandıktan sonra mühürlenir ve değiştirilemez. Uygulanan bir stili değiştirmek istiyorsanız, varolan stili değiştirmek için yeni bir stil oluşturun. Daha fazla bilgi <xref:System.Windows.Style.IsSealed%2A> için tesise bakın.

Özel mantığa göre uygulanacak bir stil seçen bir nesne oluşturabilirsiniz. Örneğin, <xref:System.Windows.Controls.StyleSelector> sınıf için sağlanan örneğe bakın.

## <a name="apply-a-style-programmatically"></a>Stili programlı olarak uygulama

Adlandırılmış bir stili bir öğeye programlı olarak atamak için, kaynakları koleksiyonundan stili <xref:System.Windows.FrameworkElement.Style%2A> alın ve öğenin özelliğine atayın. Kaynak koleksiyonundaki öğeler türündedir. <xref:System.Object> Bu nedenle, alınan stili <xref:System.Windows.Style?displayProperty=fullName> `Style` özelliğe atamadan önce bir eve atamalısınız. Örneğin, aşağıdaki kod tanımlanan stiliçin `TextBlock` `TitleText` `textblock1` adlandırılmış stili ayarlar.

[!code-csharp[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml.cs#SnippetSetStyleCode)]
[!code-vb[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/MainWindow.xaml.vb#SnippetSetStyleCode)]

## <a name="extend-a-style"></a>Stili genişletme

Belki de iki <xref:System.Windows.Controls.TextBlock> öğenizin, ortalanmış <xref:System.Windows.Controls.Control.FontFamily%2A> ve ortalanmış <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>gibi bazı özellik değerlerini paylaşmasını istersiniz. Ancak, **Resimlerim** metninin bazı ek özelliklere sahip olmasını da istersiniz. Burada gösterildiği gibi, ilk stili temel alan yeni bir stil oluşturarak bunu yapabilirsiniz.

[!code-xaml[DefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

[!code-xaml[TextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

Bu `TextBlock` stil artık ortalanır, `Comic Sans MS` boyutu olan `26`bir yazı tipi kullanır , <xref:System.Windows.Media.LinearGradientBrush> ve örnekte gösterilen ön plan renk kümesi. Temel stilin <xref:System.Windows.Controls.Control.FontSize%2A> değerini geçersiz kındığını unutmayın. Aynı özelliği işaret eden <xref:System.Windows.Setter> birden fazla özellik <xref:System.Windows.Style>varsa, `Setter` en son bildirilen önceki özelliktir.

Aşağıdaki öğelerin <xref:System.Windows.Controls.TextBlock> şimdi nasıl göründüğünü gösterir:

![Stilli TextBlocks](./media/styles-and-templates-overview/stylingintro-textblocks.png "StylingIntro_TextBlocks")

Bu `TitleText` stil, <xref:System.Windows.Controls.TextBlock> türü için oluşturulan stili genişletir, `BasedOn="{StaticResource {x:Type TextBlock}}"`ile başvurulan. Ayrıca, stili kullanarak `x:Key` `x:Key` bir stili genişletebilirsiniz. Örneğin, adlı `Header1` bir stil varsa ve bu stili genişletmek istiyorsanız, bunu kullanırsınız. `BasedOn="{StaticResource Header1}"`

## <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>TargetType özelliğinin ilişkisi ve x:Anahtar özniteliği

Daha önce gösterildiği gibi, <xref:System.Windows.Style.TargetType%2A> `TextBlock` özelliği stili atamadan `x:Key` ayarlamak stilin tüm <xref:System.Windows.Controls.TextBlock> öğelere uygulanmasına neden olur. Bu durumda, `x:Key` örtülü olarak `{x:Type TextBlock}`ayarlanır. Bu, `x:Key` değeri açıkça başka bir şeye `{x:Type TextBlock}`ayarlarsanız, <xref:System.Windows.Style> tüm `TextBlock` öğelere otomatik olarak uygulanmaz anlamına gelir. Bunun yerine, stili `x:Key` (değeri kullanarak) `TextBlock` öğelere açıkça uygulamanız gerekir. Stiliniz kaynaklar bölümündeyse ve `TargetType` özelliği stilinize göre ayarlamadıysanız, `x:Key` özniteliği ayarlamanız gerekir.

Için varsayılan bir değer sağlamanın `x:Key` `TargetType` yanı sıra, özellik ayarlayıcı özelliklerinin uygulandığı türü belirtir. Bir `TargetType`, sözdizimini <xref:System.Windows.Setter> `Property="ClassName.Property"`kullanarak nesnelerinizdeki özellikleri sınıf adı ile nitelemelisiniz. Örneğin, `Property="FontSize"`ayar yerine, ayarlamanız <xref:System.Windows.Setter.Property%2A> `"TextBlock.FontSize"` gerekir `"Control.FontSize"`veya .

Ayrıca, birçok WPF denetiminin diğer WPF denetimlerinin bir birleşiminden oluştuğunu unutmayın. Bir türün tüm denetimleri için geçerli olan bir stil oluşturursanız, beklenmeyen sonuçlar elde edebilirsiniz. Örneğin, bir tür <xref:System.Windows.Controls.TextBlock> hedefleyen bir <xref:System.Windows.Window>stil oluşturursanız , stil penceredeki tüm `TextBlock` denetimlere uygulanır, başka bir denetimin parçası olsa `TextBlock` bile, bir <xref:System.Windows.Controls.ListBox>.

## <a name="see-also"></a>Ayrıca bkz.

<!-- - [Create a style for a control](styles-templates-create-apply-template.md) -->
- [XAML Kaynaklarına Genel Bakış](xaml-resources-define.md)
- [XAML'ye genel bakış (WPF & .NET Core)](xaml.md)
