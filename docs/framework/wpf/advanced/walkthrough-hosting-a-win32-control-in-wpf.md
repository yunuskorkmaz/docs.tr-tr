---
title: "İzlenecek yol: WPF'te Win32 Denetimi Barındırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0795875b4d5f1a91b7c570320acb078b845ae712
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>İzlenecek yol: WPF'te Win32 Denetimi Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]uygulamaları oluşturmak için zengin bir ortam sağlar. Önemli ölçüde yatırımınız varsa [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kodu olabilir en az yeniden daha etkili kodda bazıları, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tamamen yeniden yazmak yerine uygulama. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]barındırma için basit bir mekanizma sağlar bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi, bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfası.  
  
 Bu konuda, bir uygulama anlatan [WPF Örneğinde Win32 ListBox denetimi barındırma](http://go.microsoft.com/fwlink/?LinkID=159998), o ana bilgisayarlar bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] liste kutusu denetimini. Bu genel yordam herhangi barındırmak için Genişletilebilir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi.  
  
  
<a name="requirements"></a>   
## <a name="requirements"></a>Gereksinimler  
 Bu konuda her ikisi de temel bilindiğini varsayar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programlama. Temel bir giriş için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programlama, bkz: [Başlarken](../../../../docs/framework/wpf/getting-started/index.md). Giriş için [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programlama herhangi konu üzerine çok sayıdaki kitaplardan özellikle başvurmalısınız *Windows programlama* Charles Petzold'un.  
  
 Bu konuda eşlik örnek uygulanan çünkü [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)], onu kullanır [!INCLUDE[TLA#tla_pinvoke](../../../../includes/tlasharptla-pinvoke-md.md)] erişimi [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]. Aşina [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] yararlı ancak temel değildir.  
  
> [!NOTE]
>  Bu konu, kod örnekleri ilişkili örnekten sayısını içerir. Ancak, okunabilmesi için tam örnek kodu içermez. Edinmek veya tam kodundan görüntülemek [WPF Örneğinde Win32 ListBox denetimi barındırma](http://go.microsoft.com/fwlink/?LinkID=159998).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Temel yordamı  
 Bu bölümde barındırma temel yordamı özetlenmektedir bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresinde bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfası. Kalan bölümler her bir adımın ayrıntılarını gidin.  
  
 Temel barındırma yordamı şöyledir:  
  
1.  Uygulama bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pencereyi barındırmak için sayfa. Bir tekniktir oluşturmak için bir <xref:System.Windows.Controls.Border> barındırılan pencere için sayfanın bölümünü ayrılacak öğesi.  
  
2.  Öğesinden devralınan denetimi barındırmak için bir sınıf uygulama <xref:System.Windows.Interop.HwndHost>.  
  
3.  Bu sınıfta geçersiz kılma <xref:System.Windows.Interop.HwndHost> sınıf üyesi <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>.  
  
4.  Bir alt öğesi içeren bir pencere olarak barındırılan pencereyi oluşturun [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfası. Geleneksel rağmen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programlama açıkça gerekmez kullanmak, barındırma sayfası işleyici (HWND) ile bir penceredir. HWND sayfasını alırsınız aracılığıyla `hwndParent` parametresinin <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> yöntemi. Barındırılan pencere bu HWND alt sitesi olarak oluşturulmalıdır.  
  
5.  Konak penceresini oluşturduktan sonra barındırılan pencere HWND döndür. Bir veya daha barındırmak istiyorsanız [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] denetimleri, genellikle bir konak pencereyi HWND alt sitesi olarak oluşturun ve konak penceresinin denetimleri alt öğesi yapın. Bir ana bilgisayar penceresinde denetimleri sarmalama için basit bir yol sağlar, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerden bildirimleri almak için bazı belirli ile ilgilenir sayfasında [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] HWND sınır üzerinden bildirimleri ile ilgili sorunları.  
  
6.  Alt denetimler bildirimler gibi konak penceresine gönderilen Seçili iletileri işleyin. Bunu yapmanın iki yolu vardır.  
  
    -   Barındırma sınıfınızda iletileri işlemek tercih ederseniz, geçersiz kılma <xref:System.Windows.Interop.HwndHost.WndProc%2A> yöntemi <xref:System.Windows.Interop.HwndHost> sınıfı.  
  
    -   Olmasını isterseniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iletileri işlemek, işleme <xref:System.Windows.Interop.HwndHost> sınıfı <xref:System.Windows.Interop.HwndHost.MessageHook> , arka plan kodu olayı. Barındırılan pencere tarafından alınan her ileti için bu olayı oluşur. Bu seçeneği seçerseniz, hala kılmalı <xref:System.Windows.Interop.HwndHost.WndProc%2A>, ancak yalnızca en az bir uygulama gerekir.  
  
7.  Geçersiz kılma <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> ve <xref:System.Windows.Interop.HwndHost.WndProc%2A> yöntemlerini <xref:System.Windows.Interop.HwndHost>. Karşılamak için bu yöntemleri geçersiz kılmanız gerekir <xref:System.Windows.Interop.HwndHost> sözleşme, ancak yalnızca gerekebilir en az bir uygulama sunmak.  
  
8.  Arka plan kodu dosyanızda, barındırma sınıfı denetim örneği oluşturun ve bir alt öğesi yapın <xref:System.Windows.Controls.Border> pencereyi barındırmak için tasarlanmıştır öğesi.  
  
9. Göndererek barındırılan pencere ile iletişim [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] iletileri ve denetimlerinin gönderdiği bildirimler gibi alt öğe pencerelerinden işleme iletileri.  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>Sayfa düzeni uygulama  
 Düzenini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ListBox denetimi barındıran sayfasını iki bölgeden oluşur. Sayfanın sol tarafında birkaç barındıran [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sağlamak denetimleri bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] yönetmenize olanak tanıyan [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] denetim. Sayfanın sağ üst köşesindeki barındırılan ListBox denetimi için kare bölgesi vardır.  
  
 Bu düzen uygulamak için kod oldukça basittir. Kök öğe bir <xref:System.Windows.Controls.DockPanel> iki alt öğeye sahip. İlki bir <xref:System.Windows.Controls.Border> ListBox denetimini barındıran öğesi. 200 x 200 kare inç sayfanın sağ üst köşesindeki kaplar. İkinci bir <xref:System.Windows.Controls.StackPanel> içeren bir dizi öğeyi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bilgilerini görüntülemek ve ayarlayarak ListBox denetimi değiştirmenize izin veren denetimleri sunulan birlikte çalışabilirlik özellikleri. Alt öğelerin her biri için <xref:System.Windows.Controls.StackPanel>, bu öğeler nelerdir veya ne yaptıklarıyla ilgili ayrıntılar için kullanılan çeşitli öğeleri için başvuru materyallerini bakın, bunlar örnek kodda listelenen ancak olmayacaktır (temel burada açıklanan birlikte çalışabilirlik modeli hiçbirini gerektirmez, bunlar bazı etkileşim için örnek eklemek için sağlanır).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Microsoft Win32 denetimi barındırmak için bir sınıf uygulama  
 Bu örnek çekirdek aslında ControlHost.cs denetimini barındıran sınıftır. Öğesinden devralınan <xref:System.Windows.Interop.HwndHost>. Oluşturucusu yüksekliğini ve genişliğini karşılık gelen iki parametre, yükseklik ve genişlik, geçen <xref:System.Windows.Controls.Border> ListBox denetimini barındıran öğesi. Bu değerleri daha sonra Denetim eşleşen boyutu emin olmak için kullanılan <xref:System.Windows.Controls.Border> öğesi.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Yoktur sabitleri kümesi de. Bu sabitlerin Winuser.H'den büyük ölçüde alınır ve çağrılırken geleneksel adlarını kullanmanıza olanak sağlayan [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] işlevleri.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Microsoft Win32 penceresi oluşturmak için BuildWindowCore'u Geçersiz kılma  
 Oluşturmak için bu yöntemi geçersiz kılın [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] sayfa tarafından barındırılan ve pencere ve sayfa arasındaki bağlantı yapan penceresi. Bu örnek bir ListBox denetimi barındırma içerdiğinden, iki windows oluşturulur. İlk gerçekte tarafından barındırılan bir penceredir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfası. ListBox denetimi penceresinin bir alt öğesi olarak oluşturulur.  
  
 Bu yaklaşım denetimden bildirimleri alma işlemini basitleştirmek için nedeni. <xref:System.Windows.Interop.HwndHost> Sınıfı, onu barındıran pencereye gönderilen iletileri işlemek olanak sağlar. Barındırıyorsanız bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] denetimini doğrudan, denetimin iç ileti döngüsü gönderilen iletileri alır. Denetim ve ona iletileri gönderme görüntüleyebilir, ancak kendi üst penceresi denetim gönderir bildirimleri almazsınız. Bu, bunun yanı sıra, kullanıcı denetimi ile etkileşim kurduğunda algılama bir yolu yoktur anlamına gelir. Bunun yerine, bir ana penceresi oluşturun ve o pencerenin alt öğesi denetimi yapın. Bu denetim tarafından gönderilen bildirimler de dahil olmak üzere ana pencere iletileri işlemenize olanak sağlar. Konak penceresi biraz daha fazla denetim için basit bir sarmalayıcısı dan olduğundan kolaylık olması için paket için bir ListBox denetimi olarak anılacaktır.  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>ListBox denetimi ve konak penceresi oluşturma  
 Kullanabileceğiniz [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] denetimi için konak pencere oluşturma ve pencere sınıfı kaydı oluşturmak ve benzeri için. Ancak, bir daha basit bir yaklaşım bir pencere ile önceden tanımlanmış "statik" pencere sınıfı oluşturmaktır. Bu pencere yordamı denetimden bildirimleri almak için gereken ve en az kodlamayı gerektiren sağlar.  
  
 Ana sayfa denetime iletiler göndermek için kullanabilirsiniz, denetimi HWND salt okunur özelliği aracılığıyla sunulur.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 ListBox denetimi ana penceresinin bir alt öğesi olarak oluşturulur. Hem windows genişliği ve yüksekliği, yukarıda açıklanan bu oluşturucuya geçirilen değerlere ayarlanır. Bu denetim ve konak pencere boyutunu sayfasında ayrılmış alanı aynı olmasını sağlar.  Pencereleri oluşturduktan sonra örnek döndüren bir <xref:System.Runtime.InteropServices.HandleRef> ana penceresinin HWND içeren nesne.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>DestroyWindow ve WndProc  
 Ek olarak <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>, ayrıca geçersiz kılmanız gerekir <xref:System.Windows.Interop.HwndHost.WndProc%2A> ve <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> yöntemlerini <xref:System.Windows.Interop.HwndHost>. Bu örnekte, denetimin iletileri tarafından işlenen <xref:System.Windows.Interop.HwndHost.MessageHook> işleyici, böylece uyarlamasını <xref:System.Windows.Interop.HwndHost.WndProc%2A> ve <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> en alt düzeydedir. Durumunda <xref:System.Windows.Interop.HwndHost.WndProc%2A>ayarlayın `handled` için `false` iletinin işlenmediğini belirtmek ve 0 döndürür. İçin <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, yalnızca penceresi yok.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>Ana sayfada denetimi  
 Sayfasında denetimi barındırmak için önce yeni bir örneğini oluşturun `ControlHost` sınıfı. Denetimi içeren kenarlık öğesinin genişliği ve yüksekliği geçirin (`ControlHostElement`) için `ControlHost` Oluşturucusu. Bu liste kutusu doğru boyutta sağlar. Daha sonra atayarak denetimi sayfasına barındırmaya `ControlHost` nesnesini <xref:System.Windows.Controls.Decorator.Child%2A> konağının özelliği <xref:System.Windows.Controls.Border>.  
  
 Örnek bir işleyici iliştirir <xref:System.Windows.Interop.HwndHost.MessageHook> olayı `ControlHost` denetimden iletileri almak için. Bu olay, barındırılan penceresine gönderilen her ileti için oluşturulur. Bu durumda denetimden bildirimler de dahil olmak üzere gerçek ListBox denetimi sarmalar penceresi gönderilen iletileri şunlardır. Örnek denetimden bilgi edinmek ve içeriğini değiştirmek için SendMessage çağırır. Sayfa denetimi ile nasıl iletişim kurduğu ayrıntılarını sonraki bölümde açıklanmıştır.  
  
> [!NOTE]
>  İki olduğuna dikkat edin [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] SendMessage için bildirimleri. Bir kullandığı için bu gereklidir `wParam` bir dize ve diğer iletilecek parametre tamsayıya geçirmek için bunu kullanır. Verileri doğru şekilde sıralanmış olduğundan emin olmak her imza için ayrı bir bildirim gerekir.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>Denetim ve sayfa arasındaki iletişimi uygulama  
 Göndererek denetimi işlemek [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)] iletileri. Kullanıcı kendi konak penceresine bildirimleri göndererek ile etkileşim denetimi size bildirir. [WPF Örneğinde Win32 ListBox denetimi barındırma](http://go.microsoft.com/fwlink/?LinkID=159998) örnek bunun nasıl çalıştığı çeşitli örnekler sağlayan bir kullanıcı Arabirimi içerir:  
  
-   Bir öğeyi listeye ekleyin.  
  
-   Seçili öğeyi listeden sil  
  
-   Seçili öğenin metni görüntüleyin.  
  
-   Listedeki öğe sayısını görüntüler.  
  
 Geleneksel bir yaptıkları gibi kullanıcı aynı zamanda bir öğe liste kutusunda, tıklayarak seçebilir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulama. Görüntülenen verileri seçme, ekleme veya bir öğe ekleme kullanıcı liste kutusu durumunu her değiştiğinde güncelleştirilir.  
  
 Öğeler eklemek için liste kutusu LB_ADDSTRING iletisi gönderin. Öğeleri silmek için geçerli seçim dizinini almak için LB_GETCURSEL ve ardından öğeyi silmek için LB_DELETESTRING gönderin. Örnek ayrıca LB_GETCOUNT gönderir ve öğe sayısını gösteren görüntü güncelleştirmek için döndürülen değeri kullanır. SendMessage'nın iki örneği birini kullanın [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] önceki bölümde tartışılan bildirimleri.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Kullanıcı bir öğeyi seçer veya seçimini değiştirir, Denetim konak penceresini başlatır WM_COMMAND ileti göndererek size bildirir <xref:System.Windows.Interop.HwndHost.MessageHook> sayfası için olay. İşleyici ana pencere yordamı ana penceresinin aynı bilgileri alır. Ayrıca bir Boole değeri başvuru geçirir `handled`. Ayarladığınız `handled` için `true` ileti işlenmiş olduğunu ve başka bir işleme gerek olmadığını belirtmek için.  
  
 İşlemek istediğiniz bir olay olup olmadığını belirlemek için bildirim kimliği incelemeniz gerekir böylece WM_COMMAND çeşitli nedenlerle, için gönderilir. Kimliği yüksek Word'de bulunan `wParam` parametresi. Bu yana [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] mu HIWORD makrosu sahip değilse, örnek kimliği ayıklamak için bit düzeyinde işleçler kullanır. Kullanıcı yapılan veya kendi seçimini, kimlik LBN_SELCHANGE olacaktır.  
  
 LBN_SELCHANGE alındığında, örnek denetimi LB_GETCURSEL iletisi göndererek seçili öğenin dizinini alır. Metni almak için önce oluşturduğunuz bir <xref:System.Text.StringBuilder>. Denetimin ardından LB_GETTEXT iletisi gönderin. Boş geçmesi <xref:System.Text.StringBuilder> olarak nesne `wParam` parametresi. SendMessage döndürüldüğünde, <xref:System.Text.StringBuilder> seçilen öğenin metnini içerir. Bu SendMessage kullanılmasını henüz gerektiren başka bir [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] bildirimi.  
  
 Son olarak, ayarlamak `handled` için `true` iletinin işlendiğini belirtmek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Interop.HwndHost>  
 [WPF ve Win32 Birlikte Çalışması](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [İzlenecek Yol: İlk WPF masaüstü uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)
