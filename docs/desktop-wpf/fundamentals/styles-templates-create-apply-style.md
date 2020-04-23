---
title: Denetim için stil oluşturma
description: Windows Presentation Foundation ve .NET Core 'da bir denetim stili oluşturmayı ve başvuruyu yapmayı öğrenin.
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
# <a name="create-a-style-for-a-control-in-wpf"></a>WPF içindeki bir denetim için stil oluşturma

Windows Presentation Foundation (WPF) ile, var olan bir denetimin görünümünü kendi yeniden kullanılabilir stilinize göre özelleştirebilirsiniz. Stiller uygulamanıza, Windows ve sayfalarınıza Global olarak veya doğrudan denetimlere uygulanabilir.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="create-a-style"></a>Stil oluşturma

Bir veya daha fazla öğeye <xref:System.Windows.Style> özellik değerleri kümesi uygulamak için kullanışlı bir yol olarak düşünebilirsiniz. Ya <xref:System.Windows.FrameworkElement> da ' dan <xref:System.Windows.FrameworkContentElement> türetilen herhangi bir <xref:System.Windows.Window> öğe için bir stil kullanabilirsiniz. <xref:System.Windows.Controls.Button>

Bir stil belirtmenin en yaygın yolu, bir XAML dosyasındaki `Resources` bölümünde kaynak olarak kullanılır. Stiller kaynaklar olduğundan, tüm kaynaklar için uygulanan aynı kapsam kurallarına uyar. Basitçe, stilin uygulanabileceğini bir stil bildirdiğiniz yere koyun. Örneğin, stili uygulama tanımı XAML dosyanızın kök öğesinde bildirirseniz, bu stil uygulamanızda herhangi bir yerde kullanılabilir.

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/App.xaml#AppResources)]

Stili uygulamanın XAML dosyalarından birinde bildirirseniz, stili yalnızca bu XAML dosyasında kullanılabilir. Kaynaklarla ilgili kapsam kuralları hakkında daha fazla bilgi için bkz. [xaml kaynakları](xaml-resources-define.md).

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowSingleResource.xaml#WindowResources)]

Stil, stilin uygulandığı öğelerin özelliklerini `<Setter>` ayarlama alt öğelerinden oluşur. Yukarıdaki örnekte, stilin `TextBlock` `TargetType` öznitelik aracılığıyla türlere uygulanacağını unutmayın. <xref:System.Windows.Controls.Control.FontSize%2A> Stili, `15` ve <xref:System.Windows.Controls.Control.FontWeight%2A> öğesini olarak ayarlar. `ExtraBold` Stilin değiştiği `<Setter>` her bir özellik için bir ekleyin.

## <a name="apply-a-style-implicitly"></a>Stili örtülü olarak uygulama

<xref:System.Windows.Style> , Bir özellik değerleri kümesini birden fazla öğeye uygulamak için kullanışlı bir yoldur. Örneğin, aşağıdaki <xref:System.Windows.Controls.TextBlock> öğeleri ve bunların varsayılan görünümlerini bir pencerede düşünün.

[!code-xaml[TextBlocks](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetTextBlocks)]

![Stil örnek ekran görüntüsü](./media/styles-and-templates-overview/stylingintro-textblocksbefore.png "StylingIntro_TextBlocksBefore")

Her <xref:System.Windows.Controls.Control.FontSize%2A> <xref:System.Windows.Controls.TextBlock> bir öğe için ve <xref:System.Windows.Controls.Control.FontFamily%2A>gibi özellikleri ayarlayarak varsayılan görünümü değiştirebilirsiniz. Ancak, <xref:System.Windows.Controls.TextBlock> öğelerinizin bazı özellikler paylaşmasını istiyorsanız, burada GÖSTERILDIĞI gibi XAML dosyanızın <xref:System.Windows.Style> `Resources` bölümünde bir oluşturabilirsiniz.

[!code-xaml[DefaultTextBlockStyle](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetDefaultTextBlockStyle)]

Tarzınıza <xref:System.Windows.Style.TargetType%2A> ait stili <xref:System.Windows.Controls.TextBlock> ayarlayıp `x:Key` ÖZNITELIĞINI atlarsanız, stil, genellikle xaml dosyasının kendisi olan stilin kapsamına alınmış tüm <xref:System.Windows.Controls.TextBlock> öğelere uygulanır.

Artık <xref:System.Windows.Controls.TextBlock> öğeler şu şekilde görünür.

![Stil örnek ekran görüntüsü](./media/styles-and-templates-overview/stylingintro-textblocksbasestyle.png "StylingIntro_TextBlocksBaseStyle")

## <a name="apply-a-style-explicitly"></a>Stili açıkça uygulama

Stile değeri olan bir `x:Key` öznitelik eklerseniz, stil artık öğesinin <xref:System.Windows.Style.TargetType%2A>tüm öğelerine örtük olarak uygulanmaz. Yalnızca stile açıkça başvuran öğelere stil uygulanır.

Önceki bölümde yer aldığı, ancak `x:Key` özniteliğiyle belirtilen stil aşağıda verilmiştir.

[!code-xaml[ExplicitStyleDeclare](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleDeclare)]

Stili uygulamak için, burada gösterildiği gibi <xref:System.Windows.FrameworkElement.Style%2A> , bir [StaticResource biçimlendirme uzantısı](../../framework/wpf/advanced/staticresource-markup-extension.md)kullanarak `x:Key` , öğesindeki özelliğini değerine ayarlayın.

[!code-xaml[ExplicitStyleReference](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleReference)]

İkinci TextBlock öğesi değişmeden <xref:System.Windows.Controls.TextBlock> kaldığı sürece ilk öğenin stile uygulanmış olduğuna dikkat edin. Önceki bölümün örtülü stili `x:Key` özniteliği tanımlayan bir stile değiştirilmiştir, yani stili tarafından etkilenen tek öğe, stile doğrudan başvurmuş olan öğedir.

![Stil örnek ekran görüntüsü](./media/styles-and-templates-overview/create-a-style-explicit-textblock.png "-a-Style-Explicit-TextBlock oluştur")

Bir stil uygulandıktan sonra, açıkça veya örtük olarak, korumalı hale gelir ve değiştirilemez. Uygulanan bir stili değiştirmek istiyorsanız, varolan bir stili değiştirmek için yeni bir stil oluşturun. Daha fazla bilgi için bkz. <xref:System.Windows.Style.IsSealed%2A> özelliği.

Özel mantığa göre uygulanacak bir stil seçen bir nesne oluşturabilirsiniz. Bir örnek için, <xref:System.Windows.Controls.StyleSelector> sınıfı için sunulan örneğe bakın.

## <a name="apply-a-style-programmatically"></a>Program aracılığıyla stil uygulama

Programlı olarak adlandırılmış bir stil atamak için, kaynaklar koleksiyonundan stili alın ve öğenin <xref:System.Windows.FrameworkElement.Style%2A> özelliğine atayın. Bir kaynak koleksiyonundaki öğeler türündedir <xref:System.Object>. Bu nedenle, <xref:System.Windows.Style?displayProperty=fullName> `Style` özelliğe atamadan önce alınan stili öğesine atamalısınız. Örneğin, aşağıdaki kod `TextBlock` adlandırılmış stil olarak adlandırılan `textblock1` stilini ayarlar. `TitleText`

[!code-csharp[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml.cs#SnippetSetStyleCode)]
[!code-vb[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/MainWindow.xaml.vb#SnippetSetStyleCode)]

## <a name="extend-a-style"></a>Stili genişletme

Belki de iki <xref:System.Windows.Controls.TextBlock> öğelerinizin, <xref:System.Windows.Controls.Control.FontFamily%2A> ve ortalandı <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>gibi bazı özellik değerlerini paylaşmasını isteyebilirsiniz. Ancak **resimlerin Metinlerimin** bazı ek özelliklere sahip olmasını de istiyorsunuz. Bunu, burada gösterildiği gibi ilk stile göre yeni bir stil oluşturarak yapabilirsiniz.

[!code-xaml[DefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

[!code-xaml[TextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

Bu `TextBlock` stil artık ortalandı, boyutu `Comic Sans MS` `26`olan bir yazı tipi kullanır ve örnekte <xref:System.Windows.Media.LinearGradientBrush> gösterilen ön plan rengi. Temel stilin <xref:System.Windows.Controls.Control.FontSize%2A> değerini geçersiz kıldığını unutmayın. ' De aynı özelliğe <xref:System.Windows.Setter> işaret eden birden çok varsa, `Setter` en son olarak belirtilen önceliği alır. <xref:System.Windows.Style>

Aşağıda, <xref:System.Windows.Controls.TextBlock> öğelerin artık nasıl göründüğünü gösterilmektedir:

![Stilli Metinblokları](./media/styles-and-templates-overview/stylingintro-textblocks.png "StylingIntro_TextBlocks")

Bu `TitleText` stil, ile <xref:System.Windows.Controls.TextBlock> `BasedOn="{StaticResource {x:Type TextBlock}}"`başvurulan türü için oluşturulan stili genişletir. Ayrıca, stili kullanarak `x:Key` `x:Key` bir stilini genişletebilirsiniz. Örneğin, adlı `Header1` bir stil varsa ve bu stili genişletmek istiyorsanız, kullanabilirsiniz `BasedOn="{StaticResource Header1}"`.

## <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>TargetType Özelliği ve x:Key özniteliği ilişkisi

Daha önce gösterildiği gibi, stili <xref:System.Windows.Style.TargetType%2A> atamadan özelliği `TextBlock` olarak ayarlamak, stilin tüm `x:Key` <xref:System.Windows.Controls.TextBlock> öğelere uygulanmasına neden olur. Bu durumda `x:Key` , örtülü olarak olarak ayarlanır `{x:Type TextBlock}`. Bu, `x:Key` değeri açıkça dışında `{x:Type TextBlock}`bir şekilde ayarlarsanız, <xref:System.Windows.Style> tüm `TextBlock` öğelerine otomatik olarak uygulanmadığını gösterir. Bunun yerine, stili açıkça `x:Key` `TextBlock` öğeler için (değeri kullanılarak) uygulamanız gerekir. Stiliniz kaynaklar bölümünde yer alıyorsa ve stilinize `TargetType` özelliği ayarlamazsanız, `x:Key` özniteliğini ayarlamanız gerekir.

`TargetType` Özelliği, `x:Key`için varsayılan bir değer sağlamaya ek olarak, ayarlayıcı özelliklerinin uygulanacağı türü belirtir. Bir `TargetType`belirtmezseniz, söz dizimini <xref:System.Windows.Setter> `Property="ClassName.Property"`kullanarak nesnelerinizin özelliklerini bir sınıf adı ile nitelemeniz gerekir. `Property="FontSize"`Örneğin, ayarı yerine <xref:System.Windows.Setter.Property%2A> veya `"TextBlock.FontSize"` `"Control.FontSize"`olarak ayarlamanız gerekir.

Ayrıca birçok WPF denetiminin diğer WPF denetimlerinin bir bileşiminden oluşur. Bir türün tüm denetimlerine uygulanan bir stil oluşturursanız, beklenmeyen sonuçlara sahip olabilirsiniz. Örneğin <xref:System.Windows.Controls.TextBlock> , bir <xref:System.Windows.Window>içinde türü hedefleyen bir stil oluşturursanız, stili, gibi başka bir denetimin parçası olsa `TextBlock` bile `TextBlock` , penceredeki tüm denetimlere uygulanır. <xref:System.Windows.Controls.ListBox>

## <a name="see-also"></a>Ayrıca bkz.

<!-- - [Create a style for a control](styles-templates-create-apply-template.md) -->
- [XAML kaynaklarına genel bakış](xaml-resources-define.md)
- [XAML 'ye Genel Bakış (WPF & .NET Core)](xaml.md)
