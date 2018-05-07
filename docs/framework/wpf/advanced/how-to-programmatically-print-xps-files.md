---
title: 'Nasıl yapılır: Program Aracılığıyla XPS Dosyalarını Yazdırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
ms.openlocfilehash: bb11ece91c1dc8ac27b67e4175c24e480da15812
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-programmatically-print-xps-files"></a>Nasıl yapılır: Program Aracılığıyla XPS Dosyalarını Yazdırma
Bir aşırı yüklemesini kullanabilirsiniz <xref:System.Printing.PrintQueue.AddJob%2A> yazdırmak için yöntemi [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] dosyaları açmadan bir <xref:System.Windows.Controls.PrintDialog> veya İlkesi, tüm [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] hiç.  
  
 Ayrıca yazdırabilirsiniz [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] çok kullanarak dosyaları <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ve <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemlerini <xref:System.Windows.Xps.XpsDocumentWriter>. Bu hakkında daha fazla bilgi için [XPS Belge yazdırma](https://msdn.microsoft.com/library/849555c8-0c4e-48c0-86bc-a5494c69b36c(v=vs.90)).  
  
 Başka bir yolu yazdırma [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] kullanmaktır <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> veya <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A> yöntemlerinin <xref:System.Windows.Controls.PrintDialog> denetim. Bkz: [yazdırma iletişim çağırma](how-to-invoke-a-print-dialog.md).  
  
## <a name="example"></a>Örnek  
 Üç parametreli kullanmanın ana adımları <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> yöntemi aşağıdaki gibidir. Aşağıdaki örnek ayrıntılarını verir.  
  
1.  Yazıcı XPSDrv yazıcısı olup olmadığını belirler. (Bkz [yazdırma genel bakış](printing-overview.md) XPSDrv hakkında daha fazla bilgi için.)  
  
2.  Yazıcı XPSDrv yazıcısı değilse, iş parçacığının grubunu tek iş parçacığı ayarlayın.  
  
3.  Bir yazdırma sunucusu ve yazdırma sırası nesnesi örneği oluşturur.  
  
4.  Yazdırılacak dosyayı bir iş adı belirterek yöntemi çağırın ve <xref:System.Boolean> bayrak belirten yazıcı XPSDrv yazıcısı olup olmadığını.  
  
 Aşağıdaki örnek, tüm yazdırma toplu nasıl gösterir [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] bir dizindeki dosyaları. Uygulama dizin, üç parametreli belirtmek için kullanıcıdan rağmen <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> yöntemi gerekli olmadığı bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Herhangi bir kod yolunda bu kullanılabilir olduğu bir [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dosya adı ve yolu için geçiş yapabilir.  
  
 Üç parametreli <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> , aşırı <xref:System.Printing.PrintQueue.AddJob%2A> bir tek iş parçacığı grubu çalıştırmalısınız her <xref:System.Boolean> parametresi `false`, XPSDrv yazıcısı kullanıldığında, bunların olması gerekir. Ancak, varsayılan grup durumu için [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] birden çok iş parçacığıdır. Bu varsayılan örnek XPSDrv yazıcısı varsayar beri ters gerekir.  
  
 Varsayılan değeri değiştirmek için iki yolu vardır. Tek yönlü eklemektir <xref:System.STAThreadAttribute> (diğer bir deyişle, "`[System.STAThreadAttribute()]`") uygulamanın ilk satırının hemen `Main` yöntemi (genellikle "`static void Main(string[] args)`"). Bununla birlikte, birçok uygulama gerektiren `Main` yöntemine sahip birden çok iş parçacıklı durumu nedenle ikinci bir yöntem: çağrısı put <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> Grup durumu ayarlanmış ayrı bir iş parçacığı <xref:System.Threading.ApartmentState.STA> ile <xref:System.Threading.Thread.SetApartmentState%2A>. Aşağıdaki örnekte bu ikinci tekniği kullanır.  
  
 Buna örnek oluşturarak başlar bir <xref:System.Threading.Thread> nesne ve onu bir **PrintXPS** yöntemi olarak <xref:System.Threading.ThreadStart> parametresi. ( **PrintXPS** yöntemi, daha sonra örnekte tanımlanır.) Sonraki iş parçacığı tek iş parçacığı grubu olarak ayarlanır. Kalan kod `Main` yöntemi yeni bir iş parçacığı başlatır.  
  
 Örnek et bulunduğu `static` **BatchXPSPrinterçPrintXPS** yöntemi. Bir yazdırma sunucusu ve sıra oluşturduktan sonra yöntemi içeren bir dizin için kullanıcıdan [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dosyaları. Dizinin varlığını ve varlığını doğrulama sonra \*.xps dosyaları içinde yöntem her bir dosya yazdırma sırasını ekler. Örneği geçiriyoruz şekilde yazıcı XPSDrv olmayan, olduğunu varsayar `false` son parametresi, için <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> yöntemi. Bu nedenle, yöntem doğrulayacak [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] yazıcının sayfası açıklaması diline dönüştürmeye çalışmadan önce dosyayı biçimlendirme. Doğrulama başarısız olursa, bir özel durum oluşur. Örnek kod catch özel durum, kullanıcıyı Bunun hakkında bilgilendirir ve sonraki işlemeye devam [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dosya.  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 XPSDrv yazıcısı kullanıyorsanız sonra son parametre ayarlayabileceğiniz `true`. Bu durumda, bu yana [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] yazıcının sayfa açıklaması dili, yöntem, doğrulamadan veya başka bir sayfa tanımlama dili dönüştürme, yazıcıya dosya gönderir. Tasarım zamanında uygulama XPSDrv yazıcısı kullanarak vermeme emin değilseniz, uygulama okumak için değiştirebileceğiniz <xref:System.Printing.PrintQueue.IsXpsDevice%2A> özelliği ve neler bulduğu göre dalı.  
  
 Başlangıçta olacağından az XPSDrv kullanılabilir hemen yayımlandıktan sonra [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] ve Microsoft .NET Framework ihtiyacınız olabilecek XPSDrv yazıcısı XPSDrv yazıcısı olarak gönderimi. Bunu yapmak için uygulamanızı çalıştıran bilgisayar aşağıdaki kayıt defteri anahtarında dosyaların listesini Pipelineconfig.xml'i ekleyin:  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\*\<PseudoXPSPrinter>* \DependentFiles  
  
 Burada  *\<PseudoXPSPrinter >* herhangi bir yazdırma sırasıdır. Makinenin daha sonra yeniden başlatılması gerekiyor.  
  
 Bu gizleme geçirmenize olanak tanır `true` son parametre olarak <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> ancak bir özel duruma neden olmadan  *\<PseudoXPSPrinter >* gerçekten XPSDrv yazıcısı değil yalnızca anlamsız şeyler yazdırır.  
  
 **Not** kolaylık sağlamak için yukarıdaki örnek varlığını kullanan bir \*.xps uzantısı bir dosyadır kendi test olarak [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]. Ancak, [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] bu uzantıya sahip dosyaların gerekmez. [İsXPS.exe (isXPS uyumluluk aracı)](https://msdn.microsoft.com/library/bfbb433f-7ab6-417a-90f0-71443d76bcb3(v=vs.100)) tek bir dosya için sınamanın bir yolu [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] geçerlilik.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.AddJob%2A>  
 <xref:System.Threading.ApartmentState>  
 <xref:System.STAThreadAttribute>  
 [XPS](http://www.microsoft.com/xps)  
 [XPS Belge yazdırma](https://msdn.microsoft.com/library/849555c8-0c4e-48c0-86bc-a5494c69b36c(v=vs.90))  
 [Yönetilen ve yönetilmeyen iş parçacığı oluşturma](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))  
 [isXPS.exe (isXPS uyumluluk aracı)](https://msdn.microsoft.com/library/bfbb433f-7ab6-417a-90f0-71443d76bcb3(v=vs.100))  
 [WPF'deki Belgeler](documents-in-wpf.md)  
 [Yazdırmaya Genel Bakış](printing-overview.md)
