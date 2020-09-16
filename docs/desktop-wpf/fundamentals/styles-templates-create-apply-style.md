---
title: Denetim için stil oluşturma
description: Windows Presentation Foundation ve .NET Core 'da bir denetim stili oluşturmayı ve başvuruyu yapmayı öğrenin.
author: adegeo
ms.author: adegeo
ms.date: 09/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: e1b1f75154431f61885d79db62b9ec289b69446e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555529"
---
# <a name="create-a-style-for-a-control-in-wpf"></a>WPF içindeki bir denetim için stil oluşturma

Windows Presentation Foundation (WPF) ile, var olan bir denetimin görünümünü kendi yeniden kullanılabilir stilinize göre özelleştirebilirsiniz. Stiller uygulamanıza, Windows ve sayfalarınıza Global olarak veya doğrudan denetimlere uygulanabilir.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="create-a-style"></a>Stil oluşturma

Bir <xref:System.Windows.Style> veya daha fazla öğeye özellik değerleri kümesi uygulamak için kullanışlı bir yol olarak düşünebilirsiniz. Ya da ' dan türetilen herhangi bir öğe için bir stil <xref:System.Windows.FrameworkElement> kullanabilirsiniz <xref:System.Windows.FrameworkContentElement> <xref:System.Windows.Window> <xref:System.Windows.Controls.Button> .

Bir stil belirtmenin en yaygın yolu, `Resources` BIR xaml dosyasındaki bölümünde kaynak olarak kullanılır. Stiller kaynaklar olduğundan, tüm kaynaklar için uygulanan aynı kapsam kurallarına uyar. Basitçe, stilin uygulanabileceğini bir stil bildirdiğiniz yere koyun. Örneğin, stili uygulama tanımı XAML dosyanızın kök öğesinde bildirirseniz, bu stil uygulamanızda herhangi bir yerde kullanılabilir.

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/App.xaml#AppResources)]

Stili uygulamanın XAML dosyalarından birinde bildirirseniz, stili yalnızca bu XAML dosyasında kullanılabilir. Kaynaklarla ilgili kapsam kuralları hakkında daha fazla bilgi için bkz. [xaml kaynakları](xaml-resources-define.md).

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowSingleResource.xaml#WindowResources)]

Stil, `<Setter>` stilin uygulandığı öğelerin özelliklerini ayarlama alt öğelerinden oluşur. Yukarıdaki örnekte, stilin `TextBlock` öznitelik aracılığıyla türlere uygulanacağını unutmayın `TargetType` . Stili, ve öğesini olarak <xref:System.Windows.Controls.Control.FontSize%2A> Ayarlar `15` <xref:System.Windows.Controls.Control.FontWeight%2A> `ExtraBold` . `<Setter>`Stilin değiştiği her bir özellik için bir ekleyin.

## <a name="apply-a-style-implicitly"></a>Stili örtülü olarak uygulama

<xref:System.Windows.Style>, Bir özellik değerleri kümesini birden fazla öğeye uygulamak için kullanışlı bir yoldur. Örneğin, aşağıdaki <xref:System.Windows.Controls.TextBlock> öğeleri ve bunların varsayılan görünümlerini bir pencerede düşünün.

[!code-xaml[TextBlocks](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetTextBlocks)]

![Stil örnek ekran görüntüsü](./media/styles-and-templates-overview/stylingintro-textblocksbefore.png "StylingIntro_TextBlocksBefore")

Her bir öğe için ve gibi özellikleri ayarlayarak varsayılan görünümü değiştirebilirsiniz <xref:System.Windows.Controls.Control.FontSize%2A> <xref:System.Windows.Controls.Control.FontFamily%2A> <xref:System.Windows.Controls.TextBlock> . Ancak, <xref:System.Windows.Controls.TextBlock> öğelerinizin bazı özellikler paylaşmasını istiyorsanız, <xref:System.Windows.Style> `Resources` burada gösterildiği gibi XAML dosyanızın bölümünde bir oluşturabilirsiniz.

[!code-xaml[DefaultTextBlockStyle](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetDefaultTextBlockStyle)]

<xref:System.Windows.Style.TargetType%2A>Tarzınıza ait stili ayarlayıp <xref:System.Windows.Controls.TextBlock> özniteliğini atlarsanız, stil, `x:Key` <xref:System.Windows.Controls.TextBlock> genellikle xaml dosyasının kendisi olan stilin kapsamına alınmış tüm öğelere uygulanır.

Artık <xref:System.Windows.Controls.TextBlock> öğeler şu şekilde görünür.

![Stil örnek ekran görüntüsü](./media/styles-and-templates-overview/stylingintro-textblocksbasestyle.png "StylingIntro_TextBlocksBaseStyle")

## <a name="apply-a-style-explicitly"></a>Stili açıkça uygulama

`x:Key`Stile değeri olan bir öznitelik eklerseniz, stil artık öğesinin tüm öğelerine örtük olarak uygulanmaz <xref:System.Windows.Style.TargetType%2A> . Yalnızca stile açıkça başvuran öğelere stil uygulanır.

Önceki bölümde yer aldığı, ancak özniteliğiyle belirtilen stil aşağıda verilmiştir `x:Key` .

[!code-xaml[ExplicitStyleDeclare](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleDeclare)]

Stili uygulamak için, <xref:System.Windows.FrameworkElement.Style%2A> `x:Key` burada gösterildiği gibi, bir [StaticResource biçimlendirme uzantısı](/dotnet/desktop/wpf/advanced/staticresource-markup-extension)kullanarak, öğesindeki özelliğini değerine ayarlayın.

[!code-xaml[ExplicitStyleReference](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleReference)]

<xref:System.Windows.Controls.TextBlock>Ikinci TextBlock öğesi değişmeden kaldığı sürece ilk öğenin stile uygulanmış olduğuna dikkat edin. Önceki bölümün örtülü stili özniteliği tanımlayan bir stile değiştirilmiştir `x:Key` , yani stili tarafından etkilenen tek öğe, stile doğrudan başvurmuş olan öğedir.

![Stil örnek ekran görüntüsü](./media/styles-and-templates-overview/create-a-style-explicit-textblock.png "-a-Style-Explicit-TextBlock oluştur")

Bir stil uygulandıktan sonra, açıkça veya örtük olarak, korumalı hale gelir ve değiştirilemez. Uygulanan bir stili değiştirmek istiyorsanız, varolan bir stili değiştirmek için yeni bir stil oluşturun. Daha fazla bilgi için bkz <xref:System.Windows.Style.IsSealed%2A> . özelliği.

Özel mantığa göre uygulanacak bir stil seçen bir nesne oluşturabilirsiniz. Bir örnek için, sınıfı için sunulan örneğe bakın <xref:System.Windows.Controls.StyleSelector> .

## <a name="apply-a-style-programmatically"></a>Program aracılığıyla stil uygulama

Programlı olarak adlandırılmış bir stil atamak için, kaynaklar koleksiyonundan stili alın ve öğenin <xref:System.Windows.FrameworkElement.Style%2A> özelliğine atayın. Bir kaynak koleksiyonundaki öğeler türündedir <xref:System.Object> . Bu nedenle, özelliğe atamadan önce alınan stili öğesine atamalısınız <xref:System.Windows.Style?displayProperty=fullName> `Style` . Örneğin, aşağıdaki kod `TextBlock` adlandırılmış stil olarak adlandırılan stilini ayarlar `textblock1` `TitleText` .

[!code-csharp[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml.cs#SnippetSetStyleCode)]
[!code-vb[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/MainWindow.xaml.vb#SnippetSetStyleCode)]

## <a name="extend-a-style"></a>Stili genişletme

Belki de iki öğelerinizin, <xref:System.Windows.Controls.TextBlock> ve ortalandı gibi bazı özellik değerlerini paylaşmasını isteyebilirsiniz <xref:System.Windows.Controls.Control.FontFamily%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> . Ancak **resimlerin Metinlerimin** bazı ek özelliklere sahip olmasını de istiyorsunuz. Bunu, burada gösterildiği gibi ilk stile göre yeni bir stil oluşturarak yapabilirsiniz.

[!code-xaml[DefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

[!code-xaml[TextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

Bu `TextBlock` Stil artık ortalandı, `Comic Sans MS` boyutu olan bir yazı tipi kullanır `26` ve örnekte gösterilen ön plan rengi <xref:System.Windows.Media.LinearGradientBrush> . Temel stilin değerini geçersiz kıldığını unutmayın <xref:System.Windows.Controls.Control.FontSize%2A> . <xref:System.Windows.Setter>' De aynı özelliğe işaret eden birden çok varsa <xref:System.Windows.Style> , `Setter` en son olarak belirtilen önceliği alır.

Aşağıda, <xref:System.Windows.Controls.TextBlock> öğelerin artık nasıl göründüğünü gösterilmektedir:

![Stilli Metinblokları](./media/styles-and-templates-overview/stylingintro-textblocks.png "StylingIntro_TextBlocks")

Bu `TitleText` Stil, ile başvurulan türü için oluşturulan stili genişletir <xref:System.Windows.Controls.TextBlock> `BasedOn="{StaticResource {x:Type TextBlock}}"` . Ayrıca, stili kullanarak bir stilini genişletebilirsiniz `x:Key` `x:Key` . Örneğin, adlı bir stil varsa `Header1` ve bu stili genişletmek istiyorsanız, kullanabilirsiniz `BasedOn="{StaticResource Header1}"` .

## <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>TargetType Özelliği ve x:Key özniteliği ilişkisi

Daha önce gösterildiği gibi, <xref:System.Windows.Style.TargetType%2A> stili atamadan özelliği olarak ayarlamak, `TextBlock` `x:Key` stilin tüm öğelere uygulanmasına neden olur <xref:System.Windows.Controls.TextBlock> . Bu durumda, örtülü olarak olarak `x:Key` ayarlanır `{x:Type TextBlock}` . Bu, değeri açıkça dışında bir şekilde ayarlarsanız `x:Key` `{x:Type TextBlock}` , <xref:System.Windows.Style> tüm `TextBlock` öğelerine otomatik olarak uygulanmadığını gösterir. Bunun yerine, stili `x:Key` açıkça öğeler için (değeri kullanılarak) uygulamanız gerekir `TextBlock` . Stiliniz kaynaklar bölümünde yer alıyorsa ve `TargetType` stilinize özelliği ayarlamazsanız, özniteliğini ayarlamanız gerekir `x:Key` .

Özelliği, için varsayılan bir değer sağlamaya ek olarak, `x:Key` `TargetType` ayarlayıcı özelliklerinin uygulanacağı türü belirtir. Bir belirtmezseniz `TargetType` , <xref:System.Windows.Setter> söz dizimini kullanarak nesnelerinizin özelliklerini bir sınıf adı ile nitelemeniz gerekir `Property="ClassName.Property"` . Örneğin, ayarı yerine `Property="FontSize"` <xref:System.Windows.Setter.Property%2A> veya olarak ayarlamanız gerekir `"TextBlock.FontSize"` `"Control.FontSize"` .

Ayrıca birçok WPF denetiminin diğer WPF denetimlerinin bir bileşiminden oluşur. Bir türün tüm denetimlerine uygulanan bir stil oluşturursanız, beklenmeyen sonuçlara sahip olabilirsiniz. Örneğin, bir içinde türü hedefleyen bir stil oluşturursanız, stili, gibi <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Window> başka bir `TextBlock` denetimin parçası olsa bile, penceredeki tüm denetimlere uygulanır `TextBlock` <xref:System.Windows.Controls.ListBox> .

## <a name="see-also"></a>Ayrıca bkz.

<!-- - [Create a style for a control](styles-templates-create-apply-template.md) -->
- [XAML kaynaklarına genel bakış](xaml-resources-define.md)
- [XAML 'ye Genel Bakış (WPF & .NET Core)](xaml.md)
