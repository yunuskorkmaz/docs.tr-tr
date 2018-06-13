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
ms.openlocfilehash: 319dc43c0953b82da94eb6dd698f1a6afd582dbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557530"
---
# <a name="richtextbox-overview"></a>RichTextBox Genel Bakışı
<xref:System.Windows.Controls.RichTextBox> Denetimi görüntülemek veya paragraflar, görüntüler, tablolar ve benzeri bir akış içeriğini düzenlemenize olanak sağlar. Bu konu tanıtır <xref:System.Windows.Controls.TextBox> sınıfı ve ikisi de kullanma örnekleri sağlar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve C#.  
  
  
<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox veya RichTextBox?  
 Her ikisi de <xref:System.Windows.Controls.RichTextBox> ve <xref:System.Windows.Controls.TextBox> metnini düzenlemek kullanıcılara izin ver, ancak iki denetim farklı senaryolarda kullanılır. A <xref:System.Windows.Controls.RichTextBox> kullanıcı biçimlendirilmiş metin, görüntüler, tablolar veya başka zengin içerik düzenlemek gerekli olduğunda daha iyi bir seçimdir. Örneğin, bir belge, makale veya biçimlendirme, gerektirir blog düzenleme görüntüleri, vb., kullanarak en iyi şekilde gerçekleştirilir bir <xref:System.Windows.Controls.RichTextBox>. A <xref:System.Windows.Controls.TextBox> daha az sistem kaynağı gerektiren sonra bir <xref:System.Windows.Controls.RichTextBox> ve olması yalnızca düz metin gerekir (yani kullanım formlarında) düzenlendiğinde idealdir. Bkz: [TextBox genel bakış](../../../../docs/framework/wpf/controls/textbox-overview.md) hakkında daha fazla bilgi için <xref:System.Windows.Controls.TextBox>. Ana özellikleri, aşağıdaki tabloda özetlenmiştir <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.RichTextBox>.  
  
|Denetim|Gerçek zamanlı yazım denetimi|Bağlam menüsü|Biçimlendirme komutları gibi <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (CTRL + B)|<xref:System.Windows.Documents.FlowDocument> içerik görüntüler, paragraflar, tablolar vb. gibi.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Evet|Evet|Hayır|Hayır.|  
|<xref:System.Windows.Controls.RichTextBox>|Evet|Evet|Evet|Evet|  
  
 **Not:** rağmen <xref:System.Windows.Controls.TextBox> biçimlendirme gibi ilgili komutları desteklemiyor <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (CTRL + B), birçok temel komut her iki denetim tarafından da desteklenir <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>.  
  
 Yukarıdaki tablodaki özellikleri daha sonra daha ayrıntılı olarak ele alınmıştır.  
  
<a name="creating_a_richtextbox"></a>   
## <a name="creating-a-richtextbox"></a>RichTextBox oluşturma  
 Aşağıdaki kodu nasıl oluşturulacağını gösterir bir <xref:System.Windows.Controls.RichTextBox> bir kullanıcı zengin içerik içinde düzenleyebilirsiniz.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]  
  
 İçinde düzenlenen içerik özellikle, bir <xref:System.Windows.Controls.RichTextBox> akış içeriğidir. Akış içeriği türlerde biçimlendirilmiş metin, görüntüler, listeleri ve tabloları gibi öğeleri içerebilir. Bkz: [akış belge genel bakış](../../../../docs/framework/wpf/advanced/flow-document-overview.md) için akış belgeleri üzerine derin bilgiler. Akış içeriği için bir <xref:System.Windows.Controls.RichTextBox> konakları bir <xref:System.Windows.Documents.FlowDocument> sırayla düzenlenebilir içerik içeren nesne. İçindeki akış içeriğini göstermek için bir <xref:System.Windows.Controls.RichTextBox>, aşağıdaki kodu nasıl oluşturulacağını gösterir bir <xref:System.Windows.Controls.RichTextBox> paragrafı ve bazı kalın metin.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]  
  
 [!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
 [!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]  
  
 Aşağıdaki çizimde, bu örnek nasıl işlediğini gösterir.  
  
 ![RichTextBox içerikle](../../../../docs/framework/wpf/controls/media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")  
  
 Öğeler <xref:System.Windows.Documents.Paragraph> ve <xref:System.Windows.Documents.Bold> belirlemek nasıl içinde içerik bir <xref:System.Windows.Controls.RichTextBox> görüntülenir. Bir kullanıcı düzenlediği gibi <xref:System.Windows.Controls.RichTextBox> içerik, bunlar Bu akış içeriğini değiştirir. Akış içeriği özellikleri ve nasıl çalışacağınız hakkında daha fazla bilgi için bkz: [akış belge genel bakış](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
 **Not:** içindeki akış içeriği bir <xref:System.Windows.Controls.RichTextBox> tam olarak diğer denetimlerde akış içeriği gibi davranırlar değil. Örneğin, hiç sütun yok bir <xref:System.Windows.Controls.RichTextBox> ve bu nedenle hiçbir otomatik yeniden boyutlandırma davranışı. Ayrıca, arama, görüntüleme modu, sayfa gezintisi ve yakınlaştırma içinde kullanılabilir olmadığından gibi özellikleri yerleşik bir <xref:System.Windows.Controls.RichTextBox>.  
  
<a name="realtime_spellechecking"></a>   
## <a name="real-time-spell-checking"></a>Gerçek zamanlı yazım denetimi  
 Gerçek zamanlı yazım denetimi etkinleştirebilirsiniz bir <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.RichTextBox>. Yazım denetimi açıldığında, kırmızı bir çizgi (aşağıdaki resme bakın) yanlış yazılmış sözcüklerin altında görüntülenir.  
  
 ![Yazım kutusuyla&#45;denetimi](../../../../docs/framework/wpf/controls/media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Bkz: [metin düzenleme denetiminde yazım denetimi etkinleştir](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md) nasıl etkinleştirileceğini öğrenin.  
  
<a name="context_menu"></a>   
## <a name="context-menu"></a>Bağlam menüsü  
 Varsayılan olarak, her ikisi de <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.RichTextBox> kullanıcı içindeki denetim tıkladığında, görünen bağlam menüsüne sahiptir. Bağlam menüsü kesme, kopyalama ve yapıştırma olanak tanır (çizimde bakın).  
  
 ![Bağlam menüsü kutusuyla](../../../../docs/framework/wpf/controls/media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Varsayılanı geçersiz kılmak için kendi özel bağlam menüsü oluşturabilirsiniz. Bkz: [RichTextBox içinde özel bağlam menüsü konumlandırma](../../../../docs/framework/wpf/controls/how-to-position-a-custom-context-menu-in-a-richtextbox.md) daha fazla bilgi için.  
  
<a name="detect_when_content_changes"></a>   
## <a name="editing-commands"></a>Düzenleme komutları  
 Düzenleme komutları içinde düzenlenebilir içeriği biçimlendirmek için etkinleştir kullanıcılar bir <xref:System.Windows.Controls.RichTextBox>. Basic yanı sıra düzenleme komutları <xref:System.Windows.Controls.RichTextBox> içeren komutları biçimlendirme <xref:System.Windows.Controls.TextBox> desteklemiyor. Örneğin, içinde düzenlerken bir <xref:System.Windows.Controls.RichTextBox>, bir kullanıcı kalın metin biçimlendirmesini geçiş yapmak için CTRL + B yapmalıdır. Bkz: <xref:System.Windows.Documents.EditingCommands> kullanılabilir komutları tam bir listesi. Klavye kısayolları kullanılarak yanı sıra diğer denetimlere düğmeleri gibi komutları kanca. Aşağıdaki örnek, kullanıcının metin biçimlendirmesini değiştirmek için kullanabileceği düğmeleri içeren çubuğu basit bir aracı oluşturulacağını gösterir.  
  
 [!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]  
  
 Aşağıdaki çizimde, bu örnek nasıl görüntülediğini gösterir.  
  
 ![ToolBar ile RichTextBox](../../../../docs/framework/wpf/controls/media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>İçerik değiştiğinde algılama  
 Genellikle <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay değiştiğinde algılamak için kullanılmalıdır metinde bir <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.RichTextBox> yerine <xref:System.Windows.UIElement.KeyDown> beklediğiniz gibi. Bkz: [algılamak zaman metinde bir metin kutusu değişti](../../../../docs/framework/wpf/controls/how-to-detect-when-text-in-a-textbox-has-changed.md) bir örnek.  
  
<a name="save_load_and_print_richtextbox_content"></a>   
## <a name="save-load-and-print-richtextbox-content"></a>RichTextBox İçeriğini Kaydetme, Yükleme ve Yazdırma  
 Aşağıdaki örnek, içeriği kaydetmek gösterilmiştir bir <xref:System.Windows.Controls.RichTextBox> bir dosyaya, içerik tekrar içine yük <xref:System.Windows.Controls.RichTextBox>ve içindekileri yazdırın. Bu örnek için biçimlendirme aşağıdadır.  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
 Arka plan kod örneğin aşağıdadır.  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/richtextbox-how-to-topics.md)  
 [TextBox Genel Bakış](../../../../docs/framework/wpf/controls/textbox-overview.md)
