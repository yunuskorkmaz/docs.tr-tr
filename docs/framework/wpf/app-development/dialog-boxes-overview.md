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
ms.openlocfilehash: 2c53dc315496d40b77e0bf0880c713ce3d3b4241
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614573"
---
# <a name="dialog-boxes-overview"></a>İletişim Kutularına Genel Bakış
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
  
 Yazdırma iletişim kutusu hakkında daha fazla bilgi için bkz. <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>. Yazdırma ayrıntılı bir açıklaması için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bkz: [yazdırma genel bakış](../advanced/printing-overview.md).  
  
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
  
- Gösteren bir **Tamam** kullanıcılar işlevi için dönüş iletişim kutusunu kapatın ve işleme devam düğmesi.  
  
- Gösteren bir **iptal** düğme iletişim kutusunu kapatın ve daha fazla işleme gelen işlevi durdurmak için kullanıcılar'ı tıklatın.  
  
- Gösteren bir **Kapat** başlık çubuğunda düğme.  
  
- Bir simge gösteriliyor.  
  
- Gösteren **simge durumuna küçült**, **Ekranı Kapla**, ve **geri** düğmeleri.  
  
- Gösteren bir **sistem** menüsünde en aza indirmek, en üst düzeye çıkarmak, geri yükleme ve iletişim kutusunu kapatın.  
  
- Yukarıda ve iletişim kutusu açılır pencerenin ortasına açılıyor.  
  
- İletişim kutuları, mümkün olduğunda iletişim kutusunu önlemek çok küçük ve kullanışlı varsayılan boyutunda kullanıcı sağlamak için hem varsayılan hem de en az ayarlamanız gerekir, böylece yeniden boyutlandırılabilir boyutları sırasıyla olması gerekir.  
  
- ESC tuşuna basarak neden olan bir klavye kısayolu olarak yapılandırılmalıdır **iptal** düğmesine basıldığında. Bu ayarı gerçekleştirilir <xref:System.Windows.Controls.Button.IsCancel%2A> özelliği **iptal** düğmesi `true`.  
  
- ENTER'ı (ya da RETURN) tuşuna basarak neden olan bir klavye kısayolu olarak yapılandırılmalıdır **Tamam** düğmesine basıldığında. Bu ayarı gerçekleştirilir <xref:System.Windows.Controls.Button.IsDefault%2A> özelliği **Tamam** düğmesi `true`.  
  
 Aşağıdaki kod, bu yapılandırma gösterilmektedir.  
  
 [!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup2)]  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind2)]  
  
 Bir iletişim kutusu için kullanıcı deneyimi de iletişim kutusu açılır pencere menü çubuğuna genişletir. Bir menü öğesi işlevi devam etmeden önce bir iletişim kutusu aracılığıyla kullanıcı etkileşimi gerektiren bir işlev çalıştığında, işlev için menü öğesi üç nokta üstbilgisinde, burada gösterildiği gibi olacaktır.  
  
 [!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup1)]  
[!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup2)]  
  
 Bir menü öğesi gibi bir hakkında iletişim kutusunda, kullanıcı etkileşimi gerektirmeyen bir iletişim kutusu görüntüleyen bir işlev çalıştığında, üç nokta gerekli değildir.  
  
#### <a name="opening-a-modal-dialog-box"></a>Kalıcı iletişim kutusu açılıyor  
 Bir iletişim kutusu, genellikle bir sözcük işlemcisi bir belgenin kenar boşluklarını ayarlama gibi bir etki alanına özgü işlevi gerçekleştirmek için bir kullanıcı bir menü öğesi seçilerek sonucu olarak gösterilir. Ek iletişim kutusu özgü yapılandırma gerektirse de gösteren bir pencere bir iletişim kutusu olarak normal bir pencere gösterecek şekilde benzerdir. Örnekleme tüm işlemi, yapılandırma ve iletişim kutusunu açıp aşağıdaki kodda gösterilmektedir.  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind4)]  
  
 Burada, kod iletişim kutusuna varsayılan bilgi (geçerli kenar boşluğu) geçiyor. Ayrıca ayarlama <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> özelliği ile bir iletişim kutusunu gösteren pencere başvurusu. Genel olarak, her zaman tüm iletişim kutularındaki ortak pencere durumu ile ilgili davranışları sağlamak için bir iletişim kutusu sahibi ayarlamanız gerekir (bkz [WPF Windows genel bakış](wpf-windows-overview.md) daha fazla bilgi için).  
  
> [!NOTE]
>  Destek için bir sahip sağlamalısınız [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Otomasyon iletişim kutuları için (bkz [UI otomasyonuna genel bakış](../../ui-automation/ui-automation-overview.md)).  
  
 İletişim kutusu yapılandırıldıktan sonra kalıcı olarak çağrılarak gösterilen <xref:System.Windows.Window.ShowDialog%2A> yöntemi.  
  
#### <a name="validating-user-provided-data"></a>Kullanıcı tarafından sağlanan verileri doğrulama  
 Bir iletişim kutusu açılır ve kullanıcının gerekli verileri sağlar, bir iletişim kutusu aşağıdaki nedenlerle sağlanan veriler geçersiz olduğundan emin olmakta sorumludur:  
  
- Güvenlik açısından bakıldığında, tüm giriş doğrulanması gerekir.  
  
- Etki alanına özgü açısından bakıldığında, veri doğrulama, hatalı verilerin olası özel durumlarını oluşturabilir kod tarafından işlenen engeller.  
  
- Bir kullanıcı deneyimi açısından bakıldığında, bir iletişim kutusu hangi verileri girdikleri geçersiz göstererek kullanıcılara yardımcı olabilirsiniz.  
  
- Özellikle uygulama Web Hizmetleri veya sunucu tabanlı veritabanları oluşturulduğunda performans açısından bakıldığında, çok katmanlı bir uygulama içinde veri doğrulama istemci ve uygulama katmanları arasındaki gidiş dönüş sayısını azaltabilir.  
  
 İlişkili bir denetiminde doğrulamak için [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], size bir doğrulama kuralını tanımlamak ve bağlama ile ilişkilendirmeniz gerekir. Bir doğrulama kuralı öğesinden türetilen özel bir sınıftır <xref:System.Windows.Controls.ValidationRule>. Aşağıdaki örnek, bir doğrulama kuralı gösterir `MarginValidationRule`, ilişkili bir değer hangi denetimleri bir <xref:System.Double> ve belirlenen aralık dahilinde.  
  
 [!code-csharp[DialogBoxSample#MarginValidationRuleCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs#marginvalidationrulecode)]
 [!code-vb[DialogBoxSample#MarginValidationRuleCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb#marginvalidationrulecode)]  
  
 Bu kodda bir doğrulama kuralını doğrulama mantığını geçersiz kılarak uygulanan <xref:System.Windows.Controls.ValidationRule.Validate%2A> verileri doğrular ve uygun bir döndüren yöntemi <xref:System.Windows.Controls.ValidationResult>.  
  
 Doğrulama kuralı ile ilişkili denetim ilişkilendirmek için aşağıdaki biçimlendirme kullanın.  
  
 [!code-xaml[DialogBoxSample#MarginsValidationMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup2)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup3)]  
  
 Doğrulama kuralı ilişkilendirildiğinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] veri ilişkili denetime girildiğinde otomatik olarak uygulanır. Bir denetim geçersiz verilerini içerdiğinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] geçersiz denetimin etrafında kırmızı bir kenarlık aşağıdaki şekilde gösterildiği gibi görüntülenir.  
  
 ![Geçersiz sol kenar boşluğu değeri etrafında kırmızı bir kenarlık bir kenar boşlukları iletişim kutusu.](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Bunlar geçerli veri girene kadar bir kullanıcı için geçersiz denetim kısıtlamaz. Bir iletişim kutusu için iyi davranışı budur; bir kullanıcının veri geçerli olup olmadığını bir iletişim kutusu denetimleri serbestçe gidebilirsiniz olması gerekir. Ancak, bir kullanıcı, geçersiz veri ve ENTER tuşuna girebilirsiniz yani **Tamam** düğmesi. Bu nedenle, kodunuzu ayrıca bir iletişim kutusu içindeki tüm denetimler doğrulamak gereken kutusunu **Tamam** işleyerek düğmesine basıldığında <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind3)]  
  
 Bu kod bir penceredeki tüm bağımlılık nesneleri numaralandırır ve geçersiz olduğunda (tarafından döndürülen <xref:System.Windows.Controls.Validation.GetHasError%2A>, geçersiz denetim odağı alır `IsValid` yöntemi döndürür `false`, ve pencerenin geçersiz olarak kabul edilir.  
  
 Bir iletişim kutusu geçerli olduğunda, onu güvenli bir şekilde kapatın dönün ve. İade işleminin bir parçası olarak, çağıran işleve bir sonuç döndürmesi gerekir.  
  
#### <a name="setting-the-modal-dialog-result"></a>Kalıcı iletişim kutusu sonucu ayarlama  
 İletişim kutusunu kullanarak açma <xref:System.Windows.Window.ShowDialog%2A> olan temelde bir yöntemi çağırmak gibi: açılan iletişim kutusunu kullanarak kod <xref:System.Windows.Window.ShowDialog%2A> kadar bekler <xref:System.Windows.Window.ShowDialog%2A> döndürür. Zaman <xref:System.Windows.Window.ShowDialog%2A> döndürür, işleme devam etmek için işleme, Durdur bağlı olup olmadığını karar vermek için ihtiyaçlarını adlı kod kullanıcı basılı **Tamam** düğmesini veya **iptal** düğmesi. Bu kararı kolaylaştırmak için kullanıcının seçenek olarak döndürülecek iletişim kutusunu gereken bir <xref:System.Boolean> öğesinden döndürülen değer <xref:System.Windows.Window.ShowDialog%2A> yöntemi.  
  
 Zaman **Tamam** düğmesine tıklandığında, <xref:System.Windows.Window.ShowDialog%2A> döndürmelidir `true`. Bu ayarı gerçekleştirilir <xref:System.Windows.Window.DialogResult%2A> özelliği iletişim kutusu **Tamam** düğmesine tıklandığında.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind3)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind4)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind4)]  
  
 Bu ayarı Not <xref:System.Windows.Window.DialogResult%2A> özelliği de penceresi otomatik olarak kapatmak, açıkça çağırma ihtiyacını neden <xref:System.Windows.Window.Close%2A>.  
  
 Zaman **iptal** düğmesine tıklandığında, <xref:System.Windows.Window.ShowDialog%2A> döndürmelidir `false`, gerektiren ayarı <xref:System.Windows.Window.DialogResult%2A> özelliği.  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind3)]  
  
 Bir düğme ayarlandığında <xref:System.Windows.Controls.Button.IsCancel%2A> özelliği `true` ve ya da kullanıcı **iptal** düğme veya ESC tuşuna <xref:System.Windows.Window.DialogResult%2A> otomatik olarak ayarlandığından `false`. Aşağıdaki biçimlendirmede işlemek zorunda kalmadan projeler yukarıdaki kodla aynı etkiye sahip <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.  
  
 [!code-xaml[DialogBoxSample#MarginsDialogDefaultCancelMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogdefaultcancelmarkup)]  
  
 Bir iletişim kutusu otomatik olarak döndürür `false` kullanıcının bastığında **Kapat** düğme başlık çubuğunda veya seçer **Kapat** menü öğesi **sistem** menüsü.  
  
#### <a name="processing-data-returned-from-a-modal-dialog-box"></a>Bir kalıcı iletişim kutusundan dönen veri işleme  
 Zaman <xref:System.Windows.Window.DialogResult%2A> ayarlanmış bir iletişim kutusu, bu işlev iletişim kutusu sonucu inceleyerek alabilirsiniz <xref:System.Windows.Window.DialogResult%2A> özelliği olduğunda <xref:System.Windows.Window.ShowDialog%2A> döndürür.  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind4)]  
  
 İletişim sonucu ise `true`, işlev, bir ipucu olarak almak ve kullanıcı tarafından sağlanan verileri işlemek için kullanır.  
  
> [!NOTE]
>  Sonra <xref:System.Windows.Window.ShowDialog%2A> döndürdü, bir iletişim kutusu açılamaz. Bunun yerine, yeni bir örneğini oluşturmanız gerekir.  
  
 İletişim sonucu ise `false`, işlev uygun şekilde işleme bitmelidir.  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a>Özel modsuz iletişim kutusu oluşturma  
 Modsuz iletişim kutusu, Bul iletişim kutusunu aşağıdaki şekilde gösterildiği gibi aynı temel görünüm kalıcı bir iletişim kutusu vardır.  
  
 ![Bul iletişim kutusunu gösteren ekran görüntüsü.](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  
  
 Ancak, aşağıdaki bölümlerde açıklandığı gibi biraz daha farklı, davranıştır.  
  
#### <a name="opening-a-modeless-dialog-box"></a>Kalıcı olmayan iletişim kutusu açılıyor  
 Çağırarak modsuz iletişim kutusu açıldığında <xref:System.Windows.Window.Show%2A> yöntemi.  
  
 [!code-xaml[DialogBoxSample#OpenFindDialogMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#openfinddialogmarkup1)]  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind3)]  
  
 Farklı <xref:System.Windows.Window.ShowDialog%2A>, <xref:System.Windows.Window.Show%2A> hemen döndürür. Modsuz iletişim kutusu kapatılır ve bu nedenle, ne zaman bir iletişim kutusu sonucu için kontrol edin veya daha fazla işleme için iletişim kutusundan veri alma emin değilseniz, bu nedenle, arama penceresi bildiremez. Bunun yerine, iletişim kutusu veri işleme için arama penceresine dönmek için alternatif bir yol oluşturması gerekir.  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a>Kalıcı olmayan iletişim kutusundan dönen veri işleme  
 Bu örnekte, `FindDialogBox` bir veya daha fazla bulma herhangi belirli bir sıklıkta için Aranan metin bağlı olarak ana penceresine sonuçlar döndürebilir. Bir kalıcı iletişim kutusu olduğu gibi modsuz iletişim kutusu özellikleri kullanılarak sonuçlar döndürebilir. Ancak, iletişim kutusunun sahibi penceresi bu özellikleri denetlemek ne zaman bilmek ister. Bunu etkinleştirmek için bir metin bulunduğunda bir olayı uygulamak iletişim kutusu için yoludur. `FindDialogBox` uygulayan `TextFoundEvent` bu amaç için bir temsilci hangi ilk gerektirir.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventHandlerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs#textfoundeventhandlercode)]
 [!code-vb[DialogBoxSample#TextFoundEventHandlerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb#textfoundeventhandlercode)]  
  
 Kullanarak `TextFoundEventHandler` temsilcisi, `FindDialogBox` uygulayan `TextFoundEvent`.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind2)]  
  
 Sonuç olarak, `Find` arama sonucu bulunduğunda olay gönderebilirsiniz.  
  
 [!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind2)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind3)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind3)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind4)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind4)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind5)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind5)]  
  
 Sahip penceresi, daha sonra kaydedin ve bu olayı işlemek gerekir.  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind2)]  
  
#### <a name="closing-a-modeless-dialog-box"></a>Kalıcı olmayan iletişim kutusunu kapatma  
 Çünkü <xref:System.Windows.Window.DialogResult%2A> , modelsiz bir iletişim sistemiyle kapatılması, ayarlanmış olması gerekmez aşağıdakiler dahil olmak üzere mekanizmalar:  
  
- Tıklayarak **Kapat** başlık çubuğunda düğme.  
  
- ALT + F4 tuşuna basın.  
  
- Seçme **Kapat** gelen **sistem** menüsü.  
  
 Alternatif olarak, kodunuzu çağırabilirsiniz <xref:System.Windows.Window.Close%2A> olduğunda **Kapat** düğmesine tıklandığında.  
  
 [!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind1)]
 [!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind1)]  
[!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind2)]
[!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Açılan Pencereye Genel Bakış](../controls/popup-overview.md)
- [İletişim kutusu örneği](https://go.microsoft.com/fwlink/?LinkID=159984)
- [ColorPicker özel denetim örneği](https://go.microsoft.com/fwlink/?LinkID=159977)
