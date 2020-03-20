---
title: TextBox Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 9fbae5ac4de4c78a1086bcbd9bfc9e01eb597fb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186637"
---
# <a name="textbox-overview"></a>TextBox Genel Bakışı
Sınıf, <xref:System.Windows.Controls.TextBox> biçimlendirilmemiş metni görüntülemenizi veya görüntülemenizi sağlar. Biçimlendirilmemiş <xref:System.Windows.Controls.TextBox> metni biçimlendirilmemiş bir biçimde düzenlemek, yaygın bir kullanımdır. Örneğin, kullanıcının adını, telefon numarasını vb. soran bir <xref:System.Windows.Controls.TextBox> form, metin girişi için denetimleri kullanır. Bu konu <xref:System.Windows.Controls.TextBox> sınıfı tanır ve hem de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] C# nasıl kullanılacağına örnekler sağlar.  

<a name="textbox_or_richtextbox"></a>
## <a name="textbox-or-richtextbox"></a>TextBox veya RichTextBox?  
 Her <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> ikisi de ve kullanıcıların metin girişine izin, ancak iki denetimfarklı senaryolar için kullanılır. A <xref:System.Windows.Controls.TextBox> daha az sistem <xref:System.Windows.Controls.RichTextBox> kaynakları gerektirir, bu nedenle yalnızca düz metnin düzenlenmesi gerektiğinde (yani bir biçimde kullanım) idealdir. A, <xref:System.Windows.Controls.RichTextBox> kullanıcının biçimlendirilmiş metni, resimleri, tabloları veya desteklenen diğer içeriği yeniden biçimlendirmesi gerektiğinde daha iyi bir seçimdir. Örneğin, biçimlendirme, resim vb. gerektiren bir belgeyi, makaleyi veya blogu düzenleme en iyi şekilde bir <xref:System.Windows.Controls.RichTextBox>. Aşağıdaki tabloda birincil özellikleri <xref:System.Windows.Controls.TextBox> özetler ve <xref:System.Windows.Controls.TextBox>.  
  
|Denetim|Gerçek Zamanlı Yazım Denetimi|Bağlam Menüsü|(Ctr+B) gibi <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> komutları biçimlendirme|<xref:System.Windows.Documents.FlowDocument>resimler, paragraflar, tablolar, vb. gibi içerikler|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Evet|Evet|Hayır|Hayır.|  
|<xref:System.Windows.Controls.RichTextBox>|Evet|Evet|Evet (bkz: [RichTextBox Genel Bakış)](richtextbox-overview.md)|Evet (bkz: [RichTextBox Genel Bakış)](richtextbox-overview.md)|  
  
> [!NOTE]
> (Ctr+B) gibi <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> ilgili düzenleme komutlarını biçimlendirmeyi desteklemese de, birçok <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>temel komut . Daha fazla bilgi edinmek için bkz. <xref:System.Windows.Documents.EditingCommands>.  
  
 Desteklenen <xref:System.Windows.Controls.TextBox> özellikler aşağıdaki bölümlerde ele alınmıştır. Hakkında <xref:System.Windows.Controls.RichTextBox>daha fazla bilgi için [RichTextBox Genel Bakış'a](richtextbox-overview.md)bakın.  
  
### <a name="real-time-spellchecking"></a>Gerçek Zamanlı Yazım Denetimi  
 Gerçek zamanlı yazım denetimi'ni <xref:System.Windows.Controls.TextBox> bir <xref:System.Windows.Controls.RichTextBox>veya . Yazım denetimi açık olduğunda, yanlış yazılmış sözcüklerin altında kırmızı bir çizgi belirir (aşağıdaki resme bakın).  
  
 ![Yazım&#45;denetimi olan textbox](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Yazım denetiminin nasıl etkinleştirilen öğrenilen [Metin Düzenleme Denetiminde Yazım Denetimi'ni Etkinleştir'e](how-to-enable-spell-checking-in-a-text-editing-control.md) bakın.  
  
### <a name="context-menu"></a>Bağlam Menüsü  
 Varsayılan olarak, <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> her ikisi de ve bir kullanıcı denetim içinde sağ tıkladığında görünen bir bağlam menüsü var. Bağlam menüsü, kullanıcının kesmesine, kopyalamasına veya yapıştırmasına olanak tanır (aşağıdaki resme bakın).  
  
 ![Bağlam menüsü ile TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Varsayılan davranışı geçersiz kılmak için kendi özel bağlam menünüzü oluşturabilirsiniz. Bkz. Daha fazla bilgi için [TextBox içeren Özel Bağlam Menüsü](how-to-use-a-custom-context-menu-with-a-textbox.md) kullanın.  
  
<a name="creating_textboxes"></a>
## <a name="creating-textboxes"></a>TextBoxes oluşturma  
 A, <xref:System.Windows.Controls.TextBox> yüksekliği tek bir satır olabilir veya birden çok çizgiden oluşabilir. Tek bir <xref:System.Windows.Controls.TextBox> satır, küçük miktarda düz metin (örneğin, "Ad", "Telefon Numarası" vb. bir formda) girerek en iyisidir. Aşağıdaki örnekte, tek bir <xref:System.Windows.Controls.TextBox>satırın nasıl oluşturulabildiğini gösterilmektedir.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Ayrıca, kullanıcının <xref:System.Windows.Controls.TextBox> birden çok metin satırı girmesini sağlayan bir metin de oluşturabilirsiniz. Örneğin, formunuz kullanıcının biyografik çizimi için sorulursa, birden çok metin satırını destekleyen bir metin <xref:System.Windows.Controls.TextBox> kullanmak istersiniz. Aşağıdaki örnek, birden [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] çok metin <xref:System.Windows.Controls.TextBox> satırını barındıracak şekilde otomatik olarak genişleyen bir denetimi tanımlamak için nasıl kullanılacağını gösterir.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 <xref:System.Windows.Controls.TextBox.TextWrapping%2A> `Wrap` Özniteliği, <xref:System.Windows.Controls.TextBox> denetimin kenarına ulaşıldığında metnin yeni bir satıra kaydırılmasına <xref:System.Windows.Controls.TextBox> neden olur ve gerekirse yeni bir satır için yer içerecek şekilde denetimi otomatik olarak genişletir.  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> Özniteliğin, `true` RETURN tuşuna basıldığında yeni bir satır eklenmesine neden olur ve <xref:System.Windows.Controls.TextBox> gerekirse yeni bir satır için yer içerecek şekilde bir kez daha otomatik olarak genişletilir.  
  
 Öznitelik, <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> çerçevenin veya pencerenin boyutunun ötesine <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox> genişletilirse içeriğinin kaydırılması için kaydırma çubuğu ekler. <xref:System.Windows.Controls.TextBox>  
  
 Bir kullanarak ilişkili farklı görevler <xref:System.Windows.Controls.TextBox>hakkında daha fazla bilgi için, [Bkz. Konular Nasıl?](textbox-how-to-topics.md)  
  
<a name="editing_commands"></a>
## <a name="detect-when-content-changes"></a>İçerik Ne Zaman Değiştiğini Algılama  
 Genellikle <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay, bir metin dediğinde <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.RichTextBox> değişiklikler dediğinde, <xref:System.Windows.UIElement.KeyDown> beklediğiniz gibi algılamak için kullanılmalıdır. Bkz. TextBox'taki Metin bir örnek için [Değiştiğinde Algıla.](how-to-detect-when-text-in-a-textbox-has-changed.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Dır Konular](textbox-how-to-topics.md)
- [RichTextBox Genel Bakış](richtextbox-overview.md)
