---
title: RichTextBox Genel Bakışı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], RichTextBox
- RichTextBox control [WPF], about RichTextBox control
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
ms.openlocfilehash: bfed42bcf3693ef744b3ed2b54ebe070931513a9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855740"
---
# <a name="richtextbox-overview"></a>RichTextBox Genel Bakışı

<xref:System.Windows.Controls.RichTextBox> Denetim, paragraflar, görüntüler, tablolar ve daha fazlasını içeren akış içeriğini görüntülemenizi veya düzenlemenizi sağlar. Bu konu <xref:System.Windows.Controls.TextBox> sınıfı tanıtır ve hem [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] hem de içinde nasıl kullanılacağına ilişkin örnekler sağlar. C#

<a name="textbox_or_richtextbox"></a>

## <a name="textbox-or-richtextbox"></a>TextBox veya RichTextBox?

Ancak,kullanıcılarınmetnidüzenlemesineizinver,ancakikidenetimfarklısenaryolardakullanılır.<xref:System.Windows.Controls.RichTextBox> <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> , Kullanıcının biçimlendirilen metin, resim, tablo veya diğer zengin içerikleri düzenlemesi gerektiğinde daha iyi bir seçenektir. Örneğin, bir <xref:System.Windows.Controls.RichTextBox>belge, makale veya blogın biçimlendirilmesi, resimler, vb. kullanarak en iyi şekilde yapılması önerilir. , Daha az sistem kaynağı <xref:System.Windows.Controls.TextBox> gerektirir ve yalnızca düz metin düzenlenmesi gerektiğinde (örneğin, formlarda kullanım <xref:System.Windows.Controls.RichTextBox> ) idealdir. Hakkında<xref:System.Windows.Controls.TextBox>daha fazla bilgi Için bkz. [TextBox Overview](textbox-overview.md) . Aşağıdaki tabloda ve <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox>öğesinin ana özellikleri özetlenmektedir.

|Denetim|Gerçek zamanlı yazım denetimi|Bağlam Menüsü|Gibi <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> biçimlendirme komutları (Ctrl + B)|<xref:System.Windows.Documents.FlowDocument>görüntüler, paragraflar, tablolar vb. içerikler|
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|<xref:System.Windows.Controls.TextBox>|Evet|Evet|Hayır|Hayır.|
|<xref:System.Windows.Controls.RichTextBox>|Evet|Evet|Evet|Evet|

> [!NOTE]
> ( <xref:System.Windows.Controls.TextBox> CTRL + B) gibi <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> ilgili komutların biçimlendirilmesini desteklemez, ancak birçok temel komut gibi <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>her iki denetim de desteklenir.

Yukarıdaki tablodaki özellikler daha sonra daha ayrıntılı bir şekilde ele alınmıştır.

<a name="creating_a_richtextbox"></a>

## <a name="creating-a-richtextbox"></a>RichTextBox oluşturma

Aşağıdaki kod, bir kullanıcının ' de zengin <xref:System.Windows.Controls.RichTextBox> içeriği düzenleyebilmesi için nasıl oluşturulacağını gösterir.

[!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]

Özellikle, öğesinde <xref:System.Windows.Controls.RichTextBox> düzenlenen içerik akış içeridir. Akış içeriği, biçimlendirilen metin, görüntüler, listeler ve tablolar gibi birçok tür öğe içerebilir. Akış belgeleriyle ilgili ayrıntılı bilgi için bkz. [akış belgesine genel bakış](../advanced/flow-document-overview.md) . Akış içeriğini içermek için, bir <xref:System.Windows.Controls.RichTextBox> nesnesi, düzenlenebilir içeriği içeren bir <xref:System.Windows.Documents.FlowDocument> nesne barındırır. İçindeki <xref:System.Windows.Controls.RichTextBox>akış içeriğini göstermek için aşağıdaki kod, bir paragraf ve bazı kalın metin içeren <xref:System.Windows.Controls.RichTextBox> bir oluşturma gösterir.

[!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]

[!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
[!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]

Aşağıdaki çizim, bu örneğin nasıl işlediğini gösterir.

![Içerikle RichTextBox](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")

Gibi <xref:System.Windows.Documents.Paragraph> öğeler ve <xref:System.Windows.Documents.Bold> içindeki içeriğin <xref:System.Windows.Controls.RichTextBox> nasıl göründüğünü belirleme. Kullanıcı içerik düzenlediklerinde <xref:System.Windows.Controls.RichTextBox> bu akış içeriğini değiştirir. Akış içeriğinin özellikleri ve bununla nasıl çalışılacağı hakkında daha fazla bilgi edinmek için bkz. [Flow belgesine genel bakış](../advanced/flow-document-overview.md).

> [!NOTE]
> A <xref:System.Windows.Controls.RichTextBox> içindeki akış içeriği, diğer denetimlerde yer alan akış içeriği gibi davranır. Örneğin, içinde <xref:System.Windows.Controls.RichTextBox> hiç sütun yok ve bu nedenle otomatik yeniden boyutlandırma davranışı yok. Ayrıca, arama, görüntüleme modu, sayfa gezintisi ve yakınlaştırma gibi yerleşik özellikler bir <xref:System.Windows.Controls.RichTextBox>içinde kullanılamaz.

<a name="realtime_spellechecking"></a>

## <a name="real-time-spell-checking"></a>Gerçek zamanlı yazım denetimi

<xref:System.Windows.Controls.TextBox> Veya<xref:System.Windows.Controls.RichTextBox>' de gerçek zamanlı yazım denetimini etkinleştirebilirsiniz. Yazım denetimi açık olduğunda, yanlış yazılmış sözcüklerin altında kırmızı bir çizgi görünür (aşağıdaki resme bakın).

![Yazım&#45;denetimi içeren metin kutusu](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")

Yazım denetimini nasıl etkinleştireceğinizi öğrenmek için bkz. [metin düzenlemede yazım denetimini etkinleştirme](how-to-enable-spell-checking-in-a-text-editing-control.md) .

<a name="context_menu"></a>

## <a name="context-menu"></a>Bağlam Menüsü

Varsayılan olarak, her <xref:System.Windows.Controls.TextBox> ikisi <xref:System.Windows.Controls.RichTextBox> de bir kullanıcı denetimin içine sağ tıkladığında görüntülenen bir bağlam menüsüne sahiptir. Bağlam menüsü, kullanıcının kesmesine, kopyalamasına veya yapıştırmaya izin verir (aşağıdaki çizime bakın).

![Bağlam menüsü olan TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")

Varsayılan olanı geçersiz kılmak için kendi özel bağlam menünüzün oluşturulmasını sağlayabilirsiniz. Daha fazla bilgi için bkz. [RichTextBox Içinde özel bağlam menüsü konumlandırma](how-to-position-a-custom-context-menu-in-a-richtextbox.md) .

<a name="detect_when_content_changes"></a>

## <a name="editing-commands"></a>Komutları Düzenle

Komutları düzenleme, kullanıcıların bir <xref:System.Windows.Controls.RichTextBox>içindeki düzenlenebilir içeriği biçimlendirmesinin mümkün olduğunu sağlar. Temel düzenlemenin yanı sıra, <xref:System.Windows.Controls.RichTextBox> desteklenmeyen biçimlendirme <xref:System.Windows.Controls.TextBox> komutlarını içerir. Örneğin, bir <xref:System.Windows.Controls.RichTextBox>üzerinde düzenlenirken, bir Kullanıcı, kalın metin biçimlendirmesini değiştirmek için CTRL + B tuşlarına basabilir. Kullanılabilir <xref:System.Windows.Documents.EditingCommands> komutların tüm listesi için bkz. Klavye kısayollarını kullanmanın yanı sıra komutları düğmeler gibi diğer denetimlere de bağlayabilirsiniz. Aşağıdaki örnek, kullanıcının metin biçimlendirmesini değiştirmek için kullanabileceği düğmeleri içeren basit bir araç çubuğunun nasıl oluşturulacağını gösterir.

[!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]

Aşağıdaki çizimde bu örneğin nasıl görüntülediği gösterilmektedir.

![Araç çubuğuyla RichTextBox](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")

<a name="editing_commands"></a>

## <a name="detect-when-content-changes"></a>Içeriğin ne zaman değiştiğini Algıla

Genellikle olay, ne zaman bir <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.RichTextBox> daha sonra <xref:System.Windows.UIElement.KeyDown> beklendiğini tahmin edebileceğiniz gibi tespit etmek için kullanılmalıdır. <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> Örnek [olarak bir metin kutusundaki metnin değiştiğini Algıla](how-to-detect-when-text-in-a-textbox-has-changed.md) bölümüne bakın.

<a name="save_load_and_print_richtextbox_content"></a>

## <a name="save-load-and-print-richtextbox-content"></a>RichTextBox İçeriğini Kaydetme, Yükleme ve Yazdırma

Aşağıdaki örnek, bir dosyasının içeriğinin bir <xref:System.Windows.Controls.RichTextBox> dosyaya nasıl kaydedileceğini, bu içeriğin tekrar tekrar <xref:System.Windows.Controls.RichTextBox>yükleneceğini ve içeriğin nasıl yazdırılacağını gösterir. Örnek için biçimlendirme aşağıda verilmiştir.

[!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]

Örnek için arka plan kodu aşağıda verilmiştir.

[!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
[!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır Konuları](richtextbox-how-to-topics.md)
- [TextBox Genel Bakış](textbox-overview.md)
