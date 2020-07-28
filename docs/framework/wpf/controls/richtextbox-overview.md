---
title: RichTextBox Genel Bakışı
description: Windows Presentation Foundation RichTextBox denetiminin, kullanıcıların metin, resim ve tablolar gibi içeriği görüntülemesine veya düzenlemesine nasıl olanak sağladığını öğrenin. Bkz. XAML ve C# örnekleri.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], RichTextBox
- RichTextBox control [WPF], about RichTextBox control
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
ms.openlocfilehash: 525e27f9602136c68f160c738fd1c92ea761536c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166233"
---
# <a name="richtextbox-overview"></a>RichTextBox Genel Bakışı

<xref:System.Windows.Controls.RichTextBox>Denetim, paragraflar, görüntüler, tablolar ve daha fazlasını içeren akış içeriğini görüntülemenizi veya düzenlemenizi sağlar. Bu konu sınıfı tanıtır <xref:System.Windows.Controls.TextBox> ve hem hem de C# içinde nasıl kullanılacağına ilişkin örnekler sağlar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .

<a name="textbox_or_richtextbox"></a>

## <a name="textbox-or-richtextbox"></a>TextBox veya RichTextBox?

<xref:System.Windows.Controls.RichTextBox> <xref:System.Windows.Controls.TextBox> Ancak, kullanıcıların metni düzenlemesine izin ver, ancak iki denetim farklı senaryolarda kullanılır. , <xref:System.Windows.Controls.RichTextBox> Kullanıcının biçimlendirilen metin, resim, tablo veya diğer zengin içerikleri düzenlemesi gerektiğinde daha iyi bir seçenektir. Örneğin, bir belge, makale veya blogın biçimlendirilmesi, resimler, vb. kullanarak en iyi şekilde yapılması önerilir <xref:System.Windows.Controls.RichTextBox> . <xref:System.Windows.Controls.TextBox>, Daha az sistem kaynağı gerektirir <xref:System.Windows.Controls.RichTextBox> ve yalnızca düz metin düzenlenmesi gerektiğinde (örneğin, formlarda kullanım) idealdir. Hakkında daha fazla bilgi için bkz. [TextBox Overview](textbox-overview.md) <xref:System.Windows.Controls.TextBox> . Aşağıdaki tabloda ve öğesinin ana özellikleri özetlenmektedir <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> .

|Denetim|Gerçek zamanlı yazım denetimi|Bağlam Menüsü|Gibi biçimlendirme komutları <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Ctrl + B)|<xref:System.Windows.Documents.FlowDocument>görüntüler, paragraflar, tablolar vb. içerikler|
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|<xref:System.Windows.Controls.TextBox>|Yes|Evet|Hayır|Hayır.|
|<xref:System.Windows.Controls.RichTextBox>|Yes|Yes|Yes|Yes|

> [!NOTE]
> <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Ctrl + B) gibi ilgili komutların biçimlendirilmesini desteklemez, ancak birçok temel komut gibi her iki denetim de desteklenir <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A> .

Yukarıdaki tablodaki özellikler daha sonra daha ayrıntılı bir şekilde ele alınmıştır.

<a name="creating_a_richtextbox"></a>

## <a name="creating-a-richtextbox"></a>RichTextBox oluşturma

Aşağıdaki kod, bir <xref:System.Windows.Controls.RichTextBox> kullanıcının ' de zengin içeriği düzenleyebilmesi için nasıl oluşturulacağını gösterir.

[!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]

Özellikle, öğesinde düzenlenen içerik <xref:System.Windows.Controls.RichTextBox> akış içeridir. Akış içeriği, biçimlendirilen metin, görüntüler, listeler ve tablolar gibi birçok tür öğe içerebilir. Akış belgeleriyle ilgili ayrıntılı bilgi için bkz. [akış belgesine genel bakış](../advanced/flow-document-overview.md) . Akış içeriğini içermek için, bir nesnesi, <xref:System.Windows.Controls.RichTextBox> <xref:System.Windows.Documents.FlowDocument> düzenlenebilir içeriği içeren bir nesne barındırır. İçindeki akış içeriğini göstermek için <xref:System.Windows.Controls.RichTextBox> Aşağıdaki kod, bir <xref:System.Windows.Controls.RichTextBox> paragraf ve bazı kalın metin içeren bir oluşturma gösterir.

[!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]

[!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
[!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]

Aşağıdaki çizim, bu örneğin nasıl işlediğini gösterir.

![İçerikle RichTextBox](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")

Gibi öğeler <xref:System.Windows.Documents.Paragraph> ve <xref:System.Windows.Documents.Bold> içindeki içeriğin nasıl <xref:System.Windows.Controls.RichTextBox> göründüğünü belirleme. Kullanıcı <xref:System.Windows.Controls.RichTextBox> içerik düzenlediklerinde bu akış içeriğini değiştirir. Akış içeriğinin özellikleri ve bununla nasıl çalışılacağı hakkında daha fazla bilgi edinmek için bkz. [Flow belgesine genel bakış](../advanced/flow-document-overview.md).

> [!NOTE]
> A içindeki akış içeriği <xref:System.Windows.Controls.RichTextBox> , diğer denetimlerde yer alan akış içeriği gibi davranır. Örneğin, içinde hiç sütun yok <xref:System.Windows.Controls.RichTextBox> ve bu nedenle otomatik yeniden boyutlandırma davranışı yok. Ayrıca, arama, görüntüleme modu, sayfa gezintisi ve yakınlaştırma gibi yerleşik özellikler bir içinde kullanılamaz <xref:System.Windows.Controls.RichTextBox> .

<a name="realtime_spellechecking"></a>

## <a name="real-time-spell-checking"></a>Gerçek zamanlı yazım denetimi

Veya ' de gerçek zamanlı yazım denetimini etkinleştirebilirsiniz <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> . Yazım denetimi açık olduğunda, yanlış yazılmış sözcüklerin altında kırmızı bir çizgi görünür (aşağıdaki resme bakın).

![Yazım&#45;denetimi içeren metin kutusu](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")

Yazım denetimini nasıl etkinleştireceğinizi öğrenmek için bkz. [metin düzenlemede yazım denetimini etkinleştirme](how-to-enable-spell-checking-in-a-text-editing-control.md) .

<a name="context_menu"></a>

## <a name="context-menu"></a>Bağlam Menüsü

Varsayılan olarak, her ikisi de <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> bir kullanıcı denetimin içine sağ tıkladığında görüntülenen bir bağlam menüsüne sahiptir. Bağlam menüsü, kullanıcının kesmesine, kopyalamasına veya yapıştırmaya izin verir (aşağıdaki çizime bakın).

![Bağlam menüsü olan TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")

Varsayılan olanı geçersiz kılmak için kendi özel bağlam menünüzün oluşturulmasını sağlayabilirsiniz. Daha fazla bilgi için bkz. [RichTextBox Içinde özel bağlam menüsü konumlandırma](how-to-position-a-custom-context-menu-in-a-richtextbox.md) .

<a name="detect_when_content_changes"></a>

## <a name="editing-commands"></a>Komutları Düzenle

Komutları düzenleme, kullanıcıların bir içindeki düzenlenebilir içeriği biçimlendirmesinin mümkün olduğunu sağlar <xref:System.Windows.Controls.RichTextBox> . Temel düzenlemenin yanı sıra, desteklenmeyen <xref:System.Windows.Controls.RichTextBox> biçimlendirme komutlarını içerir <xref:System.Windows.Controls.TextBox> . Örneğin, bir üzerinde düzenlenirken, bir <xref:System.Windows.Controls.RichTextBox> Kullanıcı, kalın metin biçimlendirmesini değiştirmek Için CTRL + B tuşlarına basabilir. <xref:System.Windows.Documents.EditingCommands>Kullanılabilir komutların tüm listesi için bkz.. Klavye kısayollarını kullanmanın yanı sıra komutları düğmeler gibi diğer denetimlere de bağlayabilirsiniz. Aşağıdaki örnek, kullanıcının metin biçimlendirmesini değiştirmek için kullanabileceği düğmeleri içeren basit bir araç çubuğunun nasıl oluşturulacağını gösterir.

[!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]

Aşağıdaki çizimde bu örneğin nasıl görüntülediği gösterilmektedir.

![Araç çubuğuyla RichTextBox](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")

<a name="editing_commands"></a>

## <a name="detect-when-content-changes"></a>Içeriğin ne zaman değiştiğini Algıla

Genellikle <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay, ne zaman bir <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.RichTextBox> daha sonra beklendiğini tahmin edebileceğiniz gibi tespit etmek için kullanılmalıdır <xref:System.Windows.UIElement.KeyDown> . Örnek [olarak bir metin kutusundaki metnin değiştiğini Algıla](how-to-detect-when-text-in-a-textbox-has-changed.md) bölümüne bakın.

<a name="save_load_and_print_richtextbox_content"></a>

## <a name="save-load-and-print-richtextbox-content"></a>RichTextBox İçeriğini Kaydetme, Yükleme ve Yazdırma

Aşağıdaki örnek, bir dosyasının içeriğinin bir dosyaya nasıl kaydedileceğini <xref:System.Windows.Controls.RichTextBox> , bu içeriğin tekrar tekrar yükleneceğini ve içeriğin nasıl <xref:System.Windows.Controls.RichTextBox> yazdırılacağını gösterir. Örnek için biçimlendirme aşağıda verilmiştir.

[!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]

Örnek için arka plan kodu aşağıda verilmiştir.

[!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
[!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır Konuları](richtextbox-how-to-topics.md)
- [TextBox Genel Bakışı](textbox-overview.md)
