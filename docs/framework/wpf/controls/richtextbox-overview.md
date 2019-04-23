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
ms.openlocfilehash: 9aa0d33b3cb2c15ba9c1cb7e7d7be9a3125f66d3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162717"
---
# <a name="richtextbox-overview"></a>RichTextBox Genel Bakışı
<xref:System.Windows.Controls.RichTextBox> Paragraflar, görüntüleri, tablolar ve benzeri akış içeriği düzenlemek veya görüntülemek, denetim olanağı sağlar. Bu konu tanıtır <xref:System.Windows.Controls.TextBox> sınıfı ve her ikisinde de kullanma örnekleri sağlar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve C#.  

<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox veya RichTextBox?  
 Her ikisi de <xref:System.Windows.Controls.RichTextBox> ve <xref:System.Windows.Controls.TextBox> metnini düzenlemek kullanıcılara izin ver, ancak iki denetimleri farklı senaryolarda kullanılır. A <xref:System.Windows.Controls.RichTextBox> kullanıcı biçimlendirilmiş metin, resimler, tablolar veya diğer zengin içerik düzenlemek gerekli olduğunda daha iyi bir seçimdir. Örneğin, bir belge, makale veya biçimlendirme, gerektiren blog düzenleme görüntüleri, vb., kullanarak en iyi şekilde gerçekleştirilir bir <xref:System.Windows.Controls.RichTextBox>. A <xref:System.Windows.Controls.TextBox> daha az sistem kaynağı gerektiren bir <xref:System.Windows.Controls.RichTextBox> yalnızca düz metin gerekiyor olabilir (yani kullanım Forms'ta) düzenlendiğinde idealdir. Bkz: [TextBox genel bakışı](textbox-overview.md) hakkında daha fazla bilgi için <xref:System.Windows.Controls.TextBox>. Aşağıdaki tabloda bulunan temel özellikler özetlenmektedir <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.RichTextBox>.  
  
|Denetim|Gerçek zamanlı yazım denetimi|Bağlam Menüsü|Biçimlendirme komutları gibi <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (CTRL + B)|<xref:System.Windows.Documents.FlowDocument> görüntüleri, paragraf, tablolar vb. gibi içeriği.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Evet|Evet|Hayır|Hayır.|  
|<xref:System.Windows.Controls.RichTextBox>|Evet|Evet|Evet|Evet|  
  
 **Not:** Ancak <xref:System.Windows.Controls.TextBox> biçimlendirme gibi ilgili komutları desteklemiyor <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (CTRL + B) birçok temel komutları gibi her iki denetim tarafından desteklenen <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>.  
  
 Yukarıdaki tabloda özelliklerinden daha sonra ayrıntılı olarak ele alınmaktadır.  
  
<a name="creating_a_richtextbox"></a>   
## <a name="creating-a-richtextbox"></a>Bir RichTextBox'ı oluşturma  
 Aşağıdaki kod nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.RichTextBox> kullanıcı zengin içerik içinde düzenleyebilirsiniz.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]  
  
 İçerik özellikle, düzenlenebilir bir <xref:System.Windows.Controls.RichTextBox> akış içeriğidir. Akış içeriği öğeleri biçimlendirilmiş metin, görüntüler, listeler ve tablolar dahil olmak üzere birçok türü içerebilir. Bkz: [akış belgesine genel bakış](../advanced/flow-document-overview.md) için akış belgeleri hakkında ayrıntılı bilgi. Akış içeriği için bir <xref:System.Windows.Controls.RichTextBox> konakları bir <xref:System.Windows.Documents.FlowDocument> sırayla düzenlenebilir içerik içeren nesne. Akış içeriği göstermek için bir <xref:System.Windows.Controls.RichTextBox>, aşağıdaki kod nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.RichTextBox> paragrafı ve kalın metin.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]  
  
 [!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
 [!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]  
  
 Aşağıdaki çizim, bu örnek nasıl işlediğini gösterir.  
  
 ![RichTextBox içerikle](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")  
  
 Gibi öğeler <xref:System.Windows.Documents.Paragraph> ve <xref:System.Windows.Documents.Bold> belirlemek nasıl içerik içinde bir <xref:System.Windows.Controls.RichTextBox> görünür. Bir kullanıcı düzenlemeleri gibi <xref:System.Windows.Controls.RichTextBox> içerik, bunlar Bu akış içeriğini değiştirir. Akış içeriği nasıl çalışacağınız ve özellikler hakkında daha fazla bilgi edinmek için [akış belgesine genel bakış](../advanced/flow-document-overview.md).  
  
 **Not:** Akış içeriği içinde bir <xref:System.Windows.Controls.RichTextBox> tam olarak diğer denetimlerde akış içeriği gibi davranmaz. Örneğin, hiç sütun yok bir <xref:System.Windows.Controls.RichTextBox> ve bu nedenle otomatik boyutlandırma davranışı. Ayrıca, arama, görüntüleme modunda, sayfa gezintisi ve yakınlaştırma içinde kullanılabilir değil gibi özellikleri yerleşik bir <xref:System.Windows.Controls.RichTextBox>.  
  
<a name="realtime_spellechecking"></a>   
## <a name="real-time-spell-checking"></a>Gerçek zamanlı yazım denetimi  
 Gerçek zamanlı yazım denetimini etkinleştirmeniz bir <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.RichTextBox>. Yazım denetimi etkinleştirildiğinde, (aşağıdaki resme bakın) yanlış yazılan sözcükleri altında kırmızı bir çizgi görünür.  
  
 ![TextBox ile yazım&#45;denetimi](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Bkz: [metin düzenleme denetiminde yazım denetimini etkinleştirme](how-to-enable-spell-checking-in-a-text-editing-control.md) nasıl etkinleştirileceğini öğrenin.  
  
<a name="context_menu"></a>   
## <a name="context-menu"></a>Bağlam Menüsü  
 Varsayılan olarak, her ikisi de <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.RichTextBox> sahip bir kullanıcı denetimi içinde tıklattığında görüntülenen bir bağlam menüsü. Bağlam menüsü kesme, kopyalama ve yapıştırma izin verir (aşağıdaki resme bakın).  
  
 ![Metin kutusu bağlam menüsü ile](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Varsayılan geçersiz kılmak için kendi özel bağlam menüsü oluşturabilirsiniz. Bkz: [RichTextBox içinde özel bağlam menüsü konumlandırma](how-to-position-a-custom-context-menu-in-a-richtextbox.md) daha fazla bilgi için.  
  
<a name="detect_when_content_changes"></a>   
## <a name="editing-commands"></a>Düzenleme komutları  
 Düzenleme komutları, etkin kullanıcılar içinde düzenlenebilir içerik biçimlendirmek için bir <xref:System.Windows.Controls.RichTextBox>. Temel yanı sıra düzenleme komutları <xref:System.Windows.Controls.RichTextBox> içeren komutları biçimlendirme <xref:System.Windows.Controls.TextBox> desteklemez. Örneğin, içinde düzenlerken bir <xref:System.Windows.Controls.RichTextBox>, kalın metin biçimlendirmesini açıp kapatmak için CTRL + B kullanıcı tuşuna basın. Bkz: <xref:System.Windows.Documents.EditingCommands> kullanılabilir komutların tam bir listesi için. Klavye kısayolları kullanmanın yanı sıra komut düğmeleri gibi diğer denetimlere bağlayabilirsiniz. Aşağıdaki örnek, basit bir araç çubuğu kullanıcı metin biçimlendirmesini değiştirmek için kullanabileceğiniz bir düğme içeren oluşturma işlemi gösterilmektedir.  
  
 [!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]  
  
 Aşağıdaki çizim, bu örneğin nasıl görüntülediğini gösterir.  
  
 ![Araç çubuğu ile RichTextBox](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>İçerik değişikliklerini Algıla  
 Genellikle <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay değiştiğinde algılamak için kullanılması gerekir metinde bir <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.RichTextBox> yerine <xref:System.Windows.UIElement.KeyDown> bekleyebileceğiniz gibi. Bkz: [algılamak, metni bir metin kutusu değişti](how-to-detect-when-text-in-a-textbox-has-changed.md) örneği.  
  
<a name="save_load_and_print_richtextbox_content"></a>   
## <a name="save-load-and-print-richtextbox-content"></a>RichTextBox İçeriğini Kaydetme, Yükleme ve Yazdırma  
 Aşağıdaki örnek nasıl kaydedileceğini içeriğini gösterir bir <xref:System.Windows.Controls.RichTextBox> , içerik tekrar içine bir dosyaya yük <xref:System.Windows.Controls.RichTextBox>ve içeriği yazdır. Bu örnek için biçimlendirme aşağıda verilmiştir.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
 Arka plan kod örnek için aşağıda verilmiştir.  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır Konuları](richtextbox-how-to-topics.md)
- [TextBox Genel Bakış](textbox-overview.md)
