---
title: TextBox Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 5ddd6600493cd127f8024f23594c628476cac19e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361076"
---
# <a name="textbox-overview"></a>TextBox Genel Bakışı
<xref:System.Windows.Controls.TextBox> Sınıfı görüntülemek veya biçimlendirilmemiş metin düzenlemenize olanak sağlar. Yaygın bir <xref:System.Windows.Controls.TextBox> form biçimlendirilmemiş metin düzenleme. Örneğin, kullanıcının adı, telefon numarası için soran bir form vb. kullanırsınız <xref:System.Windows.Controls.TextBox> metin girişi denetimleri. Bu konu tanıtır <xref:System.Windows.Controls.TextBox> sınıfı ve her ikisinde de kullanma örnekleri sağlar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve C#.  
  
 
  
<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox veya RichTextBox?  
 Her ikisi de <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.RichTextBox> metin girişi kullanıcıların ancak iki denetimleri farklı senaryolar için kullanılırlar. A <xref:System.Windows.Controls.TextBox> daha az sistem kaynağı gerektiren bir <xref:System.Windows.Controls.RichTextBox> yalnızca düz metin düzenlenecek gerektiğinde ideal, bu nedenle (yani, bir form kullanımı). A <xref:System.Windows.Controls.RichTextBox> kullanıcı biçimlendirilmiş metin, resimler, tablolar düzenlemek gerekli olan veya desteklenen diğer daha iyi bir seçenek içeriktir. Örneğin, bir belge, makale veya biçimlendirme, gerektiren blog düzenleme görüntüleri, vb., kullanarak en iyi şekilde gerçekleştirilir bir <xref:System.Windows.Controls.RichTextBox>. Aşağıdaki tabloda birincil özelliklerini özetler <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.TextBox>.  
  
|Denetim|Gerçek zamanlı yazım denetimi|Bağlam Menüsü|Biçimlendirme komutları gibi <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (CTRL + B)|<xref:System.Windows.Documents.FlowDocument> görüntüleri, paragraf, tablolar vb. gibi içeriği.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Evet|Evet|Hayır|Hayır.|  
|<xref:System.Windows.Controls.RichTextBox>|Evet|Evet|Evet (bkz [RichTextBox Genel Bakış](richtextbox-overview.md))|Evet (bkz [RichTextBox Genel Bakış](richtextbox-overview.md))|  
  
> [!NOTE]
>  Ancak <xref:System.Windows.Controls.TextBox> ilgili düzenleme biçimlendirme desteği komutları gibi mu <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (CTRL + B) birçok temel komutları gibi her iki denetim tarafından desteklenen <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>. Daha fazla bilgi edinmek için bkz. <xref:System.Windows.Documents.EditingCommands>.  
  
 Tarafından desteklenen özellikler <xref:System.Windows.Controls.TextBox> aşağıdaki bölümlerde ele alınmıştır. Hakkında daha fazla bilgi için <xref:System.Windows.Controls.RichTextBox>, bkz: [RichTextBox Genel Bakış](richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Gerçek zamanlı yazım denetimi  
 Gerçek zamanlı yazım denetimini etkinleştirmek bir <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.RichTextBox>. Yazım denetimi etkinleştirildiğinde, (aşağıdaki resme bakın) yanlış yazılan sözcükleri altında kırmızı bir çizgi görünür.  
  
 ![TextBox ile yazım&#45;denetimi](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Bkz: [metin düzenleme denetiminde yazım denetimini etkinleştirme](how-to-enable-spell-checking-in-a-text-editing-control.md) nasıl etkinleştirileceğini öğrenin.  
  
### <a name="context-menu"></a>Bağlam Menüsü  
 Varsayılan olarak, her ikisi de <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.RichTextBox> sahip bir kullanıcı denetimi içinde tıklattığında görüntülenen bir bağlam menüsü. Bağlam menüsü kesme, kopyalama ve yapıştırma izin verir (aşağıdaki resme bakın).  
  
 ![Metin kutusu bağlam menüsü ile](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Varsayılan davranışı geçersiz kılmak için kendi özel bağlam menüsü oluşturabilirsiniz. Bkz: [TextBox ile özel bağlam menüsü kullanma](how-to-use-a-custom-context-menu-with-a-textbox.md) daha fazla bilgi için.  
  
<a name="creating_textboxes"></a>   
## <a name="creating-textboxes"></a>Metin kutuları oluşturma  
 A <xref:System.Windows.Controls.TextBox> tek satır yüksekliği olabilir veya birden çok satırı kapsayabilir. Tek bir satır <xref:System.Windows.Controls.TextBox> küçük miktardaki düz metin (girişleri için idealdir "Name", "Phone Number", bir formda vb.). Aşağıdaki örnek, tek bir satır oluşturma işlemi gösterilmektedir <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Ayrıca oluşturabileceğiniz bir <xref:System.Windows.Controls.TextBox> çok satırlı metin girmesini sağlar. Örneğin, formunuza, kullanıcının biyografik taslak için istenirse, kullanmak isteyebilirsiniz bir <xref:System.Windows.Controls.TextBox> , birden çok metin satırı destekler. Aşağıdaki örnek nasıl kullanılacağını gösterir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tanımlamak için bir <xref:System.Windows.Controls.TextBox> birden çok metin satırı uyum sağlayacak şekilde otomatik olarak genişleyen bir denetim.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 Ayarlama <xref:System.Windows.Controls.TextBox.TextWrapping%2A> özniteliğini `Wrap` yeni bir kaydırılmasına neden olur olduğunda satır kenarı <xref:System.Windows.Controls.TextBox> denetim ulaşıldığında, otomatik olarak <xref:System.Windows.Controls.TextBox> gerekirse yeni bir satır için yer içerecek şekilde denetim.  
  
 Ayarı <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> özniteliğini `true` RETURN tuşuna basıldığında, bir kez daha otomatik olarak eklenmesi için yeni bir satır neden <xref:System.Windows.Controls.TextBox> gerekirse yeni bir satır için yer eklenecek.  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> Özniteliği için bir kaydırma çubuğu ekler <xref:System.Windows.Controls.TextBox>, böylece içeriğini <xref:System.Windows.Controls.TextBox> değilse kaydırılabileceğini <xref:System.Windows.Controls.TextBox> veya kendisini kapsayan pencerenin boyutu genişletir.  
  
 Kullanmayla ilişkili farklı görevler hakkında daha fazla bilgi için bir <xref:System.Windows.Controls.TextBox>, bkz: [nasıl-yapılır konularına](textbox-how-to-topics.md).  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>İçerik değişikliklerini Algıla  
 Genellikle <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay değiştiğinde algılamak için kullanılması gerekir metinde bir <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.RichTextBox> yerine, değişiklikleri <xref:System.Windows.UIElement.KeyDown> bekleyebileceğiniz gibi. Bkz: [algılamak, metni bir metin kutusu değişti](how-to-detect-when-text-in-a-textbox-has-changed.md) örneği.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Yapılır Konuları](textbox-how-to-topics.md)
- [RichTextBox Genel Bakış](richtextbox-overview.md)
