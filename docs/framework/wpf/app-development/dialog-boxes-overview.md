---
title: İletişim Kutularına Genel Bakış
description: Bilgi toplamak ve göstermek için kullanabileceğiniz Windows Foundation Presentation 'teki (WPF) iletişim kutularının değişen özellikleri hakkında bilgi edinin.
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
ms.openlocfilehash: 822604dd694f2f6260496872fd7a1a8440a62535
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618148"
---
# <a name="dialog-boxes-overview"></a>İletişim kutularına genel bakış
Tek başına uygulamalar genellikle uygulamanın çalıştığı ana verileri görüntüleyen ve [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] menü çubukları, araç çubukları ve durum çubukları gibi mekanizmalarda bu verileri işleme işlevselliğini sunan bir ana pencereye sahiptir. Önemsiz olmayan bir uygulama, aşağıdakileri yapmak için ek pencereler de gösterebilir:  
  
- Kullanıcılara belirli bilgileri görüntüleyin.  
  
- Kullanıcılardan bilgi toplayın.  
  
- Hem görüntü hem de bilgi toplayın.  
  
 Bu tür pencereler *iletişim kutusu*olarak bilinir ve iki tür vardır: kalıcı ve kalıcı.  
  
 İşlevin, bir kullanıcıdan devam etmesi için ek verilere ihtiyacı olduğunda, bir işlev tarafından *kalıcı* iletişim kutusu görüntülenir. İşlev, veri toplamak için kalıcı iletişim kutusuna bağlı olduğundan, kalıcı iletişim kutusu, kullanıcının açık kaldığı sırada uygulamadaki diğer pencereleri etkinleştirmesini de önler. Çoğu durumda, kalıcı iletişim kutusu, bir kullanıcının **Tamam** veya **iptal** düğmesine basarak kalıcı iletişim kutusuyla bitdiklerinde sinyal almasına izin verir. **Tamam** düğmesine basmak, bir kullanıcının veri girdiği ve işlevin bu verilerle işlemeye devam etmesini istediğini gösterir. **İptal** düğmesine basmak, bir kullanıcının işlevin tamamen yürütülmesini durdurmak istediğini gösterir. En yaygın kalıcı iletişim kutusu örnekleri, verileri açmak, kaydetmek ve yazdırmak için gösterilir.  
  
 Diğer yandan *geçici* bir iletişim kutusu, bir kullanıcının açıkken diğer pencereleri etkinleştirmesini engellemez. Örneğin, bir Kullanıcı bir belgedeki belirli bir sözcüğün tekrarlığını bulmak isterse, bir ana pencere genellikle bir iletişim kutusu açar ve bu, kullanıcıya baktıkları kelimeyi ister. Bir sözcüğün bulunması kullanıcının belgeyi düzenlemesini engellemez, ancak iletişim kutusunun kalıcı olması gerekmez. Kalıcı olmayan iletişim kutusu, en azından iletişim kutusunu kapatmak için bir **Kapat** düğmesi sağlar ve bir sözcük aramasının bul ölçütleriyle eşleşen sonraki sözcüğü bulmak Için bir **Sonrakini Bul** düğmesi gibi belirli işlevleri yürütmek için ek düğmeler sağlayabilir.  
  
 Windows Presentation Foundation (WPF) ileti kutuları, ortak iletişim kutuları ve özel iletişim kutuları dahil olmak üzere birkaç iletişim kutusu türü oluşturmanızı sağlar. Bu konuda her biri incelenmektedir ve [Iletişim kutusu örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox) eşleşen örnekler sağlar.  

<a name="Message_Boxes"></a>
## <a name="message-boxes"></a>İleti kutuları  
 *İleti kutusu* , metin bilgilerini göstermek ve kullanıcıların düğmelerle kararlar almasına izin vermek için kullanılabilen bir iletişim kutusudur. Aşağıdaki şekilde, metin bilgisini görüntüleyen, bir soru soran ve kullanıcıya soruyu yanıtlamak için üç düğme sağlayan bir ileti kutusu gösterilmektedir.  
  
 ![Uygulama kapanmadan önce belgedeki değişiklikleri kaydetmek isteyip istemediğinizi soran bir sözcük Işlemcisi iletişim kutusu.](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 İleti kutusu oluşturmak için <xref:System.Windows.MessageBox> sınıfını kullanırsınız. <xref:System.Windows.MessageBox>ileti kutusu metnini, başlığı, simgeyi ve düğmelerini aşağıdaki gibi bir kod kullanarak yapılandırmanıza olanak tanır.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 İleti kutusu görüntülemek için, `static` <xref:System.Windows.MessageBox.Show%2A> aşağıdaki kodda gösterildiği gibi yöntemini çağırın.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 İleti kutusu gösteren kodun, kullanıcının kararlarını algılaması ve işlemesi gerektiğinde (hangi düğmeye basıldığında), kod aşağıdaki kodda gösterildiği gibi ileti kutusu sonucunu inceleyebilir.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 İleti kutularını kullanma hakkında daha fazla bilgi için, bkz <xref:System.Windows.MessageBox> ., [MessageBox örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)ve [iletişim kutusu örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox).  
  
 <xref:System.Windows.MessageBox>Basit bir iletişim kutusu kullanıcı deneyimi sunabilir, ancak kullanmanın avantajı, <xref:System.Windows.MessageBox> bir kısmi güven güvenlik alanı içinde (bkz. [güvenlik](../security-wpf.md)) (örneğin, XAML tarayıcı uygulamaları (XBAP)) çalışan uygulamalar tarafından gösterilebilecek tek bir pencere türüdür.  
  
 Çoğu iletişim kutusu, metin, seçim (onay kutuları), karşılıklı kullanım dışı seçim (radyo düğmeleri) ve liste seçimi (liste kutuları, Birleşik giriş kutuları, açılan liste kutuları) gibi bir ileti kutusunun sonucundan daha karmaşık veriler görüntüler ve toplar. Bunlar için, Windows Presentation Foundation (WPF) birkaç ortak iletişim kutusu sağlar ve bunların kullanımı tam güvenle çalışan uygulamalarla sınırlı olsa da, kendi iletişim kutularınızı oluşturmanızı sağlar.  
  
<a name="Common_Dialogs"></a>
## <a name="common-dialog-boxes"></a>Ortak iletişim kutuları  
 Windows, dosyaları açma, dosyaları kaydetme ve yazdırma iletişim kutuları dahil olmak üzere tüm uygulamalarda ortak olan çeşitli yeniden kullanılabilir iletişim kutularını uygular. Bu iletişim kutuları işletim sistemi tarafından uygulandığından, işletim sistemi üzerinde çalışan tüm uygulamalar arasında paylaşılabilir ve bu da kullanıcı deneyiminin tutarlılığını sağlar; Kullanıcılar bir uygulamada işletim sistemi tarafından sunulan bir iletişim kutusunun kullanımını öğrendiklerinde, bu iletişim kutusunu diğer uygulamalarda nasıl kullanacağınızı öğrenmeleri gerekmez. Bu iletişim kutuları tüm uygulamalar tarafından kullanılabilir olduğundan ve tutarlı bir kullanıcı deneyimi sağlamaya yardımcı olduğundan, bunlar *ortak iletişim kutusu*olarak bilinir.  
  
 Windows Presentation Foundation (WPF), Açık dosyayı kapsüller, dosyayı kaydet ve ortak iletişim kutularını Yazdır ve tek başına uygulamalarda kullanmanız için yönetilen sınıflar olarak kullanıma sunar. Bu konuda, her birine ilişkin kısa bir genel bakış sunulmaktadır.  
  
<a name="Open_File_Dialog"></a>
### <a name="open-file-dialog"></a>Dosya Aç iletişim kutusu  
 Aşağıdaki şekilde gösterilen dosya Aç iletişim kutusu, açılacak dosyanın adını almak için dosya açma işlevi tarafından kullanılır.  
  
 ![Dosyanın alınması için konumu gösteren bir açık iletişim kutusu.](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 Ortak dosya Aç iletişim kutusu sınıf olarak uygulanır <xref:Microsoft.Win32.OpenFileDialog> ve <xref:Microsoft.Win32> ad alanında bulunur. Aşağıdaki kod, bir tane oluşturma, yapılandırma ve gösterme ve sonucun nasıl işlenmesi gerektiğini gösterir.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Dosya Aç iletişim kutusu hakkında daha fazla bilgi için bkz <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType> ..  
  
> [!NOTE]
> <xref:Microsoft.Win32.OpenFileDialog>, kısmi güvenle çalışan uygulamalar tarafından dosya adlarını güvenle almak için kullanılabilir (bkz. [güvenlik](../security-wpf.md)).  
  
<a name="Save_File_Dialog"></a>
### <a name="save-file-dialog-box"></a>Dosya Kaydet iletişim kutusu  
 Aşağıdaki şekilde gösterilen dosya Kaydet iletişim kutusu, kaydedilecek dosyanın adını almak için dosya kaydetme işlevselliği tarafından kullanılır.  
  
 ![Dosyanın kaydedileceği konumu gösteren bir farklı Kaydet iletişim kutusu.](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 Ortak dosya Kaydet iletişim kutusu sınıf olarak uygulanır <xref:Microsoft.Win32.SaveFileDialog> ve <xref:Microsoft.Win32> ad alanında bulunur. Aşağıdaki kod, bir tane oluşturma, yapılandırma ve gösterme ve sonucun nasıl işlenmesi gerektiğini gösterir.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Dosya Kaydet iletişim kutusu hakkında daha fazla bilgi için bkz <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType> ..  
  
<a name="Print_Dialog"></a>
### <a name="print-dialog-box"></a>Yazdır iletişim kutusu

Aşağıdaki şekilde gösterilen Yazdır iletişim kutusu, bir kullanıcının verileri yazdırmak istediğiniz yazıcıyı seçmek ve yapılandırmak için yazdırma işlevselliği tarafından kullanılır.  
  
![Yazdır iletişim kutusunu gösteren ekran görüntüsü.](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
Ortak Yazdır iletişim kutusu sınıf olarak uygulanır <xref:System.Windows.Controls.PrintDialog> ve <xref:System.Windows.Controls> ad alanında bulunur. Aşağıdaki kod, bir tane oluşturma, yapılandırma ve görüntüleme işlemlerinin nasıl yapılacağını gösterir.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Yazdır iletişim kutusu hakkında daha fazla bilgi için bkz <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> .. WPF 'de yazdırmayla ilgili ayrıntılı bilgi için bkz. [yazdırma genel bakış](../advanced/printing-overview.md).  
  
<a name="Custom_Dialog_Boxes"></a>
## <a name="custom-dialog-boxes"></a>Özel iletişim kutuları

Ortak iletişim kutuları yararlı olsa da, mümkün olduğunda kullanılmalıdır, etki alanına özgü iletişim kutularının gereksinimlerini desteklemezler. Bu durumlarda, kendi iletişim kutularınızı oluşturmanız gerekir. Göreceğiniz gibi, bir iletişim kutusu özel davranışları olan bir pencere olur. <xref:System.Windows.Window>Bu davranışları uygular ve sonuç olarak, <xref:System.Windows.Window> özel kalıcı ve kalıcı olmayan iletişim kutuları oluşturmak için kullanırsınız.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>
### <a name="creating-a-modal-custom-dialog-box"></a>Kalıcı özel iletişim kutusu oluşturma

Bu konuda <xref:System.Windows.Window> , bir örnek olarak iletişim kutusunu kullanarak tipik bir kalıcı iletişim kutusu uygulamasının oluşturulması için nasıl kullanılacağı gösterilmektedir `Margins` (bkz. [iletişim kutusu örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)). `Margins`İletişim kutusu aşağıdaki şekilde gösterilmiştir.  
  
 ![Sol kenar boşluğu, üst kenar boşluğu, sağ kenar boşluğu ve alt kenar boşluğu tanımlamak için alanları olan bir kenar boşlukları iletişim kutusu.](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a>Kalıcı iletişim kutusu yapılandırma

Tipik bir iletişim kutusu için Kullanıcı arabirimi şunları içerir:  
  
- İstenen verilerin toplanması için gereken çeşitli denetimler.  
  
- Kullanıcıların iletişim kutusunu kapatmak, işlevine geri dönmesi ve işlemeye devam etmesi için tıklasa **Tamam** düğmesi.  
  
- Kullanıcıların iletişim kutusunu kapatmak ve işlevin daha fazla işlemeden durması için tıklayabilmesini sağlayan bir **iptal** düğmesi.  
  
- Başlık çubuğunda bir **Kapat** düğmesi.  
  
- Bir simge.  
  
- **Küçült**, **Ekranı Kapla**ve **geri yükle** düğmeleri.  
  
- İletişim kutusunu simge durumuna küçültmek, ekranı kaplamak, geri yüklemek ve kapatmak için bir **sistem** menüsü.  
  
- İletişim kutusunu açan pencerenin ortasında ve üzerinde bir konum.  
  
- İletişim kutusunun çok küçük olmasını önleyen ve kullanıcıya yararlı bir varsayılan boyut sağlayan mümkün olduğunda yeniden boyutlandırılabilme özelliği. Bu, hem varsayılan hem de minimum boyutları ayarlamanızı gerektirir.  
  
- ESC tuşu bir klavye kısayolu olarak, **iptal** düğmesine basılmasına neden olur. Bunu <xref:System.Windows.Controls.Button.IsCancel%2A> , **iptal** düğmesinin özelliğini olarak ayarlayarak yapabilirsiniz `true` .  
  
- **Ok** düğmesine basılmasına neden olan bir klavye KıSAYOLU olarak ENTER (veya Return) anahtarı. Bunu, <xref:System.Windows.Controls.Button.IsDefault%2A> **Tamam** düğmesinin özelliğini ayarlayarak yapabilirsiniz `true` .  
  
Aşağıdaki kod bu yapılandırmayı gösterir.  
  
[!code-xaml[MarginsDialogBox XAML file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,106-112)]  

[!code-csharp[MarginsDialogBox C# code-behind](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-12,67-68)]
[!code-vb[MarginsDialogBox VB code-behind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-11,61-62)]  
  
İletişim kutusu için Kullanıcı deneyimi, iletişim kutusunu açan pencerenin menü çubuğuna da genişletilir. Bir menü öğesi, işlev devam etmeden önce bir iletişim kutusu üzerinden kullanıcı etkileşimi gerektiren bir işlevi çalıştırdığında, işlevin menü öğesi, burada gösterildiği gibi üst bilgisinde üç nokta olacak.  
  
[!code-xaml[Menu bar of MainWindow.Xaml file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L26-L27)]  
  
Bir menü öğesi, hakkında iletişim kutusu gibi kullanıcı etkileşimi gerektirmeyen bir iletişim kutusu görüntüleyen bir işlev çalıştırdığında üç nokta gerekli değildir.  
  
#### <a name="opening-a-modal-dialog-box"></a>Kalıcı iletişim kutusu açma

Bir iletişim kutusu tipik olarak, bir kullanıcının, bir sözcük işlemcisinde bir belgenin kenar boşluklarını ayarlama gibi bir menü öğesini seçen bir kullanıcı sonucu olarak gösterilir. Bir pencereyi iletişim kutusu olarak göstermek, normal bir pencerenin gösterilmesine benzer, ancak ek iletişim kutusuna özgü yapılandırma gerektirir. Bir iletişim kutusunun örneğini oluşturma, yapılandırma ve açma işleminin tamamı aşağıdaki kodda gösterilmiştir.  
  
[!code-csharp[Opening a modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-11,78-88,193-195)]
[!code-vb[Opening a modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58-67,130-132)]  

Burada kod, varsayılan bilgileri (geçerli kenar boşlukları) iletişim kutusuna geçirir. Ayrıca, <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> özelliğini iletişim kutusunu gösteren pencereye bir başvuru ile ayarlar. Genel olarak, tüm iletişim kutularında ortak olan pencere durumuyla ilgili davranışları sağlamak için her zaman bir iletişim kutusunun sahibini ayarlamanız gerekir (daha fazla bilgi için bkz. [WPF Windows 'A genel bakış](wpf-windows-overview.md) ).

> [!NOTE]
> İletişim kutuları için Kullanıcı arabirimi (UI) otomasyonunu desteklemek üzere bir sahip sağlamalısınız (bkz. [UI Automation 'A genel bakış](../../ui-automation/ui-automation-overview.md)).

İletişim kutusu yapılandırıldıktan sonra yöntemi çağırarak, bu, bir olarak gösterilir <xref:System.Windows.Window.ShowDialog%2A> .  
  
#### <a name="validating-user-provided-data"></a>Kullanıcı tarafından belirtilen veriler doğrulanıyor

Bir iletişim kutusu açıldığında ve Kullanıcı gerekli verileri sağlıyorsa, sağlanan verilerin aşağıdaki nedenlerle geçerli olduğundan emin olmak için bir iletişim kutusu sorumludur:  
  
- Bir güvenlik perspektifinden, tüm girişlerin doğrulanması gerekir.  
  
- Veri doğrulama, etki alanına özgü bir perspektiften, hatalı verilerin kod tarafından işlenmesini önler, bu durum büyük olasılıkla özel durumlar oluşturabilir.  
  
- Bir kullanıcı deneyimi perspektifinden, bir iletişim kutusu, girdikleri verilerin geçersiz olduğunu göstererek kullanıcılara yardımcı olabilir.  
  
- Bir performans açısından, çok katmanlı bir uygulamadaki veri doğrulaması, özellikle uygulama Web hizmetlerinden veya sunucu tabanlı veritabanlarından oluşturulduğunda istemci ve uygulama katmanları arasındaki gidiş dönüş sayısını azaltabilir.  

WPF 'deki bir bağlama denetimini doğrulamak için bir doğrulama kuralı tanımlamanız ve bağlama ile ilişkilendirmeniz gerekir. Doğrulama kuralı, öğesinden türetilen özel bir sınıftır <xref:System.Windows.Controls.ValidationRule> . Aşağıdaki örnek, bir doğrulama kuralını gösterir, bu `MarginValidationRule` , bir bağlanan değerin bir olduğunu <xref:System.Double> ve belirtilen bir Aralık içinde olduğunu denetler.  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

Bu kodda, bir doğrulama kuralının doğrulama mantığı, <xref:System.Windows.Controls.ValidationRule.Validate%2A> verileri doğrulayan ve uygun bir değer döndüren yöntemi geçersiz kılarak uygulanır <xref:System.Windows.Controls.ValidationResult> .  

Doğrulama kuralını, ilişkili denetimle ilişkilendirmek için aşağıdaki biçimlendirmeyi kullanırsınız.  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

Doğrulama kuralı ilişkilendirildikten sonra WPF, verileri, ilişkili denetime girildiğinde otomatik olarak uygular. Bir denetim geçersiz veri içerdiğinde WPF, aşağıdaki şekilde gösterildiği gibi geçersiz denetim etrafında kırmızı bir kenarlık görüntüler.  
  
![Geçersiz sol kenar boşluğu değeri etrafında kırmızı kenarlığı olan bir kenar boşlukları iletişim kutusu.](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

WPF, geçerli veri girene kadar bir kullanıcıyı geçersiz denetim ile kısıtlayamaz. Bu, iletişim kutusu için iyi bir davranıştır; bir Kullanıcı, verilerin geçerli olup olmadığını bir iletişim kutusunda serbestçe gezinebilmelidir. Ancak bu, bir kullanıcının geçersiz veri girebileceği ve **Tamam** düğmesine basması anlamına gelir. Bu nedenle, kodunuzun aynı zamanda olayı işleyerek **Tamam** düğmesine basıldığında bir iletişim kutusundaki tüm denetimleri doğrulaması gerekir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

Bu kod, bir penceredeki tüm bağımlılık nesnelerini numaralandırır ve eğer varsa, <xref:System.Windows.Controls.Validation.GetHasError%2A> Geçersiz denetim odağı alır, `IsValid` Yöntem döner `false` ve pencere geçersiz olarak kabul edilir.  
  
İletişim kutusu geçerli olduğunda, güvenli bir şekilde kapatılabilir ve dönebilir. Döndürülen işlemin bir parçası olarak, çağıran işleve bir sonuç döndürmesi gerekir.  
  
#### <a name="setting-the-modal-dialog-result"></a>Kalıcı iletişim kutusu sonucunu ayarlama

Kullanarak bir iletişim kutusu açmak <xref:System.Windows.Window.ShowDialog%2A> , bir yöntemi çağırmak gibidir: iletişim kutusunu açan kod, <xref:System.Windows.Window.ShowDialog%2A> <xref:System.Windows.Window.ShowDialog%2A> dönüşene kadar bekler. <xref:System.Windows.Window.ShowDialog%2A>' İ döndüğünde, kullanıcının **Tamam** düğmesine veya **iptal** düğmesine bastığına bağlı olarak, bu dosyayı çağıran kodun işlemeye veya durdurulmasına devam edip etmeyeceğine karar sağlaması gerekir. Bu kararı kolaylaştırmak için, iletişim kutusunun yönteminden döndürülen bir değer olarak kullanıcının seçeneğini döndürmesi gerekir <xref:System.Boolean> <xref:System.Windows.Window.ShowDialog%2A> .  

**Tamam** düğmesine tıklandığında, <xref:System.Windows.Window.ShowDialog%2A> döndürmelidir `true` . Bu, <xref:System.Windows.Window.DialogResult%2A> **Tamam** düğmesine tıklandığında iletişim kutusunun özelliği ayarlanarak elde edilir.  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

<xref:System.Windows.Window.DialogResult%2A>Özelliği ayarlamanın Ayrıca pencerenin otomatik olarak kapatılmasına neden olduğunu unutmayın, bu da açıkça çağrı yapması gerekir konuma almayı azaltır <xref:System.Windows.Window.Close%2A> .  
  
**İptal** düğmesine tıklandığında, <xref:System.Windows.Window.ShowDialog%2A> `false` özelliği de ayarlamayı gerektiren döndürmelidir <xref:System.Windows.Window.DialogResult%2A> .  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

Bir düğmenin <xref:System.Windows.Controls.Button.IsCancel%2A> özelliği olarak ayarlandığında `true` ve Kullanıcı **Iptal** düğmesine veya ESC tuşuna basarsa, <xref:System.Windows.Window.DialogResult%2A> otomatik olarak olarak ayarlanır `false` . Aşağıdaki biçimlendirme, olayı işlemeye gerek olmadan Yukarıdaki kodla aynı etkiye sahiptir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

Bir `false` Kullanıcı başlık çubuğundaki **Kapat** düğmesine bastığında veya **sistem** menüsünden **Kapat** menü öğesini seçtiğinde bir iletişim kutusu otomatik olarak döner.  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Kalıcı iletişim kutusundan döndürülen verileri işleme  

<xref:System.Windows.Window.DialogResult%2A>Bir iletişim kutusu tarafından ayarlandığında, onu açan işlev, döndüğünde özelliği inceleyerek iletişim kutusu sonucunu alabilir <xref:System.Windows.Window.DialogResult%2A> <xref:System.Windows.Window.ShowDialog%2A> .  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

İletişim kutusu sonucu ise `true` , işlev kullanıcı tarafından belirtilen verileri almak ve işlemek için bir ipucu olarak kullanır.  
  
> [!NOTE]
> <xref:System.Windows.Window.ShowDialog%2A>Geri döntikten sonra bir iletişim kutusu yeniden açılamaz. Bunun yerine, yeni bir örnek oluşturmanız gerekir.

İletişim kutusu sonucu ise `false` , işlev işlemeyi uygun şekilde sonlandırmalıdır.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>
### <a name="creating-a-modeless-custom-dialog-box"></a>Kalıcı olmayan özel iletişim kutusu oluşturma

Aşağıdaki şekilde gösterilen bul Iletişim kutusu gibi kalıcı olmayan bir iletişim kutusu, kalıcı iletişim kutusuyla aynı temel görünüme sahiptir.  

![Bir bul iletişim kutusunu gösteren ekran görüntüsü.](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

Ancak, aşağıdaki bölümlerde açıklandığı gibi davranış biraz farklıdır.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Kalıcı olmayan iletişim kutusu açma

Yöntemi çağırarak kalıcı olmayan bir iletişim kutusu açılır <xref:System.Windows.Window.Show%2A> .  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  

[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

Aksine <xref:System.Windows.Window.ShowDialog%2A> , <xref:System.Windows.Window.Show%2A> hemen döndürür. Sonuç olarak, geçici pencere kalıcı iletişim kutusu kapalıyken ve bu nedenle, bir iletişim kutusu sonucunu ne zaman denetleyeceğinizi veya daha fazla işleme için iletişim kutusunda veri almayı bilmez. Bunun yerine, iletişim kutusunun işleme için verileri çağıran pencereye döndürmesi için alternatif bir yol oluşturması gerekir.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Kalıcı olmayan iletişim kutusundan döndürülen verileri işleme  

Bu örnekte, `FindDialogBox` belirli bir sıklık olmadan aranan metne bağlı olarak ana pencereye bir veya daha fazla arama sonucu döndürebilir. Kalıcı iletişim kutusunda olduğu gibi, kalıcı olmayan bir iletişim kutusu, özellikleri kullanarak sonuçlar döndürebilir. Ancak, iletişim kutusunun sahibi olan pencere, bu özellikleri ne zaman denetleyeceğinizi bilmelidir. Bunu etkinleştirmenin bir yolu, iletişim kutusunun metin bulunduğunda oluşturulan bir olayı uygulaması için kullanılır. `FindDialogBox``TextFoundEvent`öncelikle bir temsilci gerektiren bu amaçla uygular.  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

Temsilciyi kullanarak, `TextFoundEventHandler` öğesini `FindDialogBox` uygular `TextFoundEvent` .
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

Sonuç olarak, `Find` bir arama sonucu bulunduğunda olayı oluşturabilir.  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

Daha sonra sahip penceresinin bu olayı ile kaydetmesi ve işlemesi gerekir.

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a>Kalıcı olmayan iletişim kutusu kapatılıyor

<xref:System.Windows.Window.DialogResult%2A>Ayarlanması gerekmeyen için, aşağıdakiler de dahil olmak üzere sistem sağlama mekanizmaları kullanılarak kalıcı olmayan bir iletişim kutusu kapatılabilir:  
  
- Başlık çubuğundaki **Kapat** düğmesine tıklanın.  
  
- ALT + F4 tuşlarına basın.  
  
- **Sistem** menüsünden **Kapat** seçeneğini belirleme.  
  
Alternatif olarak, <xref:System.Windows.Window.Close%2A> **Kapat** düğmesine tıklandığında kodunuz da çağırabilir.  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Açılır Pencereye Genel Bakış](../controls/popup-overview.md)
- [İletişim kutusu örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/DialogBox)
