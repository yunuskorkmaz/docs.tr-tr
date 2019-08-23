---
title: TextBox Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 46600fd1a3023a80d49fae6f020279be6131916a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951482"
---
# <a name="textbox-overview"></a>TextBox Genel Bakışı
<xref:System.Windows.Controls.TextBox> Sınıfı biçimlendirilmemiş metni görüntülemenizi veya düzenlemenizi sağlar. Yaygın bir <xref:System.Windows.Controls.TextBox> kullanımı, biçimlendirilmemiş metnin bir formda düzenlenmesinden oluşur. Örneğin, kullanıcının adı, telefon numarası, vb. gibi bir form da metin girişi denetimlerini kullanır <xref:System.Windows.Controls.TextBox> . Bu konu <xref:System.Windows.Controls.TextBox> sınıfı tanıtır ve hem [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] hem de içinde nasıl kullanılacağına ilişkin örnekler sağlar. C#  

<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox veya RichTextBox?  
 Hem hem de <xref:System.Windows.Controls.TextBox> kullanıcıların metin girmesini sağlar,ancakikidenetimfarklısenaryolariçinkullanılır.<xref:System.Windows.Controls.RichTextBox> , Daha az sistem kaynağı <xref:System.Windows.Controls.RichTextBox> gerektirir,bunedenleyalnızcadüzmetindüzenlenmesigerektiğinde(örneğin,birformdakullanım)idealdir.<xref:System.Windows.Controls.TextBox> Kullanıcının <xref:System.Windows.Controls.RichTextBox> biçimlendirilen metin, resim, tablo veya desteklenen diğer içerikleri düzenlemesi gerektiğinde daha iyi bir seçenektir. Örneğin, bir <xref:System.Windows.Controls.RichTextBox>belge, makale veya blogın biçimlendirilmesi, resimler, vb. kullanarak en iyi şekilde yapılması önerilir. Aşağıdaki tablo, ve ' <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox>nin birincil özelliklerini özetler.  
  
|Denetim|Gerçek zamanlı yazım denetimi|Bağlam Menüsü|Gibi <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> biçimlendirme komutları (Ctrl + B)|<xref:System.Windows.Documents.FlowDocument>görüntüler, paragraflar, tablolar vb. içerikler|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Evet|Evet|Hayır|Hayır.|  
|<xref:System.Windows.Controls.RichTextBox>|Evet|Evet|Evet (bkz. [RichTextBox 'A genel bakış](richtextbox-overview.md))|Evet (bkz. [RichTextBox 'A genel bakış](richtextbox-overview.md))|  
  
> [!NOTE]
> , <xref:System.Windows.Controls.TextBox> (CTR + B) gibi <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> ilişkili Düzenle komutlarının biçimlendirilmesini desteklemez, ancak gibi birçok temel komut, her iki denetim tarafından da <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>desteklenir. Daha fazla bilgi edinmek için bkz. <xref:System.Windows.Documents.EditingCommands>.  
  
 Tarafından <xref:System.Windows.Controls.TextBox> desteklenen özellikler aşağıdaki bölümlerde ele alınmıştır. Hakkında <xref:System.Windows.Controls.RichTextBox>daha fazla bilgi için bkz. [RichTextBox genel bakış](richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Gerçek zamanlı yazım denetimi  
 <xref:System.Windows.Controls.TextBox> Veya<xref:System.Windows.Controls.RichTextBox>' de gerçek zamanlı yazım denetimini etkinleştirebilirsiniz. Yazım denetimi açık olduğunda, yanlış yazılmış sözcüklerin altında kırmızı bir çizgi görünür (aşağıdaki resme bakın).  
  
 ![Yazım&#45;denetimi içeren metin kutusu](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Yazım denetimini nasıl etkinleştireceğinizi öğrenmek için bkz. [metin düzenlemede yazım denetimini etkinleştirme](how-to-enable-spell-checking-in-a-text-editing-control.md) .  
  
### <a name="context-menu"></a>Bağlam Menüsü  
 Varsayılan olarak, her <xref:System.Windows.Controls.TextBox> ikisi <xref:System.Windows.Controls.RichTextBox> de bir kullanıcı denetimin içine sağ tıkladığında görüntülenen bir bağlam menüsüne sahiptir. Bağlam menüsü, kullanıcının kesmesine, kopyalamasına veya yapıştırmaya izin verir (aşağıdaki resme bakın).  
  
 ![Bağlam menüsü olan TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Varsayılan davranışı geçersiz kılmak için kendi özel bağlam menüsünü oluşturabilirsiniz. Daha fazla bilgi için bkz. [TextBox Ile özel bağlam menüsü kullanma](how-to-use-a-custom-context-menu-with-a-textbox.md) .  
  
<a name="creating_textboxes"></a>   
## <a name="creating-textboxes"></a>Metin kutuları oluşturma  
 Bir <xref:System.Windows.Controls.TextBox> yükseklik veya birden çok satırı kapsayan tek bir satır olabilir. Tek bir satır <xref:System.Windows.Controls.TextBox> , küçük miktarlarda düz metin koymak için idealdir (ör. "Ad", "telefon numarası", vb. bir biçimde). Aşağıdaki örnek tek bir satırın <xref:System.Windows.Controls.TextBox>nasıl oluşturulacağını göstermektedir.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Ayrıca, kullanıcının birden çok <xref:System.Windows.Controls.TextBox> satır metin girmelerini sağlayan bir de oluşturabilirsiniz. Örneğin, formunuz Kullanıcı için bir biyografik taslağı isteniyorsa, birden çok satırı destekleyen bir <xref:System.Windows.Controls.TextBox> kullanmak isteyebilirsiniz. Aşağıdaki örnek, metnin birden çok satırını [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kapsayacak şekilde otomatik <xref:System.Windows.Controls.TextBox> olarak genişleyen bir denetim tanımlamak için öğesinin nasıl kullanılacağını gösterir.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 Özniteliği, denetiminkenarına<xref:System.Windows.Controls.TextBox> ulaşıldığında metnin yeni bir satıra kaydırılmasına neden olacak şekilde `Wrap` ayarlandığında, gerekirse yeni bir satıra yer açmak için <xref:System.Windows.Controls.TextBox> denetimin otomatik olarak genişletilmesi gerekir. <xref:System.Windows.Controls.TextBox.TextWrapping%2A>  
  
 Özniteliği olarak `true` ayarlamak, dönüş tuşuna basıldığında yeni bir satırın eklenmesine bir <xref:System.Windows.Controls.TextBox> kez, gerekirse yeni bir satıra yer açmak için otomatik olarak genişleyen yeni bir satır eklenmesine neden olur. <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>  
  
 Özniteliği öğesine bir kaydırma çubuğu ekler. böylece, öğesinin <xref:System.Windows.Controls.TextBox> içeriğinin, kendisini kapsayan çerçeve veya pencere boyutundan daha fazla <xref:System.Windows.Controls.TextBox> genişliyorsa kaydırılabilmesini sağlar. <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>  
  
 Kullanımıyla <xref:System.Windows.Controls.TextBox>ilişkili farklı görevler hakkında daha fazla bilgi için bkz. [nasıl yapılır konuları](textbox-how-to-topics.md).  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>Içeriğin ne zaman değiştiğini Algıla  
 Genellikle olay, ne zaman bir <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> veya bir değiştiğinde, bekleneceğiniz gibi,herseferindetespitetmekiçinkullanılmalıdır.<xref:System.Windows.UIElement.KeyDown> <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> Örnek [olarak bir metin kutusundaki metnin değiştiğini Algıla](how-to-detect-when-text-in-a-textbox-has-changed.md) bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır Konuları](textbox-how-to-topics.md)
- [RichTextBox Genel Bakış](richtextbox-overview.md)
