---
title: TextBox Genel Bakışı
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 02e7a5046dec689b1088585d58e4e424751ac512
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="textbox-overview"></a>TextBox Genel Bakışı
<xref:System.Windows.Controls.TextBox> Sınıfı, biçimlendirilmemiş metni görüntülemenizi ve düzenlemenizi sağlar. Yaygın kullanımı bir <xref:System.Windows.Controls.TextBox> form biçimlendirilmemiş metin düzenleme. Örneğin, kullanıcının adını, telefon numarasını soran bir form vb. kullanırsınız <xref:System.Windows.Controls.TextBox> metin giriş için denetimler. Bu konu tanıtır <xref:System.Windows.Controls.TextBox> sınıfı ve ikisi de kullanma örnekleri sağlar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve C#.  
  
 
  
<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox veya RichTextBox?  
 Her ikisi de <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.RichTextBox> metin girişi yapmalarına izin vermek, ancak iki denetim farklı senaryolar için kullanılır. A <xref:System.Windows.Controls.TextBox> daha az sistem kaynağı gerektiren sonra bir <xref:System.Windows.Controls.RichTextBox> yalnızca düz metin düzenlenmesi gerektiğinde idealdir şekilde (yani, bir formda kullanım). A <xref:System.Windows.Controls.RichTextBox> daha iyi bir kullanıcı biçimlendirilmiş metin, resim, tablo düzenlemek gerekli olduğunda veya diğer desteklenen içerik seçimdir. Örneğin, bir belge, makale veya biçimlendirme, gerektirir blog düzenleme görüntüleri, vb., kullanarak en iyi şekilde gerçekleştirilir bir <xref:System.Windows.Controls.RichTextBox>. Aşağıdaki tabloda birincil özelliklerini özetler <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.TextBox>.  
  
|Denetim|Gerçek zamanlı yazım denetimi|Bağlam menüsü|Biçimlendirme komutları gibi <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (CTRL + B)|<xref:System.Windows.Documents.FlowDocument> içerik görüntüler, paragraflar, tablolar vb. gibi.|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|Evet|Evet|Hayır|Hayır.|  
|<xref:System.Windows.Controls.RichTextBox>|Evet|Evet|Evet (bkz [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md))|Evet (bkz [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md))|  
  
> [!NOTE]
>  Ancak <xref:System.Windows.Controls.TextBox> ilgili düzenleme biçimlendirme desteklemediğinden komutları gibi mu <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (CTRL + B), birçok temel komut her iki denetim tarafından da desteklenir <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>. Daha fazla bilgi edinmek için bkz. <xref:System.Windows.Documents.EditingCommands>.  
  
 Tarafından desteklenen özellikler <xref:System.Windows.Controls.TextBox> aşağıdaki bölümlerde ele alınmıştır. Hakkında daha fazla bilgi için <xref:System.Windows.Controls.RichTextBox>, bkz: [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md).  
  
### <a name="real-time-spellchecking"></a>Gerçek zamanlı yazım denetimi  
 Gerçek zamanlı yazım etkinleştirebilirsiniz bir <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.RichTextBox>. Yazım denetimi açıldığında, kırmızı bir çizgi (aşağıdaki resme bakın) yanlış yazılmış sözcüklerin altında görüntülenir.  
  
 ![Yazım kutusuyla&#45;denetimi](../../../../docs/framework/wpf/controls/media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 Bkz: [metin düzenleme denetiminde yazım denetimi etkinleştir](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md) nasıl etkinleştirileceğini öğrenin.  
  
### <a name="context-menu"></a>Bağlam menüsü  
 Varsayılan olarak, her ikisi de <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.RichTextBox> kullanıcı içindeki denetim tıkladığında, görünen bağlam menüsüne sahiptir. Bağlam menüsü kesme, kopyalama ve yapıştırma izin verir (aşağıdaki resme bakın).  
  
 ![Bağlam menüsü kutusuyla](../../../../docs/framework/wpf/controls/media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 Varsayılan davranışı geçersiz kılmak için kendi özel bağlam menüsü oluşturabilirsiniz. Bkz: [TextBox ile özel bağlam menüsünü kullanın](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md) daha fazla bilgi için.  
  
<a name="creating_textboxes"></a>   
## <a name="creating-textboxes"></a>Metin kutuları oluşturma  
 A <xref:System.Windows.Controls.TextBox> yükseklik tek bir satırda bulunabilir veya birden çok satırı kapsayabilir. Tek bir satır <xref:System.Windows.Controls.TextBox> küçük miktardaki düz metin (girişleri için en iyisi "Name", "Telefon numarası", bir formda vb.). Aşağıdaki örnek, tek bir satır oluşturmak gösterilmiştir <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 Ayrıca bir <xref:System.Windows.Controls.TextBox> birkaç satırlık metin girmesini sağlar. Örneğin, formunuz kullanıcının biyografik taslağını için sorulursa kullanmak isteyebilirsiniz bir <xref:System.Windows.Controls.TextBox> birkaç satırlık metin destekler. Aşağıdaki örnekte nasıl kullanılacağını gösterir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tanımlamak için bir <xref:System.Windows.Controls.TextBox> birkaç satırlık metin uyum sağlamak için otomatik olarak genişleyen denetim.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 Ayarlama <xref:System.Windows.Controls.TextBox.TextWrapping%2A> özniteliğini `Wrap` yeni bir sarmalamak metin neden ne zaman satır köşesine <xref:System.Windows.Controls.TextBox> denetim ulaşıldığında, otomatik olarak genişleterek <xref:System.Windows.Controls.TextBox> gerektiğinde yeni bir satır için oda dahil denetim.  
  
 Ayarı <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> özniteliğini `true` RETURN tuşuna basıldığında otomatik olarak bir kez yeniden genişletme eklenecek yeni bir satır neden <xref:System.Windows.Controls.TextBox> gerekiyorsa, yeni bir satır için oda eklenecek.  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> Özniteliği için bir kaydırma çubuğunun ekler <xref:System.Windows.Controls.TextBox>, böylece içeriğini <xref:System.Windows.Controls.TextBox> değilse kaydırılabileceğini <xref:System.Windows.Controls.TextBox> çerçeve ya da onu pencere boyutunu genişletir.  
  
 Kullanma ile ilgili farklı görevleri hakkında daha fazla bilgi için bir <xref:System.Windows.Controls.TextBox>, bkz: [nasıl yapılır konuları](../../../../docs/framework/wpf/controls/textbox-how-to-topics.md).  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>İçerik değiştiğinde algılama  
 Genellikle <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay değiştiğinde algılamak için kullanılmalıdır metinde bir <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.RichTextBox> değişiklikler, bunun yerine sonra <xref:System.Windows.UIElement.KeyDown> beklediğiniz gibi. Bkz: [algılamak zaman metinde bir metin kutusu değişti](../../../../docs/framework/wpf/controls/how-to-detect-when-text-in-a-textbox-has-changed.md) bir örnek.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/textbox-how-to-topics.md)  
 [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
