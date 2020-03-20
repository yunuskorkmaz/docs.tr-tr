---
title: WPF'de Win32 denetimi ne zaman sunucu
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: 5185e60640c652b79bd105db54830ac3acc57129
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186748"
---
# <a name="walkthrough-host-a-win32-control-in-wpf"></a>Walkthrough: WPF'de Win32 Kontrolü Barındırma
Windows Sunu Temeli (WPF), uygulama oluşturmak için zengin bir ortam sağlar. Ancak, Win32 koduna önemli bir yatırımınız olduğunda, bu kodun en azından bir kısmını WPF uygulamanızda yeniden kullanmak, kodu tamamen yeniden yazmak yerine yeniden kullanmak daha etkili olabilir. WPF, WPF sayfasında win32 pencerebarındırmak için basit bir mekanizma sağlar.  
  
 Bu konu bir uygulama ile size yol, [WPF Örnek bir Win32 ListBox Denetim barındırma](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control), bir Win32 liste kutusu kontrolü barındıran. Bu genel yordam herhangi bir Win32 penceresi barındırma genişletilebilir.  

<a name="requirements"></a>
## <a name="requirements"></a>Gereksinimler  
 Bu konu, hem WPF hem de Windows API programlamaile temel bir aşinalık varsayar. WPF programlamaya temel bir giriş için [Başlarken'e](../getting-started/index.md)bakın. Windows API programlamasına giriş için, charles Petzold'un *Windows Programlama* sı başta olmak üzere konuyla ilgili çok sayıda kitaba bakın.  
  
 Bu konuya eşlik eden örnek C#'da uygulandığından, Windows API'sine erişmek için Platform Çağırma Hizmetleri'ni (PInvoke) kullanır. PInvoke ile bazı aşinalık yararlı ama gerekli değildir.  
  
> [!NOTE]
> Bu konu, ilişkili örnekten bir dizi kod örneği içerir. Ancak, okunabilirlik için, tam örnek kodu içermez. [WPF Örnek'te Win32 ListBox Denetimi'nden](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)tam kod alabilir veya görüntüleyebilirsiniz.  
  
<a name="basic_procedure"></a>
## <a name="the-basic-procedure"></a>Temel Prosedür  
 Bu bölümde, WPF sayfasında Win32 penceresi barındırma temel yordamı özetler. Kalan bölümler her adımın ayrıntılarını gözden geçirir.  
  
 Temel barındırma prosedürü:  
  
1. Pencereyi barındırmak için bir WPF sayfası uygulayın. Bir teknik, sayfanın bir bölümünü barındırılan pencere için ayırmak için bir <xref:System.Windows.Controls.Border> öğe oluşturmaktır.  
  
2. 'den devralan denetimi barındırmak <xref:System.Windows.Interop.HwndHost>için bir sınıf uygulayın.  
  
3. Bu sınıfta, sınıf <xref:System.Windows.Interop.HwndHost> üyesi <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>geçersiz kılın.  
  
4. WPF sayfasını içeren pencerenin alt bölümü olarak barındırılan pencereyi oluşturun. Geleneksel WPF programlama açıkça yararlanmak gerekmez rağmen, barındırma sayfası bir tutamacı (HWND) ile bir penceredir. <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> Yöntemin `hwndParent` parametresi aracılığıyla SAYFA HWND alırsınız. Barındırılan pencere bu HWND'nin bir alt bölümü olarak oluşturulmalıdır.  
  
5. Ana bilgisayar penceresini oluşturduktan sonra, barındırılan pencerenin HWND'sini döndürün. Bir veya daha fazla Win32 denetimi barındırmak istiyorsanız, genellikle HWND'nin alt bölümü olarak bir ana bilgisayar penceresi oluşturur ve denetimleri bu ana bilgisayar penceresinin alt ları yaparsınız. Denetimleri ana bilgisayar penceresinde kaydırma, WPF sayfanızın denetimlerden bildirim alması için basit bir yol sağlar ve bu da HWND sınırındaki bildirimlerle ilgili belirli bazı Win32 sorunlarıyla ilgilenir.  
  
6. Alt denetimlerden gelen bildirimler gibi ana bilgisayar penceresine gönderilen seçili iletileri işleme. Bunu yapmanın iki yolu vardır.  
  
    - Barındırma sınıfınızdaki iletileri işlemeyi tercih ederseniz, <xref:System.Windows.Interop.HwndHost.WndProc%2A> sınıfın <xref:System.Windows.Interop.HwndHost> yöntemini geçersiz kılın.  
  
    - İletileri WPF'nin işlemesini tercih ediyorsanız, kod arkanızdaki <xref:System.Windows.Interop.HwndHost> sınıf <xref:System.Windows.Interop.HwndHost.MessageHook> olayını ele alın. Bu olay, barındırılan pencere tarafından alınan her ileti için oluşur. Bu seçeneği seçerseniz, yine de <xref:System.Windows.Interop.HwndHost.WndProc%2A>geçersiz kılmanız gerekir, ancak yalnızca en az uygulama gerekir.  
  
7. Geçersiz kılın <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> <xref:System.Windows.Interop.HwndHost.WndProc%2A> ve <xref:System.Windows.Interop.HwndHost>yöntemlerini geçersiz kılın. Sözleşmeyi <xref:System.Windows.Interop.HwndHost> karşılamak için bu yöntemleri geçersiz kılmanız gerekir, ancak yalnızca en az uygulama sağlamanız gerekebilir.  
  
8. Kod arkası dosyanızda, denetim barındırma sınıfının bir örneğini oluşturun <xref:System.Windows.Controls.Border> ve pencereyi barındırmayı amaçlayan öğenin bir alt öğesi haline getirin.  
  
9. Microsoft Windows iletileri göndererek ve denetimler tarafından gönderilen bildirimler gibi alt pencerelerinden iletileri işleyerek barındırılan pencereyle iletişim kurun.  
  
<a name="page_layout"></a>
## <a name="implement-the-page-layout"></a>Sayfa Düzenini Uygulama  
 ListBox Denetimi'ni barındıran WPF sayfasının düzeni iki bölgeden oluşur. Sayfanın sol tarafında Win32 denetimini [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] işlemenize olanak tanıyan birkaç WPF denetimi barındırAn bir denetim barındırışlar. Sayfanın sağ üst köşesinde barındırılan ListBox Denetimi için bir kare bölge vardır.  
  
 Bu düzeni uygulamak için kod oldukça basittir. Kök öğesi iki <xref:System.Windows.Controls.DockPanel> alt öğeye sahip birdir. Bunlardan ilki, ListBox Denetimini barındıran bir <xref:System.Windows.Controls.Border> öğedir. Sayfanın sağ üst köşesinde 200x200 kare kaplar. İkincisi, bilgileri <xref:System.Windows.Controls.StackPanel> görüntüleyen ve açıktan etkileşim özelliklerini ayarlayarak ListBox Denetimini işlemenizi sağlayan bir WPF denetimi kümesi içeren bir öğedir. Alt öğelerin her biri <xref:System.Windows.Controls.StackPanel>için, bu öğelerin ne olduğu veya ne yaptıkları hakkında ayrıntılar için kullanılan çeşitli öğeler için referans materyaline bakın, bunlar aşağıdaki örnek kodda listelenir, ancak burada açıklanmaz (temel interoperation modeli bunlardan herhangi birini gerektirmez, bunlar örneğe bazı etkileşim ler eklemek için sağlanır).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Microsoft Win32 Denetimini Barındırmak için Bir Sınıf Uygulama  
 Bu örneğin özü, kontrolü barındıran sınıftır, ControlHost.cs. Bu miras <xref:System.Windows.Interop.HwndHost>. Oluşturucu, ListBox denetimini barındıran <xref:System.Windows.Controls.Border> öğenin yüksekliğine ve genişliğine karşılık gelen iki parametre, yükseklik ve genişlik alır. Bu değerler daha sonra denetim boyutunun <xref:System.Windows.Controls.Border> öğeyle eşleştiğinden emin olmak için kullanılır.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Sabitler bir dizi de vardır. Bu sabitler büyük ölçüde Winuser.h alınır ve Win32 işlevlerini ararken geleneksel adları kullanmanıza olanak sağlar.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Microsoft Win32 Penceresini Oluşturmak için BuildWindowCore'u geçersiz kılın  
 Sayfa tarafından barındırılacak Win32 penceresini oluşturmak ve pencere ile sayfa arasında bağlantı kurmak için bu yöntemi geçersiz kılarsınız. Bu örnek bir ListBox Denetimi barındırma içerir, iki pencere oluşturulur. İlki, WPF sayfası tarafından barındırılan penceredir. ListBox Denetimi, bu pencerenin bir alt parçası olarak oluşturulur.  
  
 Bu yaklaşımın nedeni, denetimden bildirim alma işlemini basitleştirmektir. Sınıf, <xref:System.Windows.Interop.HwndHost> barındırdığı pencereye gönderilen iletileri işlemenizi sağlar. Doğrudan bir Win32 denetimi barındırıyorsanız, denetimin iç ileti döngüsüne gönderilen iletileri alırsınız. Denetimi görüntüleyebilir ve iletigönderebilirsiniz, ancak denetimin üst penceresine gönderdiği bildirimleri almazsınız. Bu, diğer şeylerin yanı sıra, kullanıcının denetimle ne zaman etkileşimde olduğunu algılamanın bir yolu olmadığı anlamına gelir. Bunun yerine, bir ana bilgisayar penceresi oluşturun ve denetimi bu pencerenin bir alt alanı haline getirin. Bu, denetim tarafından gönderilen bildirimlerde dahil olmak üzere ana bilgisayar penceresiiçin iletileri işlemenizi sağlar. Kolaylık sağlamak için, ana bilgisayar penceresi denetim için basit bir sarmalayıcıdan biraz daha fazlası olduğundan, paket ListBox denetimi olarak adlandırılır.  
  
<a name="create_the_window_and_listbox"></a>
#### <a name="create-the-host-window-and-listbox-control"></a>Ana Bilgisayar Penceresi ve ListBox Denetimini Oluşturma  
 Bir pencere sınıfı oluşturup kaydederek denetim için ana bilgisayar penceresi oluşturmak için PInvoke'ı kullanabilirsiniz. Ancak, çok daha basit bir yaklaşım önceden tanımlanmış "statik" pencere sınıfı ile bir pencere oluşturmaktır. Bu, denetimden bildirim almak için ihtiyacınız olan pencere yordamını sağlar ve en az kodlama gerektirir.  
  
 Denetimin HWND'si salt okunur özelliği yle ortaya çıkarır, ancak ana bilgisayar sayfası denetime ileti göndermek için bunu kullanabilir.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 ListBox denetimi ana bilgisayar penceresinin bir alt parçası olarak oluşturulur. Her iki pencerenin yüksekliği ve genişliği, yukarıda tartışılan, oluşturucuya geçirilen değerlere ayarlanır. Bu, ana bilgisayar penceresinin ve denetiminin boyutunun sayfadaki ayrılmış alanla aynı olmasını sağlar.  Pencereler oluşturulduktan sonra, örnek <xref:System.Runtime.InteropServices.HandleRef> ana pencerenin HWND içeren bir nesne döndürür.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>
### <a name="implement-destroywindow-and-wndproc"></a>DestroyWindow ve WndProc uygulayın  
 Buna ek <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>olarak, ayrıca geçersiz <xref:System.Windows.Interop.HwndHost.WndProc%2A> <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> kılmanız <xref:System.Windows.Interop.HwndHost>gerekir ve yöntemleri . Bu örnekte, denetim için iletiler <xref:System.Windows.Interop.HwndHost.MessageHook> işleyici tarafından işlenir, <xref:System.Windows.Interop.HwndHost.WndProc%2A> <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> böylece uygulanması ve en azdır. <xref:System.Windows.Interop.HwndHost.WndProc%2A>, İletinin işlenmediğini belirtmek için `false` ayarlanmış ve 0 döndürecek şekilde ayarlanmış. `handled` Çünkü, <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>sadece pencereyi yok edin.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>
## <a name="host-the-control-on-the-page"></a>Denetimi Sayfada Barındır  
 Denetimi sayfada barındırmak için önce sınıfın yeni `ControlHost` bir örneğini oluşturursunuz. Denetimi içeren kenarlık öğesinin`ControlHostElement`() yüksekliğini ve `ControlHost` genişliğini oluşturucuya geçirin. Bu, ListBox'ın doğru boyutlandırılmasını sağlar. Daha sonra `ControlHost` nesneyi ana bilgisayar özelliğine <xref:System.Windows.Controls.Decorator.Child%2A> atayarak sayfadaki <xref:System.Windows.Controls.Border>denetimi barındırırsınız.  
  
 Örnek, denetimden ileti alacak <xref:System.Windows.Interop.HwndHost.MessageHook> olaya `ControlHost` bir işleyici bağlar. Bu olay, barındırılan pencereye gönderilen her ileti için yükseltilir. Bu durumda, bunlar, denetimden gelen bildirimler de dahil olmak üzere gerçek ListBox denetimini saran pencereye gönderilen iletilerdir. Örnek, denetimden bilgi almak ve içeriğini değiştirmek için SendMessage'ı çağırır. Sayfanın denetimle nasıl iletişim kurduğuna ilişkin ayrıntılar sonraki bölümde ele alınmıştır.  
  
> [!NOTE]
> SendMessage için iki PInvoke bildirimi olduğuna dikkat edin. Bu gereklidir, çünkü `wParam` biri bir dizeyi geçmek için parametreyi kullanır ve diğeri bir tamsayıyı geçmek için kullanır. Verilerin doğru şekilde marshaled olduğundan emin olmak için her imza için ayrı bir bildirim gerekir.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>
## <a name="implement-communication-between-the-control-and-the-page"></a>Denetim ve Sayfa Arasındaki İletişimi Uygulayın  
 Windows iletileri göndererek denetimi manipüle emzebilirsiniz. Denetim, kullanıcı nın ana bilgisayar penceresine bildirim göndererek onunla etkileşimde olduğu zaman sizi bildirir. [WPF örneğindeki Win32 ListBox Denetimi'nde,](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control) bunun nasıl çalıştığına dair birkaç örnek sağlayan bir Kullanıcı Aracı içerir:  
  
- Listeye bir öğe ekleyin.  
  
- Seçili öğeyi listeden silme  
  
- Şu anda seçili öğenin metnini görüntüleyin.  
  
- Listedeki öğe sayısını görüntüleyin.  
  
 Kullanıcı, geleneksel bir Win32 uygulamasında olduğu gibi, liste kutusundaki bir öğeyi de tıklayarak seçebilir. Görüntülenen veriler, kullanıcı bir öğeyi seçerek, ekleyerek veya ekleyerek liste kutusunun durumunu her değiştirdiğinde güncelleştirilir.  
  
 Öğeleri eklemek için liste kutusuna bir [ `LB_ADDSTRING` ileti](/windows/desktop/Controls/lb-addstring)gönderin. Öğeleri silmek [`LB_GETCURSEL`](/windows/desktop/Controls/lb-getcursel) için, geçerli seçimin dizinini [`LB_DELETESTRING`](/windows/desktop/Controls/lb-deletestring) almak için gönderin ve sonra öğeyi silmek için. Örnek ayrıca [`LB_GETCOUNT`](/windows/desktop/Controls/lb-getcount)gönderir ve öğe sayısını gösteren ekranı güncelleştirmek için döndürülen değeri kullanır. Her iki [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) kullanım örneği de önceki bölümde tartışılan PInvoke bildirimlerinden biridir.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Kullanıcı bir öğeyi seçtiğinde veya seçimini değiştirdiğinde, denetim ana bilgisayar penceresini sayfa <xref:System.Windows.Interop.HwndHost.MessageHook> için olayı yükselten bir [ `WM_COMMAND` ileti](/windows/desktop/menurc/wm-command)göndererek haber verirken. İşleyici, ana pencerenin ana pencere yordamıyla aynı bilgileri alır. Ayrıca Boolean değerine bir referans `handled`geçer. İletiyi `handled` `true` işleyip başka bir işleme gerek mediğini belirtmek için ayarlayın.  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command)çeşitli nedenlerle gönderildiğinden, bunun işlemek istediğiniz bir olay olup olmadığını belirlemek için bildirim kimliğini incelemeniz gerekir. `wParam` Kimlik, parametrenin yüksek sözcüğünde bulunur. Örnek, kimliği ayıklamak için bit yönünde işleçler kullanır. Kullanıcı seçimini yapmış veya değiştirmişse, kimlik [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange).  
  
 Ne [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange) zaman alınır, örnek denetim bir [ `LB_GETCURSEL` ileti](/windows/desktop/Controls/lb-getcursel)göndererek seçili öğenin dizin alır. Metni almak için önce bir <xref:System.Text.StringBuilder>. Daha sonra denetime [ `LB_GETTEXT` ](/windows/desktop/Controls/lb-gettext)bir ileti gönderirsiniz. Boş <xref:System.Text.StringBuilder> nesneyi parametre olarak geçirin. `wParam` [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) Döndürdüğünde, <xref:System.Text.StringBuilder> seçili öğenin metnini içerir. Bu kullanım [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) için başka bir PInvoke bildirimi daha gerekiyor.  
  
 Son olarak, `true` iletinin işlendiğini belirtmek için ayarlayın. `handled`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.HwndHost>
- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
- [İzlenecek Yol: İlk WPF masaüstü uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
