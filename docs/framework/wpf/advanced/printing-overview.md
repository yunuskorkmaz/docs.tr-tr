---
title: Yazdırmaya Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print path [WPF], XPS
- printers [WPF], XPSDrv-based
- printing [WPF]
- PrintQueue class PrintServer class [WPF]
- XML Paper Specification (XPS) file format
- XPS (XML Paper Specification) file format
- XPSDrv-based printers
- GDI print path [WPF]
ms.assetid: 0de8ac41-9aa6-413d-a121-7aa6f41539b1
ms.openlocfilehash: 3f99b0e93e6b16ac66f6869c284c1119ddfc3751
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740309"
---
# <a name="printing-overview"></a>Yazdırmaya Genel Bakış
Microsoft .NET Framework ile, Windows Presentation Foundation (WPF) kullanan uygulama geliştiricilerinin zengin yeni bir yazdırma ve yazdırma sistemi yönetim API 'Leri kümesi vardır. Windows Vista ile, bu yazdırma sistemi geliştirmelerinden bazıları, yönetilmeyen kod kullanan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulamalar ve geliştiriciler oluşturan geliştiriciler tarafından da kullanılabilir. Bu yeni işlevselliğin çekirdeği, yeni XML Kağıt Belirtimi (XPS) dosya biçimi ve XPS yazdırma yoludur.  
  
 Bu konuda aşağıdaki bölümleri içerir.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>XPS hakkında  
 XPS elektronik belge biçimidir, bir biriktirme dosyası biçimi ve sayfa açıklaması dilidir. Bu, platformlar arası belgeler oluşturmak için XML, açık paketleme kuralları (OPC) ve diğer sektör standartlarını kullanan bir açık belge biçimidir. XPS dijital belge oluşturma, paylaşılan, yazdırılma, görüntülenen ve arşivlenen işlemleri basitleştirir. XPS hakkında daha fazla bilgi için bkz. [XPS belgeleri](/windows/desktop/printdocs/documents).  
  
 XPS tabanlı içeriği WPF kullanarak yazdırmanın birkaç tekniği, [programlı olarak XPS dosyaları yazdırma](how-to-programmatically-print-xps-files.md)bölümünde gösterilmiştir. Bu konuda yer alan içeriğin gözden geçirilmesi sırasında bu örneklere başvurmak yararlı olabilir. (Yönetilmeyen kod geliştiricileri [MXDC_ESCAPE işlevi](/windows/desktop/printdocs/mxdc-escape)için belgeler görmelidir. Windows Forms geliştiricilerin, tam XPS yazdırma yolunu desteklemeyen <xref:System.Drawing.Printing> ad alanında API kullanması gerekir, ancak karma GDI 'dan XPS 'ye yazdırma yolunu destekler. Aşağıdaki **yazdırma yolu mimarisini** inceleyin.)  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>XPS yazdırma yolu  
 XML Kağıt Belirtimi (XPS) yazdırma yolu, yazdırmanın Windows uygulamalarında nasıl işlendiğini tekrar tanımlayan yeni bir Windows özelliğidir. XPS bir belge sunumu dilini (RTF gibi), bir yazdırma biriktiricisi biçimini (örneğin, WMF) ve bir sayfa açıklaması dilini (PCL veya PostScript gibi) değiştirebilir; Yeni yazdırma yolu, uygulama yayınından, yazdırma sürücüsü veya cihazındaki son işleme XPS biçimini korur.  
  
 XPS yazdırma yolu, geliştiriciler için "gördükleriniz ne olur" (WYSıWYG) yazdırma, geliştirilmiş renk desteği ve önemli ölçüde iyileştirilmiş baskı performansı gibi geliştiriciler için çeşitli avantajlar sunan XPS yazıcı sürücüsü modeli (XPSDrv) üzerine kurulmuştur. (XPSDrv hakkında daha fazla bilgi için bkz. [Windows Sürücü Seti belgeleri](/windows-hardware/drivers/).)  
  
 XPS belgelerinin yazdırma biriktiricisinin işlemi, Windows 'un önceki sürümlerindeki ile aynıdır. Ancak, mevcut GDI yazdırma yolunun yanı sıra XPS yazdırma yolunu destekleyecek şekilde geliştirilmiştir. Yeni yazdırma yolu yerel olarak bir XPS biriktirme dosyası kullanır. Önceki Windows sürümleri için yazılan Kullanıcı modu yazıcı sürücüleri çalışmaya devam ederken, XPS yazdırma yolunu kullanabilmeniz için bir XPS yazıcı sürücüsü (XPSDrv) gereklidir.  
  
 XPS yazdırma yolunun avantajları önemlidir ve şunları içerir:  
  
- WYSıWYG yazdırma desteği  
  
- Kanal başına 32 bit (bpc), CMYK, adlandırılmış renkler, n-mürekkepler ve saydamlık ve degradelerin yerel desteği dahil olmak üzere gelişmiş renk profillerinin yerel desteği.  
  
- Hem .NET Framework hem de Win32 tabanlı uygulamalar için iyileştirilmiş yazdırma performansı.  
  
- Endüstri standardı XPS biçimi.  
  
 Temel yazdırma senaryolarında, basit ve sezgisel bir API, Kullanıcı arabirimi, yapılandırma ve iş gönderimi için tek bir giriş noktasıyla birlikte kullanılabilir. Gelişmiş senaryolar için [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] özelleştirmeye (veya hiçbir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] hiç), zaman uyumlu veya zaman uyumsuz baskıya ve toplu yazdırma özelliklerine ek bir destek eklenir. Her iki seçenek de tam veya kısmi güven modunda yazdırma desteği sağlar.  
  
 XPS, genişletilebilirlik göz önünde bulundurularak tasarlandı. Genişletilebilirlik çerçevesini kullanarak, Özellikler ve yetenekler, XPS 'ye modüler bir şekilde eklenebilir. Genişletilebilirlik özellikleri şunlardır:  
  
- Şemayı yazdır. Ortak şema düzenli olarak güncelleştirilir ve cihaz yeteneklerinin hızlı uzantısını sunar. (Bkz. **PrintTicket ve PrintCapabilities** .)  
  
- Genişletilebilir filtre işlem hattı. XPS yazıcı sürücüsü (XPSDrv) filtre işlem hattı, XPS belgelerinin hem doğrudan hem de ölçeklenebilir yazdırılmasını etkinleştirmek üzere tasarlanmıştır. Daha fazla bilgi için bkz. [XPSDrv yazıcı sürücüleri](/windows-hardware/drivers/print/xpsdrv-printer-drivers). 
  
### <a name="print-path-architecture"></a>Yazdırma yolu mimarisi  
 Hem Win32 hem de .NET Framework uygulamaları XPS 'yi destekleirken, Win32 ve Windows Forms uygulamaları XPS yazıcı sürücüsü (XPSDrv) için XPS biçimli içerik oluşturmak üzere bir GDI 'dan XPS dönüştürmesi kullanır. Bu uygulamaların XPS yazdırma yolunu kullanması gerekmez ve gelişmiş meta dosyası (EMF) tabanlı yazdırma kullanmaya devam edebilir. Ancak, çoğu XPS özelliği ve geliştirmesi yalnızca XPS yazdırma yolunu hedefleyen uygulamalar tarafından kullanılabilir.  
  
 , Bir Win32 ve Windows Forms uygulamaları tarafından XPSDrv tabanlı yazıcıların kullanımını etkinleştirmek için, XPS yazıcı sürücüsü (XPSDrv) GDI 'dan XPS biçimine dönüştürmeyi destekler. XPSDrv modeli, Ayrıca, Win32 uygulamalarının XPS belgelerini yazdırabilmesi için, XPS için bir GDI biçimine dönüştürücü sağlar. WPF uygulamaları için, yazma işleminin hedef yazdırma sırasının bir XPSDrv sürücüsüne sahip olmadığı her seferinde XPS 'ye GDI biçimine dönüştürme işlemi, <xref:System.Windows.Xps.XpsDocumentWriter> sınıfının <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ve <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemleri tarafından otomatik olarak gerçekleştirilir. (Windows Forms uygulamalar XPS belgelerini yazdıramaz.)  
  
 Aşağıdaki çizimde, yazdırma alt sistemi gösterilmektedir ve Microsoft tarafından sunulan bölümleri ve yazılım ve donanım satıcıları tarafından tanımlanan bölümleri tanımlar:  
  
 ![Ekran görüntüsü XPS Yazdırma sistemini gösterir.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Temel XPS yazdırma  
 WPF hem temel hem de Gelişmiş API tanımlar. Kapsamlı yazdırma özelleştirmesi gerektirmeyen veya XPS özelliği 'nin tamamına erişebilen uygulamalar için, temel yazdırma desteği kullanılabilir. Temel yazdırma desteği, tanıdık bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]en düşük düzeyde yapılandırma ve özellik gerektiren bir yazdırma iletişim kutusu aracılığıyla sunulur. Bu basitleştirilmiş yazdırma modeli kullanılarak birçok XPS özelliği mevcuttur.  
  
#### <a name="printdialog"></a>PrintDialog  
 <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> denetimi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], yapılandırma ve XPS işi gönderimi için tek bir giriş noktası sağlar. Denetimin örneği oluşturma ve kullanma hakkında bilgi için bkz. [bir yazdırma Iletişim kutusu çağırma](how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Gelişmiş XPS yazdırma  
 XPS özelliklerinin tamamına erişmek için gelişmiş yazdırma API 'sinin kullanılması gerekir. Birkaç ilgili API aşağıda daha ayrıntılı olarak açıklanmıştır. XPS yazdırma yolu API 'Lerinin tüm listesi için, <xref:System.Windows.Xps> ve <xref:System.Printing> ad alanı başvurularına bakın.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket ve PrintCapabilities  
 <xref:System.Printing.PrintTicket> ve <xref:System.Printing.PrintCapabilities> sınıfları, gelişmiş XPS özelliklerinin temelidir. Her iki tür nesne, harmanlama, iki taraflı yazdırma, Zımbalama vb. gibi yazdırma odaklı özelliklerin XML biçimli yapılarıdır. Bu yapılar, yazdırma şeması tarafından tanımlanır. <xref:System.Printing.PrintTicket> bir yazıcıya bir yazdırma işini nasıl işleyeceğini bildirir. <xref:System.Printing.PrintCapabilities> sınıfı bir yazıcının yeteneklerini tanımlar. Bir yazıcının yeteneklerini sorgulayarak, yazıcının desteklenen özelliklerinden tam olarak yararlanabilen bir <xref:System.Printing.PrintTicket> oluşturulabilir. Benzer şekilde, desteklenmeyen özelliklerden kaçınılabilir.  
  
 Aşağıdaki örnek, bir yazıcı <xref:System.Printing.PrintCapabilities> sorgulama ve kod kullanarak <xref:System.Printing.PrintTicket> oluşturma işlemlerinin nasıl yapılacağını gösterir.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>YazıcıSunucusu ve PrintQueue  
 <xref:System.Printing.PrintServer> sınıfı bir ağ yazdırma sunucusunu temsil eder ve <xref:System.Printing.PrintQueue> sınıfı, kendisiyle ilişkili bir yazıcıyı ve çıkış işi kuyruğunu temsil eder. Birlikte, bu API 'Ler bir sunucunun yazdırma işlerinin gelişmiş yönetimine izin verir. Bir <xref:System.Printing.PrintServer>veya türetilmiş sınıflarından biri, bir <xref:System.Printing.PrintQueue>yönetmek için kullanılır. <xref:System.Printing.PrintQueue.AddJob%2A> yöntemi, kuyruğa yeni bir yazdırma işi eklemek için kullanılır.  
  
 Aşağıdaki örnek, kod kullanarak bir <xref:System.Printing.LocalPrintServer> oluşturma ve varsayılan <xref:System.Printing.PrintQueue> erişme gösterilmiştir.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ve <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemlerine sahip bir <xref:System.Windows.Xps.XpsDocumentWriter>, XPS belgelerini bir <xref:System.Printing.PrintQueue>yazmak için kullanılır. Örneğin, <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> yöntemi bir XPS belgesi çıkarmak ve zaman uyumlu <xref:System.Printing.PrintTicket> için kullanılır. <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> yöntemi bir XPS belgesinin çıktısını almak için kullanılır ve zaman uyumsuz olarak <xref:System.Printing.PrintTicket>.  
  
 Aşağıdaki örnek, kod kullanarak bir <xref:System.Windows.Xps.XpsDocumentWriter> oluşturmayı gösterir.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 <xref:System.Printing.PrintQueue.AddJob%2A> yöntemleri, yazdırmanın yollarını da sağlar. Bkz. [Program aracılığıyla XPS dosyalarını yazdırma](how-to-programmatically-print-xps-files.md). daha fazla bilgi için.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>GDI yazdırma yolu  
 WPF uygulamaları yerel olarak XPS yazdırma yolunu destekleirken, Win32 ve Windows Forms uygulamaları da bazı XPS özelliklerinden yararlanabilir. XPS yazıcı sürücüsü (XPSDrv), GDI tabanlı çıktıyı XPS biçimine dönüştürebilir. Gelişmiş senaryolar için, [MICROSOFT XPS Belge Dönüştürücüsü (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)kullanılarak içeriğin özel dönüştürmesi desteklenir. Benzer şekilde, WPF uygulamaları ayrıca <xref:System.Windows.Xps.XpsDocumentWriter> sınıfının <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> veya <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemlerinden birini çağırarak ve XpsDrv olmayan bir yazıcıyı hedef yazdırma kuyruğu olarak belirterek GDI yazdırma yoluna da yol açabilir.  

XPS işlevselliği veya desteği gerektirmeyen uygulamalar için geçerli GDI yazdırma yolu değişmeden kalır.  
  
- GDI yazdırma yolu ve çeşitli XPS dönüştürme seçenekleri hakkında ek başvuru malzemeleri için bkz. [MICROSOFT XPS Belge Dönüştürücüsü (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) ve [XPSDrv yazıcı sürücüleri](/windows-hardware/drivers/print/xpsdrv-printer-drivers).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>XPSDrv sürücü modeli  
 XPS yazdırma yolu, XPS özellikli bir yazıcıya veya sürücüye yazdırırken yerel yazdırma kuyruğu biçimi olarak XPS kullanarak biriktirici verimliliğini geliştirir. Basitleştirilmiş biriktirme işlemi, belge belleğe alınmadan önce, EMF veri dosyası gibi bir ara biriktirme dosyası oluşturma gereksinimini ortadan kaldırır. Daha küçük biriktirme dosya boyutları ile XPS yazdırma yolu, ağ trafiğini azaltabilir ve yazdırma performansını iyileştirebilir.  
  
 EMF, uygulama çıkışını, işleme hizmetleri için GDI 'ya bir dizi çağrı olarak temsil eden kapalı bir biçimdir. EMF 'den farklı olarak, XPS biriktirme biçimi, XPS tabanlı bir yazıcı sürücüsüne (XPSDrv) çıkış yaparken daha fazla yorum gerektirmeden gerçek belgeyi temsil eder. Sürücüler doğrudan biçimdeki veriler üzerinde çalışabilir. Bu özellik, EMF dosyalarını ve GDI tabanlı yazdırma sürücülerini kullanırken gereken veri ve renk alanı dönüştürmelerini ortadan kaldırır.  
  
 , EMF eşdeğerlerine kıyasla bir XPS yazıcı sürücüsünü (XPSDrv) hedefleyen XPS belgelerini kullandığınızda biriktirme dosya boyutları genellikle azaltılır; Ancak, özel durumlar vardır:  
  
- Çok karmaşık, çok katmanlı veya yeterince yazılamaz bir vektör grafiği aynı grafiğin bit eşlemli sürümünden daha büyük olabilir.  
  
- Ekran görüntüleme amacıyla, XPS dosyaları cihaz yazı tiplerini ve bilgisayar tabanlı yazı tiplerini de katıştırır; GDI biriktirme dosyaları cihaz yazı tiplerini katıştırmaz. Ancak her iki tür yazı tipi de alt kümelenir (aşağıya bakın) ve yazıcı sürücüleri dosyayı yazıcıya iletmeden önce cihaz yazı tiplerini kaldırabilir.  
  
 Biriktirme boyutu azaltma çeşitli mekanizmalar aracılığıyla gerçekleştirilir:  
  
- **Yazı tipi alt kümeleme**. Yalnızca gerçek belge içinde kullanılan karakterler XPS dosyasında depolanır.  
  
- **Gelişmiş grafik desteği**. Saydamlık ve gradyan temel elemanlar için yerel destek, XPS belgesinde içeriğin Rasterleştirmeye karşı.  
  
- **Ortak kaynakların tanımlanması**. Birden çok kez kullanılan kaynaklar (bir kurumsal logoyu temsil eden bir görüntü gibi), paylaşılan kaynaklar olarak değerlendirilir ve yalnızca bir kez yüklenir.  
  
- **ZIP sıkıştırması**. Tüm XPS belgeleri ZIP sıkıştırması kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.PrintDialog>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.PrintQueue>
- [Nasıl Yapılır Konuları](printing-how-to-topics.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [XPS belgeleri](/windows/desktop/printdocs/documents)
- [Belge Serileştirme ve Depolama](document-serialization-and-storage.md)
- [Microsoft XPS Belge Dönüştürücüsü (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
