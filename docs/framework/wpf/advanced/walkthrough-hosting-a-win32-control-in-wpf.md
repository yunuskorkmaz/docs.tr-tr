---
title: "İzlenecek yol: WPF'te Win32 Denetimi Barındırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: af8491a2887f4a35e2cd9926304948c12a67623a
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314984"
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>İzlenecek yol: WPF'te Win32 Denetimi Barındırma
Windows Presentation Foundation (WPF) uygulamaları oluşturmak için zengin bir ortam sağlar. Win32 kodunda önemli ölçüde yatırımınız varsa, ancak, bu en az bazılarını yeniden daha etkili olabilir, kod WPF uygulamanızda yerine tamamen yeniden yazın. WPF bir WPF sayfası üzerinde bir Win32 penceresi barındırmak için basit bir mekanizma sağlar.  
  
 Bu konuda, bir uygulama anlatan [WPF Örneğinde Win32 ListBox denetimi barındırma](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control), ana bilgisayarlar bir Win32 liste kutusu denetim. Bu genel yordam herhangi bir Win32 penceresi barındırmak için genişletilebilir.  
  
  
<a name="requirements"></a>   
## <a name="requirements"></a>Gereksinimler  
 Bu konu, WPF ve Win32 programlama temel olarak bilindiğini varsayar. WPF programlama temel bir giriş için bkz: [Başlarken](../../../../docs/framework/wpf/getting-started/index.md). Win32 programlamaya giriş için bu konu üzerine çok sayıda kitaplardan herhangi birine özellikle başvurmalısınız *Windows programlama* Charles Petzold'un.  
  
 Bu konuda eşlik örnek C# ' ta uygulandığı için Win32 API erişmek için Platform Başlatma Hizmetleri (PInvoke) kullanan kolaylaştırır. PInvoke aşina yararlı ancak temel değildir.  
  
> [!NOTE]
>  Bu konu, kod örnekleri ilişkili örnekten sayısını içerir. Ancak, okunabilmesi için tam örnek kodu içermez. Edinmek veya tam kodundan görüntülemek [WPF Örneğinde Win32 ListBox denetimi barındırma](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Temel yordamı  
 Bu bölümde bir WPF sayfası üzerinde bir Win32 penceresi barındırmak için temel yordamı özetlenmektedir. Kalan bölümler her bir adımın ayrıntılarını gidin.  
  
 Temel barındırma yordamı şöyledir:  
  
1.  Pencereyi barındırmak için bir WPF sayfası uygulayın. Bir tekniktir oluşturmak için bir <xref:System.Windows.Controls.Border> barındırılan pencere için sayfanın bölümünü ayrılacak öğesi.  
  
2.  Öğesinden devralınan denetimi barındırmak için bir sınıf uygulama <xref:System.Windows.Interop.HwndHost>.  
  
3.  Bu sınıfta geçersiz kılma <xref:System.Windows.Interop.HwndHost> sınıf üyesi <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>.  
  
4.  Barındırılan pencere WPF sayfasını içeren pencerenin alt öğesi olarak oluşturursunuz. Geleneksel WPF programlama açıkça gerekmez ancak bunu kullanmak, barındırma sayfası işleyici (HWND) ile bir penceredir. HWND sayfasını alırsınız aracılığıyla `hwndParent` parametresinin <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> yöntemi. Barındırılan pencere bu HWND alt sitesi olarak oluşturulmalıdır.  
  
5.  Konak penceresini oluşturduktan sonra barındırılan pencere HWND döndür. Bir veya daha fazla Win32 denetimleri barındırmak istiyorsanız, genellikle bir konak pencereyi HWND alt sitesi olarak oluşturun ve konak penceresinin denetimleri alt öğesi yaparsınız. Bir ana bilgisayar penceresinde denetimleri sarmalama hangi bildirimleri ile belirli bazı Win32 sorunları HWND sınırından ilgilenir denetimlerden bildirimleri almak WPF sayfanız için basit bir yol sağlar.  
  
6.  Alt denetimler bildirimler gibi konak penceresine gönderilen Seçili iletileri işleyin. Bunu yapmanın iki yolu vardır.  
  
    -   Barındırma sınıfınızda iletileri işlemek tercih ederseniz, geçersiz kılma <xref:System.Windows.Interop.HwndHost.WndProc%2A> yöntemi <xref:System.Windows.Interop.HwndHost> sınıfı.  
  
    -   WPF iletileri işlemek, işlemek tercih ederseniz <xref:System.Windows.Interop.HwndHost> sınıfı <xref:System.Windows.Interop.HwndHost.MessageHook> , arka plan kodu olayı. Barındırılan pencere tarafından alınan her ileti için bu olayı oluşur. Bu seçeneği seçerseniz, hala kılmalı <xref:System.Windows.Interop.HwndHost.WndProc%2A>, ancak yalnızca en az bir uygulama gerekir.  
  
7.  Geçersiz kılma <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> ve <xref:System.Windows.Interop.HwndHost.WndProc%2A> yöntemlerini <xref:System.Windows.Interop.HwndHost>. Karşılamak için bu yöntemleri geçersiz kılmanız gerekir <xref:System.Windows.Interop.HwndHost> sözleşme, ancak yalnızca gerekebilir en az bir uygulama sunmak.  
  
8.  Arka plan kodu dosyanızda, barındırma sınıfı denetim örneği oluşturun ve bir alt öğesi yapın <xref:System.Windows.Controls.Border> pencereyi barındırmak için tasarlanmıştır öğesi.  
  
9. Göndererek barındırılan pencere ile iletişim [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] iletileri ve denetimlerinin gönderdiği bildirimler gibi alt öğe pencerelerinden işleme iletileri.  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>Sayfa düzeni uygulama  
 ListBox denetimi barındıran WPF sayfa düzeni iki bölgeden oluşur. Sayfanın sol tarafında sağlayan birkaç WPF denetimleri barındıran bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Win32 denetimi yönetmenize olanak sağlar. Sayfanın sağ üst köşesindeki barındırılan ListBox denetimi için kare bölgesi vardır.  
  
 Bu düzen uygulamak için kod oldukça basittir. Kök öğe bir <xref:System.Windows.Controls.DockPanel> iki alt öğeye sahip. İlki bir <xref:System.Windows.Controls.Border> ListBox denetimini barındıran öğesi. 200 x 200 kare inç sayfanın sağ üst köşesindeki kaplar. İkinci bir <xref:System.Windows.Controls.StackPanel> bilgileri görüntüleyen ve ayarlayarak ListBox denetimi değiştirmenize izin veren WPF denetimleri kümesini içeren öğeyi kullanıma sunulan birlikte çalışabilirlik özellikleri. Alt öğelerin her biri için <xref:System.Windows.Controls.StackPanel>, bu öğeler nelerdir veya ne yaptıklarıyla ilgili ayrıntılar için kullanılan çeşitli öğeleri için başvuru materyallerini bakın, bunlar örnek kodda listelenen ancak olmayacaktır (temel burada açıklanan birlikte çalışabilirlik modeli hiçbirini gerektirmez, bunlar bazı etkileşim için örnek eklemek için sağlanır).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Microsoft Win32 denetimi barındırmak için bir sınıf uygulama  
 Bu örnek çekirdek aslında ControlHost.cs denetimini barındıran sınıftır. Öğesinden devralınan <xref:System.Windows.Interop.HwndHost>. Oluşturucusu yüksekliğini ve genişliğini karşılık gelen iki parametre, yükseklik ve genişlik, geçen <xref:System.Windows.Controls.Border> ListBox denetimini barındıran öğesi. Bu değerleri daha sonra Denetim eşleşen boyutu emin olmak için kullanılan <xref:System.Windows.Controls.Border> öğesi.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Yoktur sabitleri kümesi de. Bu sabitleri Winuser.H'den büyük ölçüde alınır ve Win32 işlevleri çağrılırken geleneksel adlarını kullanmanıza izin verir.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Microsoft Win32 penceresi oluşturmak için BuildWindowCore'u Geçersiz kılma  
 Sayfa tarafından barındırılan ve pencere ve sayfa arasındaki bağlantı yapan Win32 penceresi oluşturmak için bu yöntemi geçersiz kılın. Bu örnek bir ListBox denetimi barındırma içerdiğinden, iki windows oluşturulur. İlk gerçekte WPF sayfa tarafından barındırılan bir penceredir. ListBox denetimi penceresinin bir alt öğesi olarak oluşturulur.  
  
 Bu yaklaşım denetimden bildirimleri alma işlemini basitleştirmek için nedeni. <xref:System.Windows.Interop.HwndHost> Sınıfı, onu barındıran pencereye gönderilen iletileri işlemek olanak sağlar. Win32 Konak denetimini doğrudan denetimi iç ileti döngüsüne gönderilen iletileri alıyorsunuz. Denetim ve ona iletileri gönderme görüntüleyebilir, ancak kendi üst penceresi denetim gönderir bildirimleri almazsınız. Bu, bunun yanı sıra, kullanıcı denetimi ile etkileşim kurduğunda algılama bir yolu yoktur anlamına gelir. Bunun yerine, bir ana penceresi oluşturun ve o pencerenin alt öğesi denetimi yapın. Bu denetim tarafından gönderilen bildirimler de dahil olmak üzere ana pencere iletileri işlemenize olanak sağlar. Konak penceresi biraz daha fazla denetim için basit bir sarmalayıcısı dan olduğundan kolaylık olması için paket için bir ListBox denetimi olarak anılacaktır.  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>ListBox denetimi ve konak penceresi oluşturma  
 Denetim için bir konak penceresi oluşturma ve pencere sınıfı kaydı oluşturmak ve benzeri PInvoke kullanabilirsiniz. Ancak, bir daha basit bir yaklaşım bir pencere ile önceden tanımlanmış "statik" pencere sınıfı oluşturmaktır. Bu pencere yordamı denetimden bildirimleri almak için gereken ve en az kodlamayı gerektiren sağlar.  
  
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
>  SendMessage için iki PInvoke bildirimleri olduğuna dikkat edin. Bir kullandığı için bu gereklidir `wParam` bir dize ve diğer iletilecek parametre tamsayıya geçirmek için bunu kullanır. Verileri doğru şekilde sıralanmış olduğundan emin olmak her imza için ayrı bir bildirim gerekir.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>Denetim ve sayfa arasındaki iletişimi uygulama  
 Windows iletileri göndererek denetimi değiştirebilirsiniz. Kullanıcı kendi konak penceresine bildirimleri göndererek ile etkileşim denetimi size bildirir. [WPF'de Win32 ListBox denetimi barındırma](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control) örnek bunun nasıl çalıştığı çeşitli örnekler sağlayan bir kullanıcı Arabirimi içerir:  
  
-   Bir öğeyi listeye ekleyin.  
  
-   Seçili öğeyi listeden sil  
  
-   Seçili öğenin metni görüntüleyin.  
  
-   Listedeki öğe sayısını görüntüler.  
  
 Geleneksel bir Win32 uygulaması için yaptıkları gibi kullanıcı bir öğeyi liste kutusunda, tıklayarak öğesini de seçebilirsiniz. Görüntülenen verileri seçme, ekleme veya bir öğe ekleme kullanıcı liste kutusu durumunu her değiştiğinde güncelleştirilir.  
  
 Öğeler eklemek için liste kutusu Gönder bir [ `LB_ADDSTRING` ileti](https://msdn.microsoft.com/library/windows/desktop/bb775181(v=vs.85).aspx). Öğeleri silmek için Gönder [ `LB_GETCURSEL` ](https://msdn.microsoft.com/library/windows/desktop/bb775197(v=vs.85).aspx) geçerli seçim dizinini almak için ve ardından [ `LB_DELETESTRING` ](https://msdn.microsoft.com/library/windows/desktop/bb775183(v=vs.85).aspx) öğe silinemedi. Örnek ayrıca gönderir [ `LB_GETCOUNT` ](https://msdn.microsoft.com/library/windows/desktop/bb775195(v=vs.85).aspx)ve öğe sayısını gösteren görüntü güncelleştirmek için döndürülen değeri kullanır. ' In iki örneği [ `SendMessage` ](https://msdn.microsoft.com/library/windows/desktop/ms644950(v=vs.85).aspx) önceki bölümde tartışılan PInvoke bildirimleri birini kullanın.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Kullanıcı bir öğeyi seçer veya seçimini değiştirir, Denetim konak penceresine göndererek bildirir bir [ `WM_COMMAND` ileti](https://msdn.microsoft.com/library/windows/desktop/ms647591(v=vs.85).aspx), hangi başlatır <xref:System.Windows.Interop.HwndHost.MessageHook> sayfası için olay. İşleyici ana pencere yordamı ana penceresinin aynı bilgileri alır. Ayrıca bir Boole değeri başvuru geçirir `handled`. Ayarladığınız `handled` için `true` ileti işlenmiş olduğunu ve başka bir işleme gerek olmadığını belirtmek için.  
  
 [`WM_COMMAND`](https://msdn.microsoft.com/library/windows/desktop/ms647591(v=vs.85).aspx) işlemek istediğiniz bir olay olup olmadığını belirlemek için bildirim kimliği incelemeniz gerekir böylece çeşitli nedenlerle, için gönderilir. Kimliği yüksek Word'de bulunan `wParam` parametresi. Örnek kimliği ayıklamak için bit düzeyinde işleçler kullanır. Kullanıcı yapılan veya kendi seçimini, kimliği olacaktır [ `LBN_SELCHANGE` ](https://msdn.microsoft.com/library/windows/desktop/bb775161(v=vs.85).aspx).  
  
 Zaman [ `LBN_SELCHANGE` ](https://msdn.microsoft.com/library/windows/desktop/bb775161(v=vs.85).aspx) olan alınan, örnek seçili öğenin dizini denetimi göndererek alır bir [ `LB_GETCURSEL` ileti](https://msdn.microsoft.com/library/windows/desktop/bb775197(v=vs.85).aspx). Metni almak için önce oluşturduğunuz bir <xref:System.Text.StringBuilder>. Denetim daha sonra göndereceğiniz bir [ `LB_GETTEXT` ileti](https://msdn.microsoft.com/library/windows/desktop/bb761313(v=vs.85).aspx). Boş geçmesi <xref:System.Text.StringBuilder> olarak nesne `wParam` parametresi. Zaman [ `SendMessage` ](https://msdn.microsoft.com/library/windows/desktop/ms644950(v=vs.85).aspx) döndürür, <xref:System.Text.StringBuilder> seçilen öğenin metnini içerir. Bu kullanımını [ `SendMessage` ](https://msdn.microsoft.com/library/windows/desktop/ms644950(v=vs.85).aspx) henüz başka bir PInvoke bildirimi gerektirir.  
  
 Son olarak, ayarlamak `handled` için `true` iletinin işlendiğini belirtmek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Interop.HwndHost>  
 [WPF ve Win32 Birlikte Çalışması](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [İzlenecek Yol: İlk WPF masaüstü uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)
