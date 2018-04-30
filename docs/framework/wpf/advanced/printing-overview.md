---
title: Yazdırmaya Genel Bakış
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 35
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f6478f23e6be8875ebe281b83094e4ea1d2e24e4
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="printing-overview"></a>Yazdırmaya Genel Bakış
Microsoft .NET Framework ile Windows Presentation Foundation (WPF) kullanarak uygulama geliştiricilerin yeni zengin bir yazdırmayı ve baskı sistem yönetimi sahip [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]. İle [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], bazıları bu yazdırma sistemi geliştirmelerini ayrıca oluşturma geliştiricilerine kullanılabilir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulamaları ve kullanan geliştiriciler yönetilmeyen kodu. Bu yeni işlevsellik özünde yenilikler [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] dosya biçimi ve [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] yazdırma yolu.  
  
 Bu konu aşağıdaki bölümleri içerir.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>XPS hakkında  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Elektronik belge biçimi, biriktirme dosya biçimidir ve sayfa açıklaması dili içindir. Bunu kullanan bir açık belge biçimidir [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)], [!INCLUDE[TLA#tla_opc](../../../../includes/tlasharptla-opc-md.md)]ve platformlar arası belgeleri oluşturmak için diğer endüstri standartları. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] tarafından dijital belgeleri oluşturulan, paylaşılan, yazdırılan, görüntülenen arşivlenmiş ve işlemini basitleştirir. Ek bilgi için [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)], bkz: [XPS Web sitesi](http://www.microsoft.com/xps).  
  
 Yazdırma için çeşitli teknikler [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] tabanlı içerik kullanarak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] örneklerde gösterildiği [program aracılığıyla yazdırma XPS dosyaları](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md). Bu konuda yer alan içeriği gözden geçirme sırasında bu örnekleri başvuru daha yararlı olabilir. (Yönetilmeyen kod geliştiriciler için belgeleri görmelisiniz [MXDC_ESCAPE işlevi](https://msdn.microsoft.com/library/windows/desktop/dd162739.aspx). Windows Forms geliştiriciler kullanmalıdır [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] içinde <xref:System.Drawing.Printing> tam desteklemeyen ad alanı [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] yazdırma yolu ancak mu destek karma GDI XPS yazdırma yolu. Bkz: **yazdırma yolu mimarisi** aşağıda.)  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>XPS yazdırma yolu  
 [!INCLUDE[TLA#tla_metro](../../../../includes/tlasharptla-metro-md.md)] Yazdırma yolu olan yeni bir [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] yazdırma Windows uygulamalarında nasıl işlendiğini yeniden tanımlamaktadır özelliği. Çünkü [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] belge sunum dili (örneğin, RTF), yazdırma biriktiricisi biçiminde (örneğin, WMF) ve bir sayfa tanımlama dili (örneğin, PCL veya PostScript'i) değiştirebilirsiniz; yeni yazdırma yolu tutar [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] uygulamasından biçimi yazdırma sürücüsü ya da cihaz son işleme yayına.  
  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Yazdırma yolu sırasında oluşturulan [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] sağlayan birkaç avantaj geliştiriciler için gibi yazıcı sürücüsü modeli (XPSDrv) [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] yazdırma, geliştirilmiş renk desteği ve yazdırma performansı önemli ölçüde iyileştirilmiştir. (XPSDrv hakkında daha fazla bilgi için bkz: [Windows Sürücü Geliştirme Seti](https://msdn.microsoft.com/library/windows/hardware/ff557573.aspx).)  
  
 Yazdırma Biriktiricisi için işlem [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] belgeleri aynıdır temelde Windows'un önceki sürümlerinde olduğu gibi. Ancak, bunu desteklemek için geliştirilmiştir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] varolan yanı sıra yazdırma yolu [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] yazdırma yolu. Yeni yazdırma yolunun yerel olarak kullandığı bir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] biriktirme dosya. While önceki sürümleri için yazılmış kullanıcı modu yazıcı sürücülerini [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] çalışmaya devam edecek bir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazıcı sürücüsü (XPSDrv) kullanmak için gereklidir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazdırma yolu.  
  
 Avantajları [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazdırma yolu önemli bağlıdır ve şunları içerir:  
  
-   [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)] yazdırma desteği  
  
-   Kanal (bpc) CMYK başına 32 bit dahil gelişmiş renk profillerinin yerel destek adlı renkleri, n mürekkep ve saydamlık ve gradyan yerel destek.  
  
-   Hem .NET Framework için yazdırma performansı geliştirildi ve [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] tabanlı uygulamaları.  
  
-   Endüstri standardı [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] biçimi.  
  
 Temel yazdırma senaryoları için basit ve sezgisel bir [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] kullanıcı arabirimi, yapılandırma ve iş gönderme için tek giriş noktası ile kullanılabilir. Gelişmiş senaryolar için ek destek için eklenen [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] özelleştirme (veya hiç [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] hiç), zaman uyumlu veya zaman uyumsuz yazdırma ve baskı yeteneği toplu. Her iki seçenek tam veya kısmi güven modunda yazdırma desteği sağlar.  
  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Genişletilebilirlik aklınızda ile tasarlanmıştır. Genişletilebilirlik Çerçevesi kullanarak, özellikler ve yetenekler eklenebilir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] modüler bir şekilde. Genişletilebilirlik özellikleri şunlardır:  
  
-   Şema yazdırın. Ortak şema düzenli olarak güncelleştirilir ve cihaz özelliklerinin hızlı uzantısını etkinleştirir. (Bkz **PrintTicket ve PrintCapabilities** aşağıda.)  
  
-   Genişletilebilir filtre ardışık düzen. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Yazıcı sürücüsü (XPSDrv) filtre ardışık düzen hem doğrudan hem de ölçeklenebilir yazdırmayı etkinleştirmek için tasarlanmış [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] belgeleri. (Arama "XPSDrv" içinde [Windows Sürücü Seti](https://msdn.microsoft.com/library/windows/hardware/ff557573.aspx).)  
  
### <a name="print-path-architecture"></a>Yazdırma yolu mimarisi  
 Her ikisi de while [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve .NET Framework uygulamaları Destek [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)], [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve Windows Forms uygulamaları kullanın bir [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] için [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] oluşturmak için dönüştürme [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] biçimlendirilmiş içerik için[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]yazıcı sürücüsü (XPSDrv). Bu uygulamaları kullanmak için gerekli [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazdırma yolu ve kullanmaya devam edebilirsiniz [!INCLUDE[TLA#tla_emf](../../../../includes/tlasharptla-emf-md.md)] yazdırma tabanlı. Bununla birlikte, çoğu [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] özellikler ve geliştirmeler yalnızca hedef uygulamalar için de kullanılabilir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazdırma yolu.  
  
 XPSDrv tabanlı yazıcılar tarafından kullanımını etkinleştirmek için [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve Windows Forms uygulamaları [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazıcı sürücüsü (XPSDrv) destekleyen dönüştürülmesi [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] için [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] biçimi. XPSDrv modeli için bir dönüştürücü de sağlar [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] için [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] biçimi böylece [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamaları yazdırabilirsiniz [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] belgeleri. İçin [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar, dönüştürülmesi [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] için [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] biçimi tarafından otomatik olarak yapılır <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ve <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemlerinin <xref:System.Windows.Xps.XpsDocumentWriter> yazma işlemi hedef yazdırma sırasını sahip olduğunda sınıfı bir XPSDrv sürücüsü. (Windows Forms uygulamaları olamaz yazdırma [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] belgeler.)  
  
 Aşağıdaki çizimde yazdırma alt sistemi gösterir ve tarafından sağlanan bölümleri tanımlar [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]ve yazılım ve donanım satıcıları tarafından tanımlanan bölümünü.  
  
 ![XPS yazdırma sistemi](../../../../docs/framework/wpf/advanced/media/xpsprint.PNG "XPSPrint")  
  
### <a name="basic-xps-printing"></a>Temel XPS yazdırma  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Her iki temel tanımlar ve Gelişmiş [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]. Kapsamlı gerektirmeyen uygulamalar özelleştirme veya tam erişim yazdırmak için [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] özellik kümesi, temel yazdırma desteği mevcuttur. Temel yazdırma desteği minimal yapılandırma gerektirir ve bir tanıdık özellikleri bir yazdırma iletişim denetim sunulan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Birçok [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] bu Basitleştirilmiş yazdırma modelini kullanarak özellikleri kullanılabilir.  
  
#### <a name="printdialog"></a>PrintDialog  
 <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Denetimi için bir tek giriş noktası sağlar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], yapılandırması ve [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] iş gönderme. Denetim oluşturulacağı ve kullanılacağı hakkında daha fazla bilgi için bkz: [Yazdır iletişim çağırma](../../../../docs/framework/wpf/advanced/how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Gelişmiş XPS yazdırma  
 Eksiksiz olarak erişmek için [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] özellikler, Gelişmiş Yazdırma [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] kullanılması gerekir. İlgili birkaç [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] aşağıda daha ayrıntılı olarak açıklanmıştır. Tam bir listesi için [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazdırma yolu [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], bkz: <xref:System.Windows.Xps> ve <xref:System.Printing> ad alanı başvurularını.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket ve PrintCapabilities  
 <xref:System.Printing.PrintTicket> Ve <xref:System.Printing.PrintCapabilities> sınıflardır Gelişmiş foundation [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] özellikleri. Her iki türdeki nesneler olan [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] harmanlama, vb. iki taraflı yazdırma, Zımbalı yazdırma odaklı özelliklerinin yapıları biçimlendirilmiş. Bu yapıları yazdırma şema tarafından tanımlanır. A <xref:System.Printing.PrintTicket> bir yazdırma işi işlemek nasıl bir yazıcı bildirir. <xref:System.Printing.PrintCapabilities> Sınıfı, bir yazıcı özelliklerini tanımlar. Bir yazıcı özelliklerini sorgulama tarafından bir <xref:System.Printing.PrintTicket> tam yararlanır yazıcı desteklenen özellikler oluşturulabilir. Benzer şekilde, desteklenmeyen özellikler önlenebilir.  
  
 Aşağıdaki örnekte nasıl sorgulanacağını gösterir <xref:System.Printing.PrintCapabilities> bir yazıcı ve oluşturma bir <xref:System.Printing.PrintTicket> kod kullanarak.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](../../../../samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>YazıcıSunucusu ve PrintQueue  
 <xref:System.Printing.PrintServer> Sınıfı, bir ağ yazdırma sunucusu temsil eder ve <xref:System.Printing.PrintQueue> yazıcı ve ilişkili çıktı iş kuyruğu sınıfı temsil eder. Birlikte, bunlar [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] bir sunucunun yazdırma işlerini Gelişmiş yönetimine izin ver. A <xref:System.Printing.PrintServer>, veya türetilmiş sınıflarından biri yönetmek için kullanılan bir <xref:System.Printing.PrintQueue>. <xref:System.Printing.PrintQueue.AddJob%2A> Yöntemi yeni bir yazdırma işi sıraya eklemek için kullanılır.  
  
 Aşağıdaki örnekte nasıl oluşturulduğunu gösteren bir <xref:System.Printing.LocalPrintServer> ve varsayılan erişim <xref:System.Printing.PrintQueue> kodu kullanarak.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 Bir <xref:System.Windows.Xps.XpsDocumentWriter>, kendi çok ile <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ve <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemleri, yazmak için kullanılan [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] belgeler için bir <xref:System.Printing.PrintQueue>. Örneğin, <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> yöntemi kullanılır çıkış için bir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] belge ve <xref:System.Printing.PrintTicket> zaman uyumlu olarak. <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> Yöntemi kullanılır çıkış için bir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] belge ve <xref:System.Printing.PrintTicket> zaman uyumsuz olarak.  
  
 Aşağıdaki örnekte nasıl oluşturulduğunu gösteren bir <xref:System.Windows.Xps.XpsDocumentWriter> kod kullanarak.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 <xref:System.Printing.PrintQueue.AddJob%2A> Yöntemleri de yazdırmak için yollar sağlar. Bkz: [XPS dosyalarını program aracılığıyla yazdırma](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md). Ayrıntılar için.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>GDI yazdırma yolu  
 Sırada [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamaların yerel olarak destekleyen [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazdırma yolu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve Windows Forms uygulamaları ayrıca yararlanabilir bazı [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] özellikleri. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Yazıcı sürücüsü (XPSDrv) dönüştürebilir [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] çıkışı dayalı [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] biçimi. Gelişmiş senaryolar için içerik özel dönüştürme kullanarak desteklenen [Microsoft XPS Belge dönüştürücü (MXDC)](https://msdn.microsoft.com/library/windows/desktop/ff686803.aspx). Benzer şekilde, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar de için çıktı [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] birini çağırarak yazdırma yolu <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> veya <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemlerinin <xref:System.Windows.Xps.XpsDocumentWriter> yazdırma sırası sınıfı ve hedef olarak XpsDrv yazıcısı belirleme.  

Gerektirmeyen uygulamalar için [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] işlevselliği veya desteği, geçerli [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] yazdırma yolu değişmeden kalır.  
  
-   Ek başvuru bilgileri için [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] yazdırma yolu ve çeşitli [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dönüştürme seçenekleri bkz [Microsoft XPS Belge dönüştürücü (MXDC)](https://msdn.microsoft.com/library/windows/desktop/ff686803.aspx) ve "XPSDrv" [Windows Sürücü Seti](https://msdn.microsoft.com/library/windows/hardware/ff557573.aspx).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>XPSDrv sürücü modeli  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Yazdırma yolu kullanarak biriktirici verimliliğini artırır [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] için yazdırırken yerel yazdırma biriktirme biçiminde bir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] -etkin yazıcı veya sürücü. Basitleştirilmiş biriktirme işlemini gibi bir ara Biriktirme dosyası oluşturmak için ihtiyacını ortadan kaldıran bir [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] belge Biriktiricideki önce veri dosyası. Daha küçük biriktirme dosya boyutları aracılığıyla [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazdırma yolu ağ trafiği azaltmak ve yazdırma performansı.  
  
 [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] uygulama çıkış çağrılar bir dizi olarak temsil eden kapalı bir biçimidir [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] oluşturma hizmetleri için. Farklı [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)], [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] biriktirme biçimi, ne zaman çıkış için daha fazla yorumlama gerek kalmadan gerçek belge temsil eden bir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]-based yazıcı sürücüsü (XPSDrv). Sürücüleri biçimde veriler üzerinde doğrudan çalışabilir. Bu özelliği kullanırken gerekli veri ve renk alanı dönüşümleri ortadan [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] dosyaları ve [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]-yazdırma sürücülerini tabanlı.  
  
 Biriktirme dosya boyutları genellikle kullandığınızda azaltılmış [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] hedefleyen belgeleri bir [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] yazıcı sürücüsü (XPSDrv) kıyasla ile bunların [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] eşdeğerleri; ancak, özel durum vardır:  
  
-   Çok karmaşık, çok katmanlı ya da inefficiently yazılmış bir vektör grafik eşlemli aynı grafik sürümünden büyük olamaz.  
  
-   Ekran görüntüleme amacıyla, Aygıt yazı tipleri ve bunun yanı sıra bilgisayar tabanlı yazı tipleri XPS dosyaları ekleme; GDI biriktirme dosyaları Aygıt yazı tiplerini katıştırma ise. Ancak her iki yazı tipleri alt kümelenmiş (aşağıya bakın) türleridir ve yazıcı sürücülerini yazıcı dosyasına iletmeden önce aygıt yazı tiplerini kaldırabilirsiniz.  
  
 Biriktirme boyutunu azaltma çeşitli mekanizmalar aracılığıyla gerçekleştirilir:  
  
-   **Yazı tipi alt kümeleme**. Yalnızca gerçek belge içinde kullanılan karakter depolanır [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dosya.  
  
-   **Gelişmiş grafik desteği**. Saydamlık ve gradyan temelleri için yerleşik destek önler içeriğin tarama [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] belge.  
  
-   **Ortak kaynakları tanımlaması**. (Şirket logosu temsil eden birden çok kez bir görüntü gibi) kullanılan kaynaklar paylaşılan kaynaklar olarak kabul edilir ve yalnızca bir kez yüklenir.  
  
-   **ZIP sıkıştırması**. Tüm [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] belgeleri ZIP sıkıştırması kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.PrintDialog>  
 <xref:System.Windows.Xps.XpsDocumentWriter>  
 <xref:System.Windows.Xps.Packaging.XpsDocument>  
 <xref:System.Printing.PrintTicket>  
 <xref:System.Printing.PrintCapabilities>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.PrintQueue>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/printing-how-to-topics.md)  
 [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [XPS](http://www.microsoft.com/xps)  
 [Belge Serileştirme ve Depolama](../../../../docs/framework/wpf/advanced/document-serialization-and-storage.md)  
 [Microsoft XPS Belge dönüştürücü (MXDC)](https://msdn.microsoft.com/library/windows/desktop/ff686803.aspx)
