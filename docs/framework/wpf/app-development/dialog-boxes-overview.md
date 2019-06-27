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
ms.openlocfilehash: 8008feb91a72353a74a647cf79bcecbf7023f962
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410552"
---
# <a name="dialog-boxes-overview"></a>İletişim kutularına genel bakış
Tek başına uygulamalar genellikle her ikisi de, uygulama üzerinden çalışır ve aracılığıyla bu verileri işlemek için işlevselliği kullanıma sunma ana verileri görüntüler ana pencere sahip [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] mekanizmaları menü çubukları, araç çubuklarını ve durum çubukları ister. Önemsiz olmayan bir uygulama, ayrıca aşağıdakileri yapmak için ek windows görüntülenebilir:  
  
- Belirli bilgiler, kullanıcılara görüntülenir.  
  
- Kullanıcılardan bilgi toplayın.  
  
- Hem görüntülemek ve bilgi toplayın.  
  
 Windows bu tür olarak da bilinir *iletişim kutuları*, ve iki tür vardır: kalıcı ve kalıcı olmayan.  
  
 A *kalıcı* işlevi devam etmek için kullanıcıdan ek verilere ihtiyaç duyduğunda işlev tarafından iletişim kutusu görüntülenir. Veri toplamak üzere kalıcı bir iletişim kutusunda işlevi bağlı olduğundan, kalıcı bir iletişim kutusu açık kaldığı sürece uygulamadaki diğer windows etkinleştirme bir kullanıcı da engeller. Çoğu durumda, kalıcı bir iletişim kutusu ya da tuşlarına basarak kalıcı bir iletişim kutusuyla tamamladıktan sonra sinyal açmasına olanak sağlar. bir **Tamam** veya **iptal** düğmesi. Tuşuna basarak **Tamam** düğmesini gösteren bir kullanıcı veri geçtiğini ve işlev veri işleme devam etmek istiyor. Tuşuna basarak **iptal** düğmesini gösteren bir kullanıcı işlevi tamamen yürütülmesini durdurmak istiyor. Kalıcı iletişim kutuları en yaygın örnekleri açın, kaydedin ve veri yazdırma gösterilir.  
  
 A *geçici* iletişim kutusu, diğer taraftan, engellemez kullanıcı açıkken diğer windows etkinleştirme. Örneğin, bir kullanıcı bir belgedeki belirli bir sözcüğün oluşumlarını bulmak isterse, ana pencere genellikle aradıklarını hangi word kullanıcıdan bir iletişim kutusu açılır. Bu yana bulma bir word belgesi düzenlemesini kullanıcı engellemez, ancak iletişim kutusunun kalıcı olması gerekmez. En az bir modsuz iletişim kutusu sağlayan bir **kapatmak** iletişim kutusunu kapatmak için düğme ve ek düğmeler gibi belirli İşlevler, yürütülecek sağlayabilir bir **Sonrakini Bul** Sonrakini Bul düğmesini, word bulma ölçütleri sözcük araması eşleşir.  
  
 Windows Presentation Foundation (WPF), birden fazla ileti kutuları, ortak iletişim kutuları ve özel iletişim kutuları gibi iletişim kutularına oluşturmanıza olanak sağlar. Bu konu, her açıklar ve [iletişim kutusu örnek](https://go.microsoft.com/fwlink/?LinkID=159984) eşleşen örnekler sağlar.  

<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a>İleti kutuları  
 A *ileti kutusu* metinsel bilgilerini görüntülemek ve kullanıcıların düğmelerle kararlar izin vermek için kullanılan bir iletişim kutusudur. Aşağıdaki şekil, metin tabanlı bilgiler görüntüler, soru soran ve kullanıcının soruyu yanıtlamak için üç düğme sağlayan bir ileti kutusu gösterir.  
  
 ![Belgeyi uygulama önce değişiklikleri kaydetmek isteyip istemediğinizi soran bir sözcük işlemcisi iletişim kutusu kapanır.](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 Bir ileti kutusu oluşturmak için kullandığınız <xref:System.Windows.MessageBox> sınıfı. <xref:System.Windows.MessageBox> ileti kutusu metni, başlık, simge ve düğmeler, aşağıdaki gibi bir kod kullanarak yapılandırmanıza olanak sağlar.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 Bir ileti kutusu görüntülemek için çağrı `static` <xref:System.Windows.MessageBox.Show%2A> yöntemi, aşağıdaki kodda gösterildiği gibi.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 Bir ileti kutusu gösteren kod algılamak ve (hangi düğmeye basıldığını) kullanıcının karar işleme gerektiğinde, aşağıdaki kodda gösterildiği gibi kod ileti kutusu sonucu inceleyebilirsiniz.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 İleti kutuları kullanma hakkında daha fazla bilgi için bkz. <xref:System.Windows.MessageBox>, [MessageBox örnek](https://go.microsoft.com/fwlink/?LinkID=160023), ve [iletişim kutusu örnek](https://go.microsoft.com/fwlink/?LinkID=159984).  
  
 Ancak <xref:System.Windows.MessageBox> kullanmanın avantajı bir basit iletişim kutusunda kullanıcı deneyimi sunabilir <xref:System.Windows.MessageBox> kısmi güven güvenliği korumalı alan içinde çalışan uygulamalar tarafından gösterilebilir penceresinin tek tür olduğu (bkz [güvenlik](../security-wpf.md)), aşağıdakiler gibi [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
 Çoğu iletişim kutusu görüntülemek ve metin seçimi (onay kutuları) birbirini dışlayan seçimi (radyo düğmeleri) dahil olmak üzere bir ileti kutusu sonucu değerinden daha karmaşık veri toplamak ve seçimi (liste kutuları, birleşik giriş kutuları, açılan liste kutuları) listesi. Bu, Windows Presentation Foundation (WPF) birkaç ortak iletişim kutusu sağlar ve kullanımı ya da tam güvenle çalışan uygulamalar için sınırlı olmasına karşın, kendi iletişim kutuları oluşturmanıza olanak sağlar.  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a>Ortak iletişim kutuları  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] dosyaları kaydetme ve yazdırma dosyaları açma, iletişim kutularını dahil olmak üzere tüm uygulamalar için ortak olan yeniden kullanılabilir iletişim kutuları çeşitli uygular. Bu iletişim kutularından işletim sistemi tarafından uygulanan olduğundan, kullanıcı deneyimini tutarlılık yardımcı olan işletim sistemi üzerinde çalıştırılan tüm uygulamalar arasında paylaşılabilir; Kullanıcılar, bir işletim sistemi tarafından sağlanan bir iletişim kutusu, bir uygulamada kullanımını bilginiz, diğer uygulamalarda bu iletişim kutusunu kullanma hakkında bilgi edinmek gerekmez. Bu iletişim kutularından tüm uygulamalar için kullanılabilir olduğundan ve tutarlı bir kullanıcı deneyimi sağlamaya yardımcı olduğundan, bunlar olarak bilinir *ortak iletişim kutuları*.  
  
 Windows Presentation Foundation (WPF) açık dosyanın kapsüller, dosyayı kaydedin ve yazdırma ortak iletişim kutuları ve bunları olarak yönetilen tek başına uygulamalarda kullanabilmeniz için sınıflar çıkarır. Bu konu, her kısa bir genel bakış sağlar.  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a>Dosya Aç iletişim kutusu  
 Aşağıdaki şekilde gösterilen Dosya Aç iletişim kutusu açmak için bir dosya adını almak için işlevselliği açma dosya tarafından kullanılır.  
  
 ![Dosya alma konumu gösteren bir açık iletişim kutusu.](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 Ortak bir dosya Aç iletişim kutusu olarak uygulanan <xref:Microsoft.Win32.OpenFileDialog> sınıfı ve bulunan <xref:Microsoft.Win32> ad alanı. Aşağıdaki kod oluşturma, yapılandırma ve bir Göster ve sonuçları işlemek nasıl gösterir.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 Dosya Aç iletişim kutusu hakkında daha fazla bilgi için bkz. <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>.  
  
> [!NOTE]
>  <xref:Microsoft.Win32.OpenFileDialog> güvenli bir şekilde dosya adları almak için kısmi güven ile çalışan uygulamalar tarafından kullanılabilir (bkz [güvenlik](../security-wpf.md)).  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a>Dosya Kaydet iletişim kutusu  
 Kaydetme dosya iletişim kutusunda, aşağıdaki şekilde gösterildiği işlevleri kaydetme dosyasıyla kaydetmek için bir dosya adını almak için kullanılır.  
  
 ![Dosyanın kaydedileceği konumu gösteren Farklı Kaydet iletişim kutusu.](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 Dosya iletişim kutusu kaydetme yaygın olarak uygulanan <xref:Microsoft.Win32.SaveFileDialog> sınıfı ve bulunan <xref:Microsoft.Win32> ad alanı. Aşağıdaki kod oluşturma, yapılandırma ve bir Göster ve sonuçları işlemek nasıl gösterir.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 Kaydetme hakkında daha fazla bilgi için bkz, dosya iletişim kutusu <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>.  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a>Yazdır iletişim kutusu

Aşağıdaki şekilde gösterilen yazdırma iletişim kutusunda, seçmek ve kullanıcı verilerini yazdırmak istediğiniz yazıcı için yazdırma işlevselliği tarafından kullanılır.  
  
![Yazdır iletişim kutusunu gösteren ekran görüntüsü.](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
Ortak bir yazdırma iletişim kutusu olarak uygulanan <xref:System.Windows.Controls.PrintDialog> sınıfı ve bulunan <xref:System.Windows.Controls> ad alanı. Aşağıdaki kod, oluşturma, yapılandırma ve bir Göster gösterilmektedir.  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 Yazdırma iletişim kutusu hakkında daha fazla bilgi için bkz. <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>. Yazdırma ' WPF'de hakkında ayrıntılı bilgi için bkz. [yazdırma genel bakış](../advanced/printing-overview.md).  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a>Özel iletişim kutuları

Ortak iletişim kutuları yararlıdır ve mümkün olduğunda kullanılmalıdır, ancak etki alanına özgü iletişim kutuları gereksinimlerini desteklemez. Bu durumlarda, kendi iletişim kutuları oluşturmanız gerekir. Anlatıldığı gibi bir iletişim kutusu ile özel davranışları penceredir. <xref:System.Windows.Window> Bu davranışları uygular ve bu nedenle, kullandığınız <xref:System.Windows.Window> özel kalıcı ve kalıcı olmayan iletişim kutuları oluşturmak için.  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a>Özel bir kalıcı iletişim kutusu oluşturma

Bu konu nasıl kullanılacağını gösterir <xref:System.Windows.Window> tipik kalıcı bir iletişim kutusu uygulamasını kullanarak `Margins` iletişim kutusu örnek olarak (bkz [iletişim kutusu örnek](https://go.microsoft.com/fwlink/?LinkID=159984)). `Margins` İletişim kutusunda, aşağıdaki şekilde gösterilmiştir.  
  
 ![Sol kenar boşluğu, üst kenar boşluğu, sağ kenar boşluğu ve alt kenar boşluğu tanımlamak için kullanılan alanları içeren bir kenar boşlukları iletişim kutusu.](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a>Kalıcı bir iletişim kutusu yapılandırma

Kullanıcı arabirimi için genel iletişim kutusunda, aşağıdakileri içerir:  
  
- İstenen veri toplamak için gereken çeşitli denetimler.  
  
- Bir **Tamam** kullanıcılar işlevi için dönüş iletişim kutusunu kapatın ve işleme devam düğmesi.  
  
- A **iptal** düğme iletişim kutusunu kapatın ve daha fazla işleme gelen işlevi durdurmak için kullanıcılar'ı tıklatın.  
  
- A **Kapat** başlık çubuğunda düğme.  
  
- Bir simge.  
  
- **Simge Durumuna Küçült**, **Ekranı Kapla**, ve **geri** düğmeleri.  
  
- A **sistem** menüsünde en aza indirmek, en üst düzeye çıkarmak, geri yükleme ve iletişim kutusunu kapatın.  
  
- Yukarıda ve iletişim kutusu açılır pencerenin ortasına konumu.  
  
- Mümkün olduğunda iletişim kutusunu önlemek çok küçük ve kullanışlı varsayılan boyutunda kullanıcı sağlamayı boyutlandırılmaya yeteneği. Bu, hem varsayılan hem de en az bir boyutlar kümesi gerektirir.  
  
- ESC tuşuna neden olan bir klavye kısayolu **iptal** düğmesine basıldığında. Ayarlayarak bunu <xref:System.Windows.Controls.Button.IsCancel%2A> özelliği **iptal** düğmesi `true`.  
  
- ENTER'ı (ya da RETURN) anahtar neden olan bir klavye kısayolu olarak **Tamam** düğmesine basıldığında. Ayarlayarak bunu <xref:System.Windows.Controls.Button.IsDefault%2A> özelliği **Tamam** düğmesi `true`.  
  
Aşağıdaki kod, bu yapılandırma gösterilmektedir.  
  
[!code-xaml[MarginsDialogBox XAML file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,106-112)]  

[!code-csharp[MarginsDialogBox C# code-behind](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-12,67-68)]
[!code-vb[MarginsDialogBox VB code-behind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-11,61-62)]  
  
Bir iletişim kutusu için kullanıcı deneyimi de iletişim kutusu açılır pencere menü çubuğuna genişletir. Bir menü öğesi işlevi devam etmeden önce bir iletişim kutusu aracılığıyla kullanıcı etkileşimi gerektiren bir işlev çalıştığında, işlev için menü öğesi üç nokta üstbilgisinde, burada gösterildiği gibi olacaktır.  
  
[!code-xaml[Menu bar of MainWindow.Xaml file](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L26-L27)]  
  
Bir menü öğesi gibi bir hakkında iletişim kutusunda, kullanıcı etkileşimi gerektirmeyen bir iletişim kutusu görüntüleyen bir işlev çalıştığında, üç nokta gerekli değildir.  
  
#### <a name="opening-a-modal-dialog-box"></a>Kalıcı iletişim kutusu açılıyor

Bir iletişim kutusu, genellikle bir sözcük işlemcisi bir belgenin kenar boşluklarını ayarlama gibi bir etki alanına özgü işlevi gerçekleştirmek için bir kullanıcı bir menü öğesi seçilerek sonucu olarak gösterilir. Ek iletişim kutusu özgü yapılandırma gerektirse de gösteren bir pencere bir iletişim kutusu olarak normal bir pencere gösterecek şekilde benzerdir. Örnekleme tüm işlemi, yapılandırma ve iletişim kutusunu açıp aşağıdaki kodda gösterilmektedir.  
  
[!code-csharp[Opening a modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-11,78-88,193-195)]
[!code-vb[Opening a modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58-67,130-132)]  

Burada, kod iletişim kutusuna varsayılan bilgi (geçerli kenar boşluğu) geçirir. Ayrıca ayarlar <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> özelliği ile bir iletişim kutusunu gösteren pencere başvurusu. Genel olarak, her zaman tüm iletişim kutularındaki ortak pencere durumu ile ilgili davranışları sağlamak için bir iletişim kutusu sahibi ayarlamanız gerekir (bkz [WPF Windows genel bakış](wpf-windows-overview.md) daha fazla bilgi için).

> [!NOTE]
> İletişim kutuları için kullanıcı arabirimi (UI) otomasyonunu desteklemek için bir sahip sağlamanız gerekir (bkz [UI otomasyonuna genel bakış](../../ui-automation/ui-automation-overview.md)).

İletişim kutusu yapılandırıldıktan sonra kalıcı olarak çağrılarak gösterilen <xref:System.Windows.Window.ShowDialog%2A> yöntemi.  
  
#### <a name="validating-user-provided-data"></a>Kullanıcı tarafından sağlanan verileri doğrulama

Bir iletişim kutusu açılır ve kullanıcının gerekli verileri sağlar, bir iletişim kutusu aşağıdaki nedenlerle sağlanan veriler geçersiz olduğundan emin olmakta sorumludur:  
  
- Güvenlik açısından bakıldığında, tüm giriş doğrulanması gerekir.  
  
- Etki alanına özgü açısından bakıldığında, veri doğrulama, hatalı verilerin olası özel durumlarını oluşturabilir kod tarafından işlenen engeller.  
  
- Bir kullanıcı deneyimi açısından bakıldığında, bir iletişim kutusu hangi verileri girdikleri geçersiz göstererek kullanıcılara yardımcı olabilirsiniz.  
  
- Özellikle uygulama Web Hizmetleri veya sunucu tabanlı veritabanları oluşturulduğunda performans açısından bakıldığında, çok katmanlı bir uygulama içinde veri doğrulama istemci ve uygulama katmanları arasındaki gidiş dönüş sayısını azaltabilir.  

İlişkili bir WPF denetiminde doğrulamak için bir doğrulama kuralını tanımlamak ve bağlama ile ilişkilendirmeniz gerekir. Bir doğrulama kuralı öğesinden türetilen özel bir sınıftır <xref:System.Windows.Controls.ValidationRule>. Aşağıdaki örnek, bir doğrulama kuralı gösterir `MarginValidationRule`, ilişkili bir değer hangi denetimleri bir <xref:System.Double> ve belirlenen aralık dahilinde.  

[!code-csharp[Margin validation rules](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs)]
[!code-vb[Margin validation rules](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb)]  

Bu kodda bir doğrulama kuralını doğrulama mantığını geçersiz kılarak uygulanan <xref:System.Windows.Controls.ValidationRule.Validate%2A> verileri doğrular ve uygun bir döndüren yöntemi <xref:System.Windows.Controls.ValidationResult>.  

Doğrulama kuralı ile ilişkili denetim ilişkilendirmek için aşağıdaki biçimlendirme kullanın.  
  
[!code-xaml[Associating a validation rule with a control](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml?range=1-16,57-68,111-112)]

Doğrulama kuralı ilişkilendirildikten sonra veri ilişkili denetime girildiğinde WPF bunu otomatik olarak uygulanır. WPF denetim geçersiz veri içeriyorsa, geçersiz denetimin etrafında kırmızı bir kenarlık aşağıdaki şekilde gösterildiği gibi görüntülenir.  
  
![Geçersiz sol kenar boşluğu değeri etrafında kırmızı bir kenarlık bir kenar boşlukları iletişim kutusu.](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  

WPF geçerli verileri girdikleri kadar bir kullanıcı için geçersiz denetim kısıtlamaz. Bir iletişim kutusu için iyi davranışı budur; bir kullanıcının veri geçerli olup olmadığını bir iletişim kutusu denetimleri serbestçe gidebilirsiniz olması gerekir. Ancak, bir kullanıcı, geçersiz veri ve ENTER tuşuna girebilirsiniz yani **Tamam** düğmesi. Bu nedenle, kodunuzu ayrıca bir iletişim kutusu içindeki tüm denetimler doğrulamak gereken kutusunu **Tamam** işleyerek düğmesine basıldığında <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.  
  
[!code-csharp[Validating all controls in a dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,26-29,33-68)]
[!code-vb[Validating all controls in a dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27-29,33-62)]  

Bu kod bir penceredeki tüm bağımlılık nesneleri numaralandırır ve geçersiz olduğunda (tarafından döndürülen <xref:System.Windows.Controls.Validation.GetHasError%2A>, geçersiz denetim odağı alır `IsValid` yöntemi döndürür `false`, ve pencerenin geçersiz olarak kabul edilir.  
  
Bir iletişim kutusu geçerli olduğunda, onu güvenli bir şekilde kapatın dönün ve. İade işleminin bir parçası olarak, çağıran işleve bir sonuç döndürmesi gerekir.  
  
#### <a name="setting-the-modal-dialog-result"></a>Kalıcı iletişim kutusu sonucu ayarlama

İletişim kutusunu kullanarak açma <xref:System.Windows.Window.ShowDialog%2A> olan temelde bir yöntemi çağırmak gibi: açılan iletişim kutusunu kullanarak kod <xref:System.Windows.Window.ShowDialog%2A> kadar bekler <xref:System.Windows.Window.ShowDialog%2A> döndürür. Zaman <xref:System.Windows.Window.ShowDialog%2A> döndürür, işleme devam etmek için işleme, Durdur bağlı olup olmadığını karar vermek için ihtiyaçlarını adlı kod kullanıcı basılı **Tamam** düğmesini veya **iptal** düğmesi. Bu kararı kolaylaştırmak için kullanıcının seçenek olarak döndürülecek iletişim kutusunu gereken bir <xref:System.Boolean> öğesinden döndürülen değer <xref:System.Windows.Window.ShowDialog%2A> yöntemi.  

Zaman **Tamam** düğmesine tıklandığında, <xref:System.Windows.Window.ShowDialog%2A> döndürmelidir `true`. Bu ayarı gerçekleştirilir <xref:System.Windows.Window.DialogResult%2A> özelliği iletişim kutusu **Tamam** düğmesine tıklandığında.  

[!code-csharp[Responding to the OK button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,25-27,32-33,67-68)]
[!code-vb[Responding to the OK button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,27,31-33,61-62)]  

Bu ayarı Not <xref:System.Windows.Window.DialogResult%2A> özelliği de penceresi otomatik olarak kapatmak, açıkça çağırma ihtiyacını neden <xref:System.Windows.Window.Close%2A>.  
  
Zaman **iptal** düğmesine tıklandığında, <xref:System.Windows.Window.ShowDialog%2A> döndürmelidir `false`, gerektiren ayarı <xref:System.Windows.Window.DialogResult%2A> özelliği.  
  
[!code-csharp[Responding to the Cancel button](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs?range=1-8,19-24,67-68)]
[!code-vb[Responding to the Cancel button](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb?range=1-8,22-25,61-62)]  

Bir düğme ayarlandığında <xref:System.Windows.Controls.Button.IsCancel%2A> özelliği `true` ve ya da kullanıcı **iptal** düğme veya ESC tuşuna <xref:System.Windows.Window.DialogResult%2A> otomatik olarak ayarlandığından `false`. Aşağıdaki biçimlendirmede işlemek zorunda kalmadan projeler yukarıdaki kodla aynı etkiye sahip <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.  
  
[!code-xaml[Markup instead of handling the Click event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#L109-L109)]  

Bir iletişim kutusu otomatik olarak döndürür `false` kullanıcının bastığında **Kapat** düğme başlık çubuğunda veya seçer **Kapat** menü öğesi **sistem** menüsü.  

#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Bir kalıcı iletişim kutusundan dönen veri işleme  

Zaman <xref:System.Windows.Window.DialogResult%2A> ayarlanmış bir iletişim kutusu, bu işlev iletişim kutusu sonucu inceleyerek alabilirsiniz <xref:System.Windows.Window.DialogResult%2A> özelliği olduğunda <xref:System.Windows.Window.ShowDialog%2A> döndürür.  
  
[!code-csharp[Processing data returned from the modal dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,77-79,89-96,194-195)]
[!code-vb[Processing data returned from the modal dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,58,69-73,131-132)]

İletişim sonucu ise `true`, işlev, bir ipucu olarak almak ve kullanıcı tarafından sağlanan verileri işlemek için kullanır.  
  
> [!NOTE]
> Sonra <xref:System.Windows.Window.ShowDialog%2A> döndürdü, bir iletişim kutusu açılamaz. Bunun yerine, yeni bir örneğini oluşturmanız gerekir.

İletişim sonucu ise `false`, işlev uygun şekilde işleme bitmelidir.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>Özel modsuz iletişim kutusu oluşturma

Modsuz iletişim kutusu, Bul iletişim kutusunu aşağıdaki şekilde gösterildiği gibi aynı temel görünüm kalıcı bir iletişim kutusu vardır.  

![Bul iletişim kutusunu gösteren ekran görüntüsü.](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  

Ancak, aşağıdaki bölümlerde açıklandığı gibi biraz daha farklı, davranıştır.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Kalıcı olmayan iletişim kutusu açılıyor

Çağırarak modsuz iletişim kutusu açıldığında <xref:System.Windows.Window.Show%2A> yöntemi.  

[!code-xaml[XAML to define a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#L21-L22)]  
 
[!code-csharp[Opening a modeless dialog box](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,65-76,194-195)]
[!code-vb[Openng a modeless dialog box](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,18-23,131,132)]  

Farklı <xref:System.Windows.Window.ShowDialog%2A>, <xref:System.Windows.Window.Show%2A> hemen döndürür. Modsuz iletişim kutusu kapatılır ve bu nedenle, ne zaman bir iletişim kutusu sonucu için kontrol edin veya daha fazla işleme için iletişim kutusundan veri alma emin değilseniz, bu nedenle, arama penceresi bildiremez. Bunun yerine, iletişim kutusu veri işleme için arama penceresine dönmek için alternatif bir yol oluşturması gerekir.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Kalıcı olmayan iletişim kutusundan dönen veri işleme  

Bu örnekte, `FindDialogBox` bir veya daha fazla bulma herhangi belirli bir sıklıkta için Aranan metin bağlı olarak ana penceresine sonuçlar döndürebilir. Bir kalıcı iletişim kutusu olduğu gibi modsuz iletişim kutusu özellikleri kullanılarak sonuçlar döndürebilir. Ancak, iletişim kutusunun sahibi penceresi bu özellikleri denetlemek ne zaman bilmek ister. Bunu etkinleştirmek için bir metin bulunduğunda bir olayı uygulamak iletişim kutusu için yoludur. `FindDialogBox` uygulayan `TextFoundEvent` bu amaç için bir temsilci hangi ilk gerektirir.  

[!code-csharp[The TextFoundEventHandler delegate](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs)]
[!code-vb[The TextFoundEventHandler delegate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb)]  

Kullanarak `TextFoundEventHandler` temsilcisi, `FindDialogBox` uygulayan `TextFoundEvent`.
  
[!code-csharp[The TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-17,125-126)]
[!code-vb[The TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-15,102-103)]

Sonuç olarak, `Find` arama sonucu bulunduğunda olay gönderebilirsiniz.  
  
[!code-csharp[Raising the TextFound event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,50-52,91-94,124-127)]
[!code-vb[Raising the TextFound event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,15,60-64,102-103)]  

Sahip penceresi, daha sonra kaydedin ve bu olayı işlemek gerekir.

[!code-csharp[Registering and handling the event](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs?range=1-10,184-195)]
[!code-vb[Registering and handling the event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb?range=1-9,126-132)]  

#### <a name="closing-a-modeless-dialog-box"></a>Kalıcı olmayan iletişim kutusunu kapatma

Çünkü <xref:System.Windows.Window.DialogResult%2A> , modelsiz bir iletişim sistemiyle kapatılması, ayarlanmış olması gerekmez aşağıdakiler dahil olmak üzere mekanizmalar:  
  
- Tıklayarak **Kapat** başlık çubuğunda düğme.  
  
- ALT + F4 tuşuna basın.  
  
- Seçme **Kapat** gelen **sistem** menüsü.  
  
Alternatif olarak, kodunuzu çağırabilirsiniz <xref:System.Windows.Window.Close%2A> olduğunda **Kapat** düğmesine tıklandığında.  

[!code-csharp[Calling the Close method](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs?range=1-9,119-126)]
[!code-vb[Calling the Close method](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb?range=1-9,99-103)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Açılan Pencereye Genel Bakış](../controls/popup-overview.md)
- [İletişim kutusu örneği](https://go.microsoft.com/fwlink/?LinkID=159984)
