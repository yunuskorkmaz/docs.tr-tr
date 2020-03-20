---
title: İletişim Kutularına Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- modeless dialog boxes [WPF]
- dialog boxes [WPF]
- message boxes [WPF]
- modal dialog boxes [WPF]
ms.assetid: 0d23d544-a393-4a02-a3aa-d8cd5d3d6511
ms.openlocfilehash: c98d6a45d151d4b683a21e48eaeb5f4a19eaadb1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187452"
---
# <a name="dialog-boxes-overview"></a>İletişim kutularına genel bakış
Bağımsız uygulamalar genellikle, hem uygulamanın çalıştığı ana verileri görüntüleyen hem de bu verileri menü [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] çubukları, araç çubukları ve durum çubukları gibi mekanizmalar aracılığıyla işlemek için işlevselliği ortaya çıkaran bir ana pencereye sahiptir. Önemsiz olmayan bir uygulama, aşağıdakileri yapmak için ek pencereler de görüntüleyebilir:  
  
- Belirli bilgileri kullanıcılara görüntüleyin.  
  
- Kullanıcılardan bilgi toplayın.  
  
- Hem görüntüleyebilir hem de bilgi toplayın.  
  
 Bu tür pencereler *iletişim kutuları*olarak bilinir ve iki türü vardır: modal ve modeless.  
  
 İşlevin devam etmesi için kullanıcıdan ek veri gerektiğinde *modal* iletişim kutusu bir işlev tarafından görüntülenir. İşlev veri toplamak için modal iletişim kutusuna bağlı olduğundan, modal iletişim kutusu kullanıcının açık kalırken uygulamadaki diğer pencereleri etkinleştirmesini de engeller. Çoğu durumda, modal iletişim kutusu, bir kullanıcının modal iletişim kutusunu tamam **veya** **iptal** düğmesine basarak işaret etmesini sağlar. **Tamam** düğmesine basıldığında, kullanıcının veri girdiğini ve işlevin bu verilerle işlemeye devam etmesini istediğini gösterir. **İptal** düğmesine basıldığında, kullanıcının işlevin tamamen yürütülmesini durdurmak istediği belirtilir. Modal iletişim kutularının en yaygın örnekleri verileri açmak, kaydetmek ve yazdırmak için gösterilir.  
  
 Diğer taraftan, *modeless* iletişim kutusu, kullanıcının açıkken diğer pencereleri etkinleştirmesini engellemez. Örneğin, bir kullanıcı belgede belirli bir sözcüğün oluşumlarını bulmak isterse, bir ana pencere genellikle bir kullanıcıya hangi sözcüğü aradığını sormak için bir iletişim kutusu açar. Ancak bir sözcük bulmak, kullanıcının belgeyi düzenlemesini engellemediğinden, iletişim kutusunun modal olması gerekmez. Modeless iletişim kutusu en azından iletişim kutusunu kapatmak için **kapat** düğmesi sağlar ve sözcük aramasının bul ölçütlerine uyan bir sonraki sözcüğü bulmak için **Sonrakini Bul** düğmesi gibi belirli işlevleri yürütmek için ek düğmeler sağlayabilir.  
  
 Windows Sunu Temeli (WPF), ileti kutuları, ortak iletişim kutuları ve özel iletişim kutuları da dahil olmak üzere çeşitli iletişim kutuları oluşturmanıza olanak tanır. Bu konu her biri tartışır ve [İletişim Kutusu Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox) eşleşen örnekler sağlar.  

<a name="Message_Boxes"></a>
## <a name="message-boxes"></a>İleti kutuları  
 *İleti kutusu,* metin bilgilerini görüntülemek ve kullanıcıların düğmelerle karar almasına izin vermek için kullanılabilecek bir iletişim kutusudur. Aşağıdaki şekilde metin bilgilerini görüntüleyen, soru soran ve kullanıcıya soruyu yanıtlaması için üç düğme sağlayan bir ileti kutusu görüntülenir.  
  
 ![Uygulama kapanmadan önce belgedeki değişiklikleri kaydetmek isteyip istemediğinizi soran bir Sözcük İşlemci iletişim kutusu.](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 İleti kutusu oluşturmak için <xref:System.Windows.MessageBox> sınıfı kullanırsınız. <xref:System.Windows.MessageBox>aşağıdaki gibi kodu kullanarak ileti kutusu metnini, başlığını, simgesini ve düğmelerini yapılandırmanızı sağlar.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 İleti kutusunu göstermek için, `static` <xref:System.Windows.MessageBox.Show%2A> aşağıdaki kodda gösterildiği gibi yöntemi çağırırsınız.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 İleti kutusunu gösteren kodun kullanıcının kararını algılaması ve işlemesi gerektiğinde (hangi düğmeye basıldı), kod aşağıdaki kodda gösterildiği gibi ileti kutusu sonucunu inceleyebilir.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 İleti kutularını kullanma hakkında <xref:System.Windows.MessageBox>daha fazla bilgi için bkz: [MessageBox Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)ve [İletişim Kutusu Örneği.](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)  
  
 Basit <xref:System.Windows.MessageBox> bir iletişim kutusu kullanıcı deneyimi sunabilir rağmen, kullanmanın <xref:System.Windows.MessageBox> avantajı, xaml tarayıcı uygulamaları (XBAPs) gibi, kısmi [Security](../security-wpf.md)güven güvenlik sandbox içinde çalışan uygulamalar tarafından gösterilebilen tek pencere türüdür.  
  
 Çoğu iletişim kutusu, metin, seçim (onay kutuları), birbirini dışlayan seçim (radyo düğmeleri) ve liste seçimi (liste kutuları, açılan liste kutuları) dahil olmak üzere bir ileti kutusunun sonucundan daha karmaşık verileri görüntüler ve toplar. Bunlar için, Windows Sunu Temeli (WPF) birkaç ortak iletişim kutusu sağlar ve her ikisinin kullanımı tam güvenle çalışan uygulamalarla sınırlı olsa da, kendi iletişim kutularınızı oluşturmanıza olanak tanır.  
  
<a name="Common_Dialogs"></a>
## <a name="common-dialog-boxes"></a>Ortak iletişim kutuları  
 Windows, dosyaları açmak, dosyaları kaydetmek ve yazdırmak için iletişim kutuları da dahil olmak üzere tüm uygulamalarda ortak olan çeşitli yeniden kullanılabilir iletişim kutuları uygular. Bu iletişim kutuları işletim sistemi tarafından uygulandığından, işletim sisteminde çalışan tüm uygulamalar arasında paylaşılabilir, bu da kullanıcının tutarlılığı deneyimlemesine yardımcı olur; Kullanıcılar bir uygulamada işletim sistemi tarafından sağlanan iletişim kutusunun kullanımına aşina olduklarında, diğer uygulamalarda bu iletişim kutusunu nasıl kullanacaklarını öğrenmeleri gerekmez. Bu iletişim kutuları tüm uygulamalar için kullanılabilir olduğundan ve tutarlı bir kullanıcı deneyimi sağlamaya yardımcı olduklarından, *ortak iletişim kutuları*olarak bilinirler.  
  
 Windows Sunu Temeli (WPF), açık dosyayı kapsüller, dosyayı kaydeder ve ortak iletişim kutularını yazdırır ve bunları bağımsız uygulamalarda kullanmanız için yönetilen sınıflar olarak ortaya çıkarır. Bu konu, her biri için kısa bir genel bakış sağlar.  
  
<a name="Open_File_Dialog"></a>
### <a name="open-file-dialog"></a>Dosya iletişim kutusunu aç  
 Aşağıdaki şekilde gösterilen açık dosya iletişim kutusu, açılacak bir dosyanın adını almak için dosya açma işlevi tarafından kullanılır.  
  
 ![Dosyayı almak için konumu gösteren açık iletişim kutusu.](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 Ortak açık dosya iletişim kutusu <xref:Microsoft.Win32.OpenFileDialog> sınıf olarak uygulanır ve <xref:Microsoft.Win32> ad alanında bulunur. Aşağıdaki kod, nasıl oluşturulup, yapılandırışlaştırılatır ve gösterilir ve sonucu nasıl işlenir.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Açık dosya iletişim kutusu hakkında daha <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>fazla bilgi için bkz.  
  
> [!NOTE]
> <xref:Microsoft.Win32.OpenFileDialog>kısmi güvenle çalışan uygulamalara göre dosya adlarını güvenli bir şekilde almak için kullanılabilir (bkz. [Güvenlik).](../security-wpf.md)  
  
<a name="Save_File_Dialog"></a>
### <a name="save-file-dialog-box"></a>Dosya Kaydet iletişim kutusu  
 Aşağıdaki şekilde gösterilen dosyayı kaydet iletişim kutusu, kaydetmek için bir dosyanın adını almak için dosya kaydetme işlevi tarafından kullanılır.  
  
 ![Dosyayı kaydetmek için konumu gösteren Bir Olarak Kaydet iletişim kutusu.](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 Ortak kaydet dosyası iletişim kutusu <xref:Microsoft.Win32.SaveFileDialog> sınıf olarak uygulanır ve <xref:Microsoft.Win32> ad alanında bulunur. Aşağıdaki kod, nasıl oluşturulup, yapılandırışlaştırılatır ve gösterilir ve sonucu nasıl işlenir.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Dosyayı kaydet iletişim kutusunda daha <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>fazla bilgi için bkz.  
  
<a name="Print_Dialog"></a>
### <a name="print-dialog-box"></a>Yazdır iletişim kutusu

Aşağıdaki şekilde gösterilen yazdırma iletişim kutusu, kullanıcının verileri yazdırmak istediği yazıcıyı seçmek ve yapılandırmak için işlevselliği yazdırarak kullanılır.  
  
![Yazdır iletişim kutusunu gösteren ekran görüntüsü.](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
Ortak yazdırma iletişim kutusu <xref:System.Windows.Controls.PrintDialog> sınıf olarak uygulanır ve <xref:System.Windows.Controls> ad alanında bulunur. Aşağıdaki kod, nasıl oluşturulup, yapılandırışlaştırılanın ve bir kodu nasıl göstereceğimi gösterir.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Yazdırma iletişim kutusu hakkında daha fazla <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>bilgi için bkz. WPF'de yazdırma nın ayrıntılı tartışılması için yazdırmaya [genel bakış](../advanced/printing-overview.md)bölümüne bakın.  
  
<a name="Custom_Dialog_Boxes"></a>
## <a name="custom-dialog-boxes"></a>Özel iletişim kutuları

Ortak iletişim kutuları yararlı olsa da ve mümkün olduğunda kullanılması gerekirken, etki alanına özgü iletişim kutularının gereksinimlerini desteklemezler. Bu gibi durumlarda, kendi iletişim kutularınızı oluşturmanız gerekir. Göreceğimiz gibi, iletişim kutusu özel davranışları olan bir penceredir. <xref:System.Windows.Window>bu davranışları uygular ve sonuç olarak, <xref:System.Windows.Window> özel modal ve modeless iletişim kutuları oluşturmak için kullanın.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>
### <a name="creating-a-modal-custom-dialog-box"></a>Modal özel iletişim kutusu oluşturma

Bu konu, örnek <xref:System.Windows.Window> olarak iletişim kutusunu kullanarak tipik bir `Margins` modal iletişim kutusu uygulaması oluşturmak için nasıl kullanılacağını gösterir [(bkz.](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox) İletişim `Margins` kutusu aşağıdaki şekilde gösterilir.  
  
 ![Sol kenar boşluğu, üst kenar boşluğu, sağ kenar boşluğu ve alt kenar boşluğu tanımlamak için alanları olan kenar boşlukları iletişim kutusu.](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a>Modal iletişim kutusunu yapılandırma

Tipik bir iletişim kutusunun kullanıcı arabirimi aşağıdakileri içerir:  
  
- İstenilen verileri toplamak için gereken çeşitli denetimler.  
  
- Kullanıcıların iletişim kutusunu kapatmak, işleve dönmek ve işlemeye devam etmek için tıklattıkları **Tamam** düğmesi.  
  
- Kullanıcıların iletişim kutusunu kapatmak ve işlevin daha fazla işlemesini engellemek için tıklattıkları **İptal** düğmesi.  
  
- Başlık çubuğunda **Kapat** düğmesi.  
  
- Bir simge.  
  
- **Simge durumuna küçültün,** **En Üst Düzeye Çıkarın**ve Düğmeleri Geri **Yükleyin.**  
  
- İletişim kutusunu en aza indirmek, en üst düzeye çıkarmak, geri yüklemek ve kapatmak için **bir Sistem** menüsü.  
  
- İletişim kutusunu açan pencerenin üstünde ve ortasında bir konum.  
  
- İletişim kutusunun çok küçük olmasını önlemek ve kullanıcıya yararlı bir varsayılan boyut sağlamak için mümkün olan yerlerde yeniden boyutlandırılabilme yeteneği. Bu, hem varsayılan hem de minimum boyutları ayarlamanızı gerektirir.  
  
- **İptal** düğmesine basılmasına neden olan klavye kısayolu olarak ESC tuşu. **Bunu, İptal** düğmesinin özelliğini `true` <xref:System.Windows.Controls.Button.IsCancel%2A> ' e ayarlayarak yaparsınız.  
  
- **OK** düğmesine basılmasına neden olan klavye kısayolu olarak ENTER (veya RETURN) tuşu. <xref:System.Windows.Controls.Button.IsDefault%2A> **Tamam** düğmesinin `true`özelliğini ayarlayarak bunu yaparsınız.  
  
Aşağıdaki kod bu yapılandırmayı gösterir.  
  
[!code-xaml[MarginsDialogBox XAML file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,106-112)]  

[!code-csharp[MarginsDialogBox C# code-behind](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-12,67-68)]
[!code-vb[MarginsDialogBox VB code-behind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-11,61-62)]  
  
İletişim kutusu için kullanıcı deneyimi, iletişim kutusunu açan pencerenin menü çubuğuna da uzanır. Bir menü öğesi, işlev devam etmeden önce iletişim kutusu aracılığıyla kullanıcı etkileşimi gerektiren bir işlev çalıştırdığında, işlevin menü öğesinin üstbilgisinde burada gösterildiği gibi bir elips olur.  
  
[!code-xaml[Menu bar of MainWindow.Xaml file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L26-L27)]  
  
Bir menü öğesi, Hakkında iletişim kutusu gibi kullanıcı etkileşimi gerektirmeyen bir iletişim kutusu görüntüleyen bir işlev çalıştırdığında, elips gerekmez.  
  
#### <a name="opening-a-modal-dialog-box"></a>Modal iletişim kutusunu açma

İletişim kutusu genellikle, bir sözcük işlemcisinde belgenin kenar boşluklarını ayarlamak gibi etki alanına özgü bir işlev gerçekleştirmek için bir menü öğesi seçen bir kullanıcı nın sonucu olarak gösterilir. Bir pencereyi iletişim kutusu olarak göstermek, ek iletişim kutusuna özgü yapılandırma gerektirmesine rağmen normal bir pencereyi göstermeye benzer. Bir iletişim kutusunu anlık, yapılandırma ve açma işleminin tamamı aşağıdaki kodda gösterilir.  
  
[!code-csharp[Opening a modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-11,78-88,193-195)]
[!code-vb[Opening a modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58-67,130-132)]  

Burada, kod iletişim kutusuna varsayılan bilgileri (geçerli kenar boşlukları) geçirir. Ayrıca, iletişim <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> kutusunu gösteren pencereye bir başvuru ile özelliği ayarlar. Genel olarak, tüm iletişim kutularında ortak olan pencere durumuyla ilgili davranışları sağlamak için her zaman bir iletişim kutusu sahibini ayarlamanız gerekir (daha fazla bilgi için [WPF Windows Genel Bakış'a](wpf-windows-overview.md) bakın).

> [!NOTE]
> İletişim kutuları için kullanıcı arabirimi (UI) otomasyonunu desteklemek için bir sahip sağlamanız gerekir (bkz. [Kullanıcı Otomasyonu Genel Bakış).](../../ui-automation/ui-automation-overview.md)

İletişim kutusu yapılandırıldıktan sonra, <xref:System.Windows.Window.ShowDialog%2A> yöntem çağırılarak modally gösterilir.  
  
#### <a name="validating-user-provided-data"></a>Kullanıcı tarafından sağlanan verileri doğrulama

Bir iletişim kutusu açıldığında ve kullanıcı gerekli verileri sağladığında, sağlanan verilerin aşağıdaki nedenlerle geçerli olduğundan emin olmak için bir iletişim kutusu sorumludur:  
  
- Güvenlik açısından bakıldığında, tüm girişler doğrulanmalıdır.  
  
- Etki alanına özgü bir bakış açısından, veri doğrulama hatalı verilerin kod tarafından işlenmesini engeller ve bu da özel durumlar yaratabilir.  
  
- Kullanıcı deneyimi açısından bakıldığında, bir iletişim kutusu, girdikleri verilerin geçersiz olduğunu göstererek kullanıcılara yardımcı olabilir.  
  
- Performans açısından bakıldığında, çok katmanlı bir uygulamadaki veri doğrulama, özellikle uygulama Web hizmetleri veya sunucu tabanlı veritabanlarından oluşuyorsa, istemci ve uygulama katmanları arasındaki gidiş-dönüş yolculuklarının sayısını azaltabilir.  

WPF'de bağlı bir denetimi doğrulamak için bir doğrulama kuralı tanımlamanız ve bağlamayla ilişkilendirmeniz gerekir. Doğrulama <xref:System.Windows.Controls.ValidationRule>kuralı, ''den türeyen özel bir sınıftır. Aşağıdaki örnek, `MarginValidationRule`bağlı bir değerin a <xref:System.Double> olduğunu ve belirtilen aralıkta olduğunu denetleyen bir doğrulama kuralını gösterir.  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

Bu kodda, doğrulama kuralının <xref:System.Windows.Controls.ValidationRule.Validate%2A> doğrulama mantığı, verileri doğrulayan ve uygun <xref:System.Windows.Controls.ValidationResult>bir .  

Doğrulama kuralını bağlı denetimle ilişkilendirmek için aşağıdaki biçimlendirmeyi kullanırsınız.  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

Doğrulama kuralı ilişkilendirildiğinde, veriler bağlı denetime girildiğinde WPF otomatik olarak uygular. Denetim geçersiz veri içeriyorsa, WPF aşağıdaki şekilde gösterildiği gibi geçersiz denetimin etrafında kırmızı kenarlık görüntüler.  
  
![Geçersiz sol kenar boşluğu değerinin etrafında kırmızı kenarlıklı kenar boşlukları iletişim kutusu.](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

WPF, geçerli verileri girene kadar kullanıcıyı geçersiz denetimle sınırlamaz. Bu, bir iletişim kutusu için iyi bir davranıştır; bir kullanıcı, verilerin geçerli olup olmadığı bir iletişim kutusundadenetimlerde serbestçe gezinebilir. Ancak, bu, kullanıcının geçersiz veri girebileceği ve **Tamam** düğmesine basabileceği anlamına gelir. Bu nedenle, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> tamam düğmesine olay işleyerek basıldığında **OK** kodunuzun bir iletişim kutusundaki tüm denetimleri doğrulanması gerekir.  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

Bu kod, bir penceredeki tüm bağımlılık nesnelerini sıralar ve varsa geçersizse (döndürülderken, <xref:System.Windows.Controls.Validation.GetHasError%2A>geçersiz `IsValid` denetim `false`odağı alır, yöntem döndürür ve pencere geçersiz kabul edilir.  
  
Bir iletişim kutusu geçerli olduğunda, güvenli bir şekilde kapanıp geri dönebilir. İade işleminin bir parçası olarak, bir sonucu arama işlevine döndürmesi gerekir.  
  
#### <a name="setting-the-modal-dialog-result"></a>Modal iletişim sonucunun ayarlanması

Bir iletişim kutusunu <xref:System.Windows.Window.ShowDialog%2A> kullanarak açmak temelde bir yöntemi çağırmaya benzer: iletişim <xref:System.Windows.Window.ShowDialog%2A> kutusunu <xref:System.Windows.Window.ShowDialog%2A> kullanan kod döndürünceye kadar bekler. Döndürdüğünde, <xref:System.Windows.Window.ShowDialog%2A> kullanıcının **Tamam** düğmesine mi yoksa **İptal düğmesine** mi bastığına bağlı olarak, kodu niçin işleme devam edeceğine yoksa işleme durdurmaya mı karar vermesi gerekir. Bu kararı kolaylaştırmak için iletişim kutusunun yöntemden döndürülen <xref:System.Boolean> bir değer olarak <xref:System.Windows.Window.ShowDialog%2A> kullanıcının seçimini döndürmesi gerekir.  

**Tamam** düğmesi tıklatıldığında, <xref:System.Windows.Window.ShowDialog%2A> geri `true`dönmelidir. Bu, Tamam düğmesi <xref:System.Windows.Window.DialogResult%2A> tıklatıldığında iletişim kutusunun **OK** özelliğini ayarlayarak elde edilir.  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

Özelliği ayarlamanın <xref:System.Windows.Window.DialogResult%2A> pencerenin otomatik olarak kapanmasına da neden olduğunu ve <xref:System.Windows.Window.Close%2A>bunun da açıkça arama gereksinimini azalttı.  
  
**İptal** düğmesi tıklatıldığında, <xref:System.Windows.Window.ShowDialog%2A> özelliği `false`niçin ayarlamayı <xref:System.Windows.Window.DialogResult%2A> da gerektiren döndürmelidir.  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

Bir <xref:System.Windows.Controls.Button.IsCancel%2A> düğmenin özelliği ayarlandığında `true` ve kullanıcı **İptal** düğmesine veya ESC <xref:System.Windows.Window.DialogResult%2A> tuşuna bastığında `false`otomatik olarak . Aşağıdaki biçimlendirme, olayı işlemek için gerek kalmadan, önceki <xref:System.Windows.Controls.Primitives.ButtonBase.Click> kodla aynı etkiye sahiptir.  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

Kullanıcı başlık çubuğundaki `false` **Kapat** düğmesine bastığında veya **Sistem** menüsünden Menü öğesini **kapat'ı** seçtiğinde iletişim kutusu otomatik olarak döner.  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Modal iletişim kutusundan döndürülen verileri işleme  

Bir <xref:System.Windows.Window.DialogResult%2A> iletişim kutusu tarafından ayarlandığında, onu açan işlev döndürdüğünde <xref:System.Windows.Window.DialogResult%2A> <xref:System.Windows.Window.ShowDialog%2A> özelliği inceleyerek iletişim kutusu sonucunu alabilir.  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

İletişim sonucu `true`ise, işlev kullanıcı tarafından sağlanan verileri almak ve işlemek için bir ipucu olarak kullanır.  
  
> [!NOTE]
> Döndürülen bir <xref:System.Windows.Window.ShowDialog%2A> iletişim kutusu yeniden açılamaz. Bunun yerine, yeni bir örnek oluşturmanız gerekir.

İletişim sonucu `false`ise, işlev uygun şekilde işleme son vermelidir.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>
### <a name="creating-a-modeless-custom-dialog-box"></a>Modeless özel iletişim kutusu oluşturma

Aşağıdaki şekilde gösterilen İletişim Kutusunu Bul gibi modeless iletişim kutusu, modal iletişim kutusuyla aynı temel görünüme sahiptir.  

![Bul iletişim kutusunu gösteren ekran görüntüsü.](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

Ancak, davranış, aşağıdaki bölümlerde açıklandığı gibi biraz farklıdır.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Modeless iletişim kutusunu açma

<xref:System.Windows.Window.Show%2A> Yöntem çağırılarak modeless iletişim kutusu açılır.  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  

[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

<xref:System.Windows.Window.ShowDialog%2A>Aksine, <xref:System.Windows.Window.Show%2A> hemen döner. Sonuç olarak, arama penceresi modeless iletişim kutusunun ne zaman kapatıldığında olduğunu söyleyemez ve bu nedenle iletişim kutusu sonucunu ne zaman onaylayıp daha fazla işlem için iletişim kutusundan veri alacağını bilmez. Bunun yerine, iletişim kutusunun verileri işleme için arama penceresine döndürmek için alternatif bir yol oluşturması gerekir.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Modeless iletişim kutusundan döndürülen verileri işleme  

Bu örnekte, `FindDialogBox` belirli bir frekans olmadan aranan metne bağlı olarak, bir veya daha fazla bulma sonucu ana pencereye dönebilir. Modal iletişim kutusunda olduğu gibi, modsuz bir iletişim kutusu özellikleri kullanarak sonuçları döndürebilir. Ancak, iletişim kutusunun sahibi olan pencerenin bu özellikleri ne zaman denetlemesi gerektiğini bilmesi gerekir. Bunu etkinleştirmenin bir yolu, iletişim kutusunun metin bulunduğunda yükseltilen bir olayı uygulamasıdır. `FindDialogBox`öncelikle bir `TextFoundEvent` temsilci gerektiren bu amaç için uygular.  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

Temsilciyi `TextFoundEventHandler` kullanarak, `FindDialogBox` `TextFoundEvent`.
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

Sonuç olarak, `Find` bir arama sonucu bulunduğunda olayı yükseltebilirsiniz.  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

Sahibi penceresi daha sonra bu olayı kaydve işlemek gerekir.

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a>Modeless iletişim kutusunu kapatma

Ayarlanması <xref:System.Windows.Window.DialogResult%2A> gerekmedığından, aşağıdakiler de dahil olmak üzere sistem sağlayan mekanizmalar kullanılarak modeless iletişim kutusu kapatılabilir:  
  
- Başlık çubuğundaki **Kapat** düğmesini tıklatın.  
  
- ALT+F4 tuşuna basArak.  
  
- **Sistem** menüsünden **Kapat'ı** seçme.  
  
Alternatif olarak, **Kapat** <xref:System.Windows.Window.Close%2A> düğmesi tıklandığında kodunuz arayabilir.  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Açılan Pencereye Genel Bakış](../controls/popup-overview.md)
- [İletişim Kutusu Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)
