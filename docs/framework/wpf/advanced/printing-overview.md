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
ms.openlocfilehash: 902d51341850b5245b9fa6410b1954b2ab373bbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187210"
---
# <a name="printing-overview"></a>Yazdırmaya Genel Bakış
Microsoft .NET Framework ile Windows Presentation Foundation 'ı (WPF) kullanan uygulama geliştiricileri, zengin yeni bir yazdırma ve yazdırma sistemi yönetimi API'si kümesine sahiptir. Windows Vista ile bu yazdırma sistemi geliştirmelerinden bazıları, yönetilmeyen kodu kullanan Windows Forms uygulamaları ve geliştiricileri oluşturan geliştiriciler tarafından da kullanılabilir. Bu yeni işlevselliğin özünde yeni XML Kağıt Belirtimi (XPS) dosya biçimi ve XPS yazdırma yolu yer almaktadır.  
  
 Bu konuda aşağıdaki bölümler yer almaktadır.  
  
<a name="introduction_to_XPS"></a>
## <a name="about-xps"></a>XPS Hakkında  
 XPS elektronik belge biçimi, makara dosya biçimi ve sayfa açıklama dilidir. Platform ötesi belgeler oluşturmak için XML, Açık Ambalaj Sözleşmeleri (OPC) ve diğer endüstri standartlarını kullanan açık belge biçimidir. XPS, dijital belgelerin oluşturulma, paylaşılma, yazdırılma, görüntülenme ve arşivlenme işlemini kolaylaştırır. XPS hakkında daha fazla bilgi için [XPS Belgeleri'ne](/windows/desktop/printdocs/documents)bakın.  
  
 WPF kullanarak XPS tabanlı içerik yazdırmak için çeşitli teknikler [Programmatically Print XPS Dosyaları](how-to-programmatically-print-xps-files.md)gösterilmiştir. Bu konuyla ilgili içeriğin gözden geçirilmesi sırasında bu örneklere başvurmayı yararlı bulabilirsiniz. (Yönetilmeyen kod [geliştiricileri MXDC_ESCAPE işlevi](/windows/desktop/printdocs/mxdc-escape)için belgeleri görmelisiniz. Windows Forms <xref:System.Drawing.Printing> geliştiricileri, tam XPS yazdırma yolunu desteklemeyen, ancak karma GDI'den XPS yazdırma yolunu destekleyen ad alanında API'yi kullanmalıdır. Aşağıdaki **Yazdırma Yolu Mimarisi'ne** bakın.)  
  
<a name="XPS_print_path_intro"></a>
## <a name="xps-print-path"></a>XPS Yazdırma Yolu  
 XML Kağıt Belirtimi (XPS) yazdırma yolu, Yazdırmanın Windows uygulamalarında nasıl işleneceğini yeniden tanımlayan yeni bir Windows özelliğidir. XPS belge sunu dilini (RTF gibi), yazdırma biriktirme biçimi (WMF gibi) ve sayfa açıklama dilini (PCL veya Postscript gibi) değiştirebildiği için; yeni yazdırma yolu, xps biçimini uygulama yayınından yazdırma sürücüsüveya aygıtındaki son işleme kadar korur.  
  
 XPS yazdırma yolu, geliştiriciler için "ne elde ettiğinizi görürsünüz" (WYSIWYG) yazdırma, geliştirilmiş renk desteği ve önemli ölçüde geliştirilmiş yazdırma performansı gibi geliştiriciler için çeşitli avantajlar sağlayan XPS yazıcı sürücüsü modeli (XPSDrv) üzerine kurulmuştur. (XPSDrv hakkında daha fazla bilgi için [Windows Sürücü Kiti belgelerine](/windows-hardware/drivers/)bakın.)  
  
 XPS belgeleri için baskı biriktirme işleminin çalışması temelde Windows'un önceki sürümlerindekiyle aynıdır. Ancak, xps yazdırma yolunu desteklemek için varolan GDI yazdırma yoluna ek olarak geliştirilmiştir. Yeni yazdırma yolu yerel olarak bir XPS biriktirme havuzu dosyasını tüketir. Windows'un önceki sürümleri için yazılan kullanıcı modu yazıcı sürücüleri çalışmaya devam ederken, XPS yazdırma yolunu kullanmak için bir XPSyazıcı sürücüsü (XPSDrv) gereklidir.  
  
 XPS yazdırma yolunun yararları önemlidir ve şunları içerir:  
  
- WYSIWYG baskı desteği  
  
- Kanal başına 32 bit (bpc), CMYK, adlandırılmış renkler, n-mürekkepler ve saydamlık ve degradelerin yerel desteğini içeren gelişmiş renk profillerinin yerel desteği.  
  
- Hem .NET Framework hem de Win32 tabanlı uygulamalar için geliştirilmiş baskı performansı.  
  
- Endüstri standardı XPS formatı.  
  
 Temel yazdırma senaryoları için, kullanıcı arabirimi, yapılandırma ve iş gönderme için tek bir giriş noktasıyla basit ve sezgisel bir API kullanılabilir. Gelişmiş senaryolar için özelleştirme (veya [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] hiç yok), [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senkron veya eşzamanlı yazdırma ve toplu yazdırma özellikleri için ek bir destek eklenir. Her iki seçenek de tam veya kısmi güven modunda yazdırma desteği sağlar.  
  
 XPS genişletilebilirlik göz önünde bulundurularak tasarlanmıştır. Genişletilebilirlik çerçevesi kullanılarak, özellikler ve yetenekler XPS'ye modüler bir şekilde eklenebilir. Genişletilebilirlik özellikleri şunlardır:  
  
- Schema'yı yazdır. Genel şema düzenli olarak güncellenir ve cihaz yeteneklerinin hızla genişletilmesini sağlar. (Aşağıdaki **PrintTicket ve PrintCapabilities'e** bakın.)  
  
- Genişletilebilir Filtre Boru Hattı. XPS yazıcı sürücüsü (XPSDrv) filtre ardışık bölümü, XPS belgelerinin hem doğrudan hem de ölçeklenebilir şekilde yazdırılmasını sağlayacak şekilde tasarlanmıştır. Daha fazla bilgi için [XPSDrv Yazıcı Sürücüleri'ne](/windows-hardware/drivers/print/xpsdrv-printer-drivers)bakın.
  
### <a name="print-path-architecture"></a>Yazdırma Yolu Mimarisi  
 Hem Win32 hem de .NET Framework uygulamaları XPS'i desteklerken, Win32 ve Windows Forms uygulamaları XPS yazıcı sürücüsü (XPSDrv) için XPS biçimlendirilmiş içerik oluşturmak için XPS'e gdi ile dönüştürme kullanır. Bu uygulamaların XPS yazdırma yolunu kullanması gerekmez ve Gelişmiş Metafile (EMF) tabanlı yazdırmayı kullanmaya devam edebilir. Ancak, çoğu XPS özelliği ve geliştirmesi yalnızca XPS yazdırma yolunu hedefleyen uygulamalar tarafından kullanılabilir.  
  
 XPSDrv tabanlı yazıcıların Win32 ve Windows Forms uygulamaları tarafından kullanılmasını sağlamak için XPS Yazıcı sürücüsü (XPSDrv) GDI'nin XPS biçimine dönüştürülmesini destekler. XPSDrv modeli, Win32 uygulamalarının XPS Belgeleri yazdırabilmesi için XPS'den GDI formatına dönüştürücü de sağlar. WPF uygulamaları için XPS'nin GDI biçimine dönüştürülmesi, <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yazma işleminin hedef yazdırma sırası XPSDrv sürücüsü olmadığında <xref:System.Windows.Xps.XpsDocumentWriter> sınıfın yöntemleri ve yöntemleri yle otomatik olarak yapılır. (Windows Forms uygulamaları XPS Belgelerini yazdıramaz.)  
  
 Aşağıdaki resimde yazdırma alt sistemi gösterilmektedir ve Microsoft tarafından sağlanan bölümleri ve yazılım ve donanım satıcıları tarafından tanımlanan bölümleri tanımlar:  
  
 ![Ekran görüntüsü XPS yazdırma sistemini gösterir.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Temel XPS Baskı  
 WPF hem temel hem de gelişmiş API tanımlar. Kapsamlı yazdırma özelleştirmesi veya xps özellik kümesinin tamamına erişim gerektirmeyen uygulamalar için temel yazdırma desteği kullanılabilir. Temel yazdırma desteği, en az yapılandırma gerektiren ve tanıdık [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]bir şekilde sahip olan bir yazdırma iletişim denetimi aracılığıyla ortaya çıkarır. Bu basitleştirilmiş yazdırma modelini kullanarak birçok XPS özelliği mevcuttur.  
  
#### <a name="printdialog"></a>PrintDialog  
 Denetim, <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> yapılandırma ve XPS iş gönderimi için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]tek bir giriş noktası sağlar. Denetimi anında nasıl kullanacağınız ve kullanılacağı hakkında bilgi için [bkz.](how-to-invoke-a-print-dialog.md)  
  
### <a name="advanced-xps-printing"></a>Gelişmiş XPS Baskı  
 XPS özelliklerinin tamamına erişmek için gelişmiş yazdırma API'sinin kullanılması gerekir. Birkaç ilgili API aşağıda daha ayrıntılı olarak açıklanmıştır. XPS yazdırma yolu API'lerinin tam <xref:System.Windows.Xps> listesi <xref:System.Printing> için, ad alanı başvurularına bakın.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket ve PrintYetenekleri  
 Ve <xref:System.Printing.PrintTicket> <xref:System.Printing.PrintCapabilities> sınıflar gelişmiş XPS özelliklerinin temelidir. Her iki nesne türü de harmanlama, iki taraflı yazdırma, zımbalama gibi yazdırma yönelimli özelliklerin XML biçimlendirilmiş yapılarıdır. Bu yapılar baskı şeması ile tanımlanır. Bir <xref:System.Printing.PrintTicket> yazıcıya yazdırma işini nasıl işlenir talimat verir. Sınıf, <xref:System.Printing.PrintCapabilities> yazıcının özelliklerini tanımlar. Bir yazıcının özelliklerini sorgulayarak, <xref:System.Printing.PrintTicket> yazıcının desteklenen özelliklerinden tam olarak yararlanan bir yazıcı oluşturulabilir. Benzer şekilde, desteklenmeyen özellikler önlenebilir.  
  
 Aşağıdaki örnek, yazıcının <xref:System.Printing.PrintCapabilities> nasıl sorgulanır ve <xref:System.Printing.PrintTicket> bir kod oluşturmak için gösterir.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer ve PrintQueue  
 Sınıf <xref:System.Printing.PrintServer> bir ağ yazdırma sunucusunu temsil eder ve <xref:System.Printing.PrintQueue> sınıf bir yazıcıyı ve onunla ilişkili çıktı iş sırasını temsil eder. Bu API'ler birlikte, bir sunucunun yazdırma işlerinin gelişmiş yönetimine olanak sağlar. A <xref:System.Printing.PrintServer>, ya da türetilmiş sınıflarından <xref:System.Printing.PrintQueue>biri, bir . Yöntem, <xref:System.Printing.PrintQueue.AddJob%2A> kuyruğa yeni bir yazdırma işi eklemek için kullanılır.  
  
 Aşağıdaki örnek, kodu kullanarak <xref:System.Printing.LocalPrintServer> varsayılan bir <xref:System.Printing.PrintQueue> oluşturmak ve erişim nasıl göstermektedir.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 Bir <xref:System.Windows.Xps.XpsDocumentWriter>, onun <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> birçok <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> ve yöntemleri ile, bir <xref:System.Printing.PrintQueue>XPS belgeleri yazmak için kullanılır. Örneğin, <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> yöntem bir XPS belgesini ve <xref:System.Printing.PrintTicket> eşzamanlı olarak çıktıvermek için kullanılır. Yöntem, <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> xps belgesini ve <xref:System.Printing.PrintTicket> eşzamanlı olarak çıktıvermek için kullanılır.  
  
 Aşağıdaki örnek, <xref:System.Windows.Xps.XpsDocumentWriter> bir kod kullanma nın nasıl oluşturulabildiğini gösterir.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 Yöntemler <xref:System.Printing.PrintQueue.AddJob%2A> yazdırmak için yollar da sağlar. XpS [Dosyalarını Programlı Olarak Yazdır'a](how-to-programmatically-print-xps-files.md)bakın. ayrıntılar için.  
  
<a name="GDI_Print_Path_intro"></a>
## <a name="gdi-print-path"></a>GDI Yazdırma Yolu  
 WPF uygulamaları xps yazdırma yolunu doğal olarak desteklerken, Win32 ve Windows Forms uygulamaları da bazı XPS özelliklerinden yararlanabilir. XPS yazıcı sürücüsü (XPSDrv), GDI tabanlı çıktıyı XPS biçimine dönüştürebilir. Gelişmiş senaryolar için, içeriğin özel dönüşümü [Microsoft XPS Belge Dönüştürücü (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)kullanılarak desteklenir. Benzer şekilde, WPF uygulamaları da <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> <xref:System.Windows.Xps.XpsDocumentWriter> sınıfın veya yöntemlerinden birini arayarak ve hedef yazdırma sırası olarak XpsDrv olmayan bir yazıcı atayarak GDI yazdırma yoluna çıktı olabilir.  

XPS işlevselliği veya desteği gerektirmeyen uygulamalar için geçerli GDI yazdırma yolu değişmeden kalır.  
  
- GDI yazdırma yolundaki ek başvuru malzemesi ve çeşitli XPS dönüşüm seçenekleri için [Microsoft XPS Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) ve [XPSDrv Yazıcı Sürücüleri'ne](/windows-hardware/drivers/print/xpsdrv-printer-drivers)bakın.  
  
<a name="XPS_Driver_Model_intro"></a>
## <a name="xpsdrv-driver-model"></a>XPSDrv Sürücü Modeli  
 XPS yazdırma yolu, XPS özellikli bir yazıcıya veya sürücüye yazdırılırken XPS'yi yerel yazdırma makara biçimi olarak kullanarak biriktirme verimliliğini artırır. Basitleştirilmiş biriktirme işlemi, belge biriktirmeden önce EMF veri dosyası gibi bir ara biriktirme dosyası oluşturma gereksinimini ortadan kaldırır. XPS yazdırma yolu, daha küçük makara dosya boyutları sayesinde ağ trafiğini azaltabilir ve yazdırma performansını artırabilir.  
  
 EMF, hizmet vermek için GDI'ye yapılan bir dizi çağrı olarak uygulama çıktısını temsil eden kapalı bir biçimdir. EMF'nin aksine, XPS biriktirme biçimi, XPS tabanlı bir yazıcı sürücüsüne (XPSDrv) çıktı verildiğinde daha fazla yorum gerektirmeden gerçek belgeyi temsil eder. Sürücüler doğrudan formattaki veriler üzerinde çalışabilir. Bu özellik, EMF dosyalarını ve GDI tabanlı yazdırma sürücülerini kullandığınızda gereken veri ve renk alanı dönüşümlerini ortadan kaldırır.  
  
 EMF eşdeğerleriyle karşılaştırıldığında bir XPS yazıcı sürücüsünü (XPSDrv) hedefleyen XPS Belgeleri kullandığınızda dosya boyutları genellikle azalır; ancak, istisnalar vardır:  
  
- Çok karmaşık, çok katmanlı veya verimsiz yazılmış bir vektör grafiği, aynı grafiğin eşeşlenmiş sürümünden daha büyük olabilir.  
  
- Ekran görüntüleme amacıyla XPS dosyaları aygıt yazı tiplerini ve bilgisayar tabanlı yazı tiplerini katıştırır; oysa GDI biriktirme dosyaları aygıt yazı tiplerini gömmez. Ancak her iki yazı tipi türü de subsetted (aşağıya bakın) ve yazıcı sürücüleri dosyayı yazıcıya iletmeden önce aygıt yazı tiplerini kaldırabilir.  
  
 Makara boyutu azaltma çeşitli mekanizmalar aracılığıyla gerçekleştirilir:  
  
- **Yazı tipi alt ayarı.** XpS dosyasında yalnızca gerçek belge içinde kullanılan karakterler depolanır.  
  
- **Gelişmiş Grafik Desteği**. Saydamlık ve degrade ilkel için yerel destek XPS Belgesi'nde içeriğin rasterization önler.  
  
- **Ortak kaynakların tanımlanması.** Birden çok kez kullanılan kaynaklar (şirket logosunu temsil eden bir resim gibi) paylaşılan kaynak olarak kabul edilir ve yalnızca bir kez yüklenir.  
  
- **ZIP sıkıştırma**. Tüm XPS belgeleri ZIP sıkıştırma kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.PrintDialog>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.PrintQueue>
- [Nasıl Dır Konular](printing-how-to-topics.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [XPS Belgeleri](/windows/desktop/printdocs/documents)
- [Belge Serileştirme ve Depolama](document-serialization-and-storage.md)
- [Microsoft XPS Belge Dönüştürücü (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
