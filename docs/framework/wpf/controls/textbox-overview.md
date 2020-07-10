---
title: TextBox Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 86b2cf8cb0c72186fd92bdad0af6bf5bd3fa9f3f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174438"
---
# <a name="textbox-overview"></a>TextBox Genel Bakışı
<xref:System.Windows.Controls.TextBox>Sınıfı biçimlendirilmemiş metni görüntülemenizi veya düzenlemenizi sağlar. Yaygın bir kullanımı <xref:System.Windows.Controls.TextBox> , biçimlendirilmemiş metnin bir formda düzenlenmesinden oluşur. Örneğin, kullanıcının adı, telefon numarası, vb. gibi bir form da <xref:System.Windows.Controls.TextBox> metin girişi denetimlerini kullanır. Bu konu sınıfı tanıtır <xref:System.Windows.Controls.TextBox> ve hem hem de C# içinde nasıl kullanılacağına ilişkin örnekler sağlar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .  

<a name="textbox_or_richtextbox"></a>
## <a name="textbox-or-richtextbox"></a>TextBox veya RichTextBox?  
 Hem hem de <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> Kullanıcıların metin girmesini sağlar, ancak iki denetim farklı senaryolar için kullanılır. <xref:System.Windows.Controls.TextBox>, Daha az sistem kaynağı gerektirir <xref:System.Windows.Controls.RichTextBox> , bu nedenle yalnızca düz metin düzenlenmesi gerektiğinde (örneğin, bir formda kullanım) idealdir. <xref:System.Windows.Controls.RichTextBox>Kullanıcının biçimlendirilen metin, resim, tablo veya desteklenen diğer içerikleri düzenlemesi gerektiğinde daha iyi bir seçenektir. Örneğin, bir belge, makale veya blogın biçimlendirilmesi, resimler, vb. kullanarak en iyi şekilde yapılması önerilir <xref:System.Windows.Controls.RichTextBox> . Aşağıdaki tablo, ve ' nin birincil özelliklerini <xref:System.Windows.Controls.TextBox> özetler <xref:System.Windows.Controls.RichTextBox> .  
  
|Denetim|Gerçek zamanlı yazım denetimi|Bağlam Menüsü|Gibi biçimlendirme komutları <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Ctrl + B)|<xref:System.Windows.Documents.FlowDocument>görüntüler, paragraflar, tablolar vb. içerikler|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Yes|Evet|Hayır|Hayır.|  
|<xref:System.Windows.Controls.RichTextBox>|Yes|Evet|Evet (bkz. [RichTextBox 'A genel bakış](richtextbox-overview.md))|Evet (bkz. [RichTextBox 'A genel bakış](richtextbox-overview.md))|  
  
> [!NOTE]
> <xref:System.Windows.Controls.TextBox>, (CTR + B) gibi ilişkili Düzenle komutlarının biçimlendirilmesini desteklemez, ancak gibi <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> birçok temel komut, her iki denetim tarafından da desteklenir <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A> . Daha fazla bilgi edinmek için bkz. <xref:System.Windows.Documents.EditingCommands>.  
  
 Tarafından desteklenen özellikler <xref:System.Windows.Controls.TextBox> Aşağıdaki bölümlerde ele alınmıştır. Hakkında daha fazla bilgi için <xref:System.Windows.Controls.RichTextBox> bkz. [RichTextBox genel bakış](richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Gerçek zamanlı yazım denetimi  
 Veya ' de gerçek zamanlı yazım denetimini etkinleştirebilirsiniz <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> . Yazım denetimi açık olduğunda, yanlış yazılmış sözcüklerin altında kırmızı bir çizgi görünür (aşağıdaki resme bakın).  
  
 ![Yazım&#45;denetimi içeren metin kutusu](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Yazım denetimini nasıl etkinleştireceğinizi öğrenmek için bkz. [metin düzenlemede yazım denetimini etkinleştirme](how-to-enable-spell-checking-in-a-text-editing-control.md) .  
  
### <a name="context-menu"></a>Bağlam Menüsü  
 Varsayılan olarak, her ikisi de <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> bir kullanıcı denetimin içine sağ tıkladığında görüntülenen bir bağlam menüsüne sahiptir. Bağlam menüsü, kullanıcının kesmesine, kopyalamasına veya yapıştırmaya izin verir (aşağıdaki resme bakın).  
  
 ![Bağlam menüsü olan TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Varsayılan davranışı geçersiz kılmak için kendi özel bağlam menüsünü oluşturabilirsiniz. Daha fazla bilgi için bkz. [TextBox Ile özel bağlam menüsü kullanma](how-to-use-a-custom-context-menu-with-a-textbox.md) .  
  
<a name="creating_textboxes"></a>
## <a name="creating-textboxes"></a>Metin kutuları oluşturma  
 Bir <xref:System.Windows.Controls.TextBox> Yükseklik veya birden çok satırı kapsayan tek bir satır olabilir. Tek bir satır, <xref:System.Windows.Controls.TextBox> küçük miktarlarda düz metin (örn. "ad", "telefon numarası", vb.) almak için idealdir. Aşağıdaki örnek tek bir satırın nasıl oluşturulacağını göstermektedir <xref:System.Windows.Controls.TextBox> .  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Ayrıca <xref:System.Windows.Controls.TextBox> , kullanıcının birden çok satır metin girmelerini sağlayan bir de oluşturabilirsiniz. Örneğin, formunuz Kullanıcı için bir biyografik taslağı isteniyorsa, <xref:System.Windows.Controls.TextBox> birden çok satırı destekleyen bir kullanmak isteyebilirsiniz. Aşağıdaki örnek, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <xref:System.Windows.Controls.TextBox> metnin birden çok satırını kapsayacak şekilde otomatik olarak genişleyen bir denetim tanımlamak için öğesinin nasıl kullanılacağını gösterir.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 Özniteliği, <xref:System.Windows.Controls.TextBox.TextWrapping%2A> `Wrap` denetimin kenarına ulaşıldığında metnin yeni bir satıra kaydırılmasına neden olacak şekilde ayarlandığında <xref:System.Windows.Controls.TextBox> , <xref:System.Windows.Controls.TextBox> gerekirse yeni bir satıra yer açmak için denetimin otomatik olarak genişletilmesi gerekir.  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>Özniteliği olarak ayarlamak, `true` dönüş tuşuna basıldığında yeni bir satırın eklenmesine bir kez, <xref:System.Windows.Controls.TextBox> gerekirse yeni bir satıra yer açmak için otomatik olarak genişleyen yeni bir satır eklenmesine neden olur.  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>Özniteliği öğesine bir kaydırma çubuğu ekler <xref:System.Windows.Controls.TextBox> . böylece, öğesinin içeriğinin, <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox> kendisini kapsayan çerçeve veya pencere boyutundan daha fazla genişliyorsa kaydırılabilmesini sağlar.  
  
 Kullanımıyla ilişkili farklı görevler hakkında daha fazla bilgi için <xref:System.Windows.Controls.TextBox> bkz. [nasıl yapılır konuları](textbox-how-to-topics.md).  
  
<a name="editing_commands"></a>
## <a name="detect-when-content-changes"></a>Içeriğin ne zaman değiştiğini Algıla  
 Genellikle <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay, ne zaman bir <xref:System.Windows.Controls.TextBox> veya bir <xref:System.Windows.Controls.RichTextBox> değiştiğinde, bekleneceğiniz gibi, her seferinde tespit etmek için kullanılmalıdır <xref:System.Windows.UIElement.KeyDown> . Örnek [olarak bir metin kutusundaki metnin değiştiğini Algıla](how-to-detect-when-text-in-a-textbox-has-changed.md) bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır Konuları](textbox-how-to-topics.md)
- [RichTextBox Genel Bakışı](richtextbox-overview.md)
