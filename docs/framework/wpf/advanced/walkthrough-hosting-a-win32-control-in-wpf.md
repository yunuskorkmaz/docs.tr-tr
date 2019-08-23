---
title: 'İzlenecek yol: WPF içinde Win32 Denetimini Barındırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: cc27189afd2185d5f0a1eeacccf4c537dd3d9c2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917539"
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>İzlenecek yol: WPF içinde Win32 Denetimini Barındırma
Windows Presentation Foundation (WPF), uygulamalar oluşturmak için zengin bir ortam sağlar. Ancak, Win32 kodunda önemli bir yatırımınız olduğunda, bu kodu tamamen yeniden yazmak yerine WPF uygulamanızda en az bir kısmını yeniden kullanmak daha etkili olabilir. WPF, bir WPF sayfasında Win32 penceresini barındırmak için kolay bir mekanizma sağlar.  
  
 Bu konu, bir Win32 liste kutusu denetimi barındıran [WPF örneğinde Win32 ListBox denetimini barındıran](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)bir uygulamada size kılavuzluk eder. Bu genel yordam, herhangi bir Win32 penceresini barındırmak için genişletilebilir.  

<a name="requirements"></a>   
## <a name="requirements"></a>Gereksinimler  
 Bu konu, WPF ve Windows API programlamasında temel bir benzerlik olduğunu varsayar. WPF programlamasına temel bir giriş için bkz. Başlarken [](../getting-started/index.md). Windows API programlamaya giriş için, özellikle Charles Petzold tarafından yapılan belirli bir *programlama* penceresinde konu üzerinde bulunan çok sayıda kitaplardan birine bakın.  
  
 Bu konuya eşlik eden örnek ' de C#uygulandığından, Windows API 'sine erişmek Için platform çağırma hizmetleri 'Ni (PInvoke) kullanır. PInvoke ile ilgili bazı benzerlik yararlı ancak gerekli değildir.  
  
> [!NOTE]
> Bu konu, ilişkili örnekten bir dizi kod örneği içerir. Ancak okunabilirlik için, örnek kodu tamamen içermez. [WPF örneğinde Win32 ListBox denetimini barındırırken](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)tüm kodu alabilir veya görüntüleyebilirsiniz.  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Temel yordam  
 Bu bölümde, bir WPF sayfasında Win32 penceresi barındırmak için temel yordam özetlenmektedir. Kalan bölümler her adımın ayrıntılarına gider.  
  
 Temel barındırma prosedürü şunlardır:  
  
1. Pencereyi barındırmak için bir WPF sayfası uygulayın. Bir yöntem, barındırılan pencere için <xref:System.Windows.Controls.Border> sayfanın bir bölümünü ayırmak üzere bir öğesi oluşturmaktır.  
  
2. Öğesinden <xref:System.Windows.Interop.HwndHost>devralan denetimi barındırmak için bir sınıf uygulayın.  
  
3. Bu sınıfta, <xref:System.Windows.Interop.HwndHost> sınıf üyesini <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>geçersiz kılın.  
  
4. Barındırılan pencereyi WPF sayfasını içeren pencerenin bir alt öğesi olarak oluşturun. Geleneksel WPF programlamanın açık bir şekilde kullanılmasını gerektirmese de, barındırma sayfası tutamacı (HWND) olan bir pencere olur. `hwndParent` Yöntemin parametresi<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> aracılığıyla HWND sayfasını alırsınız. Barındırılan pencere bu HWND 'nin bir alt öğesi olarak oluşturulmalıdır.  
  
5. Konak penceresini oluşturduktan sonra barındırılan pencerenin HWND 'sini döndürün. Bir veya daha fazla Win32 denetimini barındırmak istiyorsanız, genellikle HWND 'nin bir alt öğesi olarak bir ana bilgisayar penceresi oluşturur ve bu konak penceresinin alt öğelerini yapar. Denetimleri bir ana bilgisayar penceresinde sarmalama, WPF sayfanızın, HWND sınırları içindeki bildirimlerle ilgili bazı Win32 sorunlarıyla ilgilenen, denetimlerden bildirimler alması için basit bir yol sağlar.  
  
6. Alt denetimlerin bildirimleri gibi ana bilgisayar penceresine gönderilen Seçili iletileri işleyin. Bunu iki şekilde yapabilirsiniz.  
  
    - Barındırma sınıfınıza iletileri işlemek isterseniz, <xref:System.Windows.Interop.HwndHost.WndProc%2A> <xref:System.Windows.Interop.HwndHost> sınıfının yöntemini geçersiz kılın.  
  
    - WPF 'nin iletileri işlemesini tercih ediyorsanız, arka plan kodunuzda <xref:System.Windows.Interop.HwndHost> sınıf <xref:System.Windows.Interop.HwndHost.MessageHook> olayını işleyin. Bu olay barındırılan pencere tarafından alınan her ileti için oluşur. Bu seçeneği belirlerseniz, yine de geçersiz kılmalısınız <xref:System.Windows.Interop.HwndHost.WndProc%2A>, ancak yalnızca en az bir uygulama gerekir.  
  
7. <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> Ve yöntemlerinigeçersiz<xref:System.Windows.Interop.HwndHost>kılın. <xref:System.Windows.Interop.HwndHost.WndProc%2A> <xref:System.Windows.Interop.HwndHost> Sözleşmeyi karşılamak için bu yöntemleri geçersiz kılmanız gerekir, ancak yalnızca en az bir uygulama sağlamanız gerekebilir.  
  
8. Arka plan kod dosyanızda, denetim barındırma sınıfının bir örneğini oluşturun ve pencereyi barındırmak amaçlanan <xref:System.Windows.Controls.Border> öğesinin bir alt öğesi yapın.  
  
9. Barındırılan pencereyle, denetimler tarafından gönderilen bildirimler gibi [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] , kendi alt penceresağından iletiler göndererek ve iletileri işleyerek iletişim kurun.  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>Sayfa düzeni uygulama  
 ListBox denetimini barındıran WPF sayfasının düzeni iki bölgeden oluşur. Sayfanın sol tarafında, Win32 denetimini değiştirmenize olanak sağlayan çeşitli WPF denetimleri [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] barındırır. Sayfanın sağ üst köşesinde barındırılan ListBox denetimi için bir kare bölgesi bulunur.  
  
 Bu düzeni uygulamak için kod oldukça basittir. Kök öğesi, iki alt <xref:System.Windows.Controls.DockPanel> öğesi olan bir öğesidir. Birincisi, ListBox denetimini <xref:System.Windows.Controls.Border> barındıran bir öğedir. Sayfanın sağ üst köşesinde bir 200x200 kare kaplar. İkincisi, bilgileri görüntüleyen <xref:System.Windows.Controls.StackPanel> ve gösterilen birlikte çalışabilirlik özelliklerini ayarlayarak ListBox denetimini değiştirmenize izin veren bir WPF denetimleri kümesini içeren bir öğedir. Öğesinin alt öğesi olan öğelerin her biri için <xref:System.Windows.Controls.StackPanel>, bu öğelerin ne olduğu veya ne yaptığını gösteren Ayrıntılar için kullanılan çeşitli öğelerin başvuru malzemesine bakın, bunlar aşağıdaki örnek kodda listelenir, ancak burada açıklanmaz (temel birlikte çalışabilirlik modeli bunlardan herhangi birini gerektirmez, örneğe bazı etkileşimler eklemek için bu değerler sağlanır.  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Microsoft Win32 denetimini barındırmak için bir sınıf uygulama  
 Bu örneğin çekirdeği aslında ControlHost.cs denetimini barındıran sınıftır. Öğesinden <xref:System.Windows.Interop.HwndHost>devralır. Oluşturucu, ListBox denetimini barındıran <xref:System.Windows.Controls.Border> öğenin yüksekliğine ve genişliğine karşılık gelen iki parametre, yükseklik ve genişlik alır. Bu değerler daha sonra denetimin boyutunun <xref:System.Windows.Controls.Border> öğesiyle eşleştiğinden emin olmak için kullanılır.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Ayrıca bir sabitler kümesi de vardır. Bu sabitler büyük ölçüde Winuser. h 'den alınmıştır ve Win32 işlevlerini çağırırken geleneksel adları kullanmanıza izin verir.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Microsoft Win32 penceresini oluşturmak için BuildWindowCore ' u geçersiz kılın  
 Bu yöntemi, sayfa tarafından barındırılacak Win32 penceresini oluşturmak ve pencere ile sayfa arasında bağlantı kurmak için geçersiz kılar. Bu örnek bir ListBox denetimini barındırmayı içerdiğinden, iki pencere oluşturulur. Birincisi, WPF sayfası tarafından gerçekten barındırılan penceredir. ListBox denetimi pencerenin alt öğesi olarak oluşturulur.  
  
 Bu yaklaşımın nedeni denetimden bildirim alma sürecini basitleştirmektir. <xref:System.Windows.Interop.HwndHost> Sınıfı, barındırmakta olduğu pencereye gönderilen iletileri işleyebilmeniz için izin verir. Bir Win32 denetimini doğrudan barındırdıysanız, denetimin iç ileti döngüsüne gönderilen iletileri alırsınız. Denetimi görüntüleyebilir ve bu iletileri gönderebilirsiniz, ancak denetimin ana penceresine gönderdiği bildirimleri almazsınız. Bu, diğer öğelerin yanı sıra kullanıcının denetimle ne zaman etkileşime gireceğini tespit etmenin hiçbir şekilde algılanmadığını gösterir. Bunun yerine, bir konak penceresi oluşturun ve denetimi bu pencerenin alt öğesi yapın. Bu, denetim tarafından kendisine gönderilen bildirimler dahil olmak üzere ana bilgisayar penceresi iletilerini işlemanıza olanak sağlar. Kolaylık sağlaması için, ana bilgisayar penceresi denetim için basit bir sarmalayıcıdan daha fazla olduğundan, pakete ListBox denetimi olarak başvurulur.  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>Konak penceresini ve ListBox denetimini oluşturma  
 Bir pencere sınıfı oluşturup kaydederek denetim için bir konak penceresi oluşturmak üzere PInvoke kullanabilirsiniz. Ancak, çok daha basit bir yaklaşım önceden tanımlanmış "static" pencere sınıfıyla bir pencere oluşturmaktır. Bu, denetimden bildirimleri almak için ihtiyaç duyduğunuz pencere yordamını sağlar ve en az kodlama gerektirir.  
  
 Denetimin HWND 'si, bir salt okunurdur özelliği aracılığıyla sunulur, örneğin konak sayfası denetime ileti göndermek için bunu kullanabilir.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 ListBox denetimi, ana bilgisayar penceresinin alt öğesi olarak oluşturulur. Her iki pencerelerin da yüksekliği ve genişliği, yukarıda açıklanan oluşturucuya geçirilen değerlere ayarlanır. Bu, konak penceresinin ve denetiminin boyutunun sayfadaki ayrılmış alanla aynı olmasını sağlar.  Windows oluşturulduktan sonra örnek, konak penceresinin HWND 'sini içeren <xref:System.Runtime.InteropServices.HandleRef> bir nesne döndürür.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>Destroyıwindow ve WndProc uygulama  
 Ayrıca, <xref:System.Windows.Interop.HwndHost.WndProc%2A> ve<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> yöntemlerini<xref:System.Windows.Interop.HwndHost>geçersizkılmanızgerekir. <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> Bu örnekte, denetimin iletileri <xref:System.Windows.Interop.HwndHost.MessageHook> işleyici tarafından işlenir ve bu nedenle, ve <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> uygulamanız en az bir <xref:System.Windows.Interop.HwndHost.WndProc%2A> örnektir. Durumunda <xref:System.Windows.Interop.HwndHost.WndProc%2A>, iletinin işlendiğinin ve 0 `false` döndürülmeyeceğini belirtmek için olarak ayarlayın `handled` . İçin <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, pencereyi yok etmeniz yeterlidir.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>Denetimi sayfada barındırın  
 Denetimi sayfada barındırmak için önce `ControlHost` sınıfın yeni bir örneğini oluşturun. Denetimi (`ControlHostElement`) `ControlHost` içeren Border öğesinin yüksekliğini ve genişliğini oluşturucuya geçirin. Bu, ListBox 'ın doğru boyutlandırılmasını sağlar. Daha sonra `ControlHost` nesneyi <xref:System.Windows.Controls.Decorator.Child%2A> ana bilgisayarın <xref:System.Windows.Controls.Border>özelliğine atayarak sayfayı sayfada barındırabilirsiniz.  
  
 Örnek, <xref:System.Windows.Interop.HwndHost.MessageHook> `ControlHost` denetiminden ileti almak için öğesinin olayına bir işleyici ekler. Bu olay barındırılan pencereye gönderilen her ileti için oluşturulur. Bu durumda, denetim bildirimleri de dahil olmak üzere gerçek ListBox denetimini sarmalayan pencereye gönderilen iletilerdir. Örnek, denetimden bilgi almak ve içeriğini değiştirmek için SendMessage 'ı çağırır. Sayfanın denetimle nasıl iletişim kurduğu hakkındaki ayrıntılar, sonraki bölümde ele alınmıştır.  
  
> [!NOTE]
> SendMessage için iki PInvoke bildirimi olduğuna dikkat edin. Bu gereklidir çünkü biri bir dizeyi geçirmek `wParam` için parametresini kullandığından diğeri bir tamsayıyı iletmek için onu kullanır. Verilerin doğru şekilde sıralanmasını sağlamak için her imza için ayrı bir bildirime ihtiyacınız vardır.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>Denetim ve sayfa arasındaki Iletişimi Uygula  
 Denetimi, Windows iletilerini göndererek yönetebilirsiniz. Denetim, ana bilgisayar penceresine bildirim göndererek Kullanıcı onunla etkileşime geçtiğinde size bildirir. [WPF örneğinde Win32 ListBox denetimini barındırma](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control) , bunun nasıl çalıştığına dair birkaç örnek sağlayan bir kullanıcı arabirimi içerir:  
  
- Listeye bir öğe ekleyin.  
  
- Seçili öğeyi listeden Sil  
  
- Şu anda seçili olan öğenin metnini görüntüleyin.  
  
- Listedeki öğelerin sayısını görüntüleyin.  
  
 Kullanıcı aynı zamanda, Ayrıca, geleneksel bir Win32 uygulaması gibi, bu öğeye tıklayarak liste kutusunda bir öğe seçebilir. Görünen veriler, Kullanıcı bir öğe seçerek, ekleyerek veya ekleyerek liste kutusunun durumunu her değiştirdiğinde güncellenir.  
  
 Öğeleri eklemek için liste kutusuna bir [ `LB_ADDSTRING` ileti](/windows/desktop/Controls/lb-addstring)gönderin. Öğeleri silmek için Gönder [`LB_GETCURSEL`](/windows/desktop/Controls/lb-getcursel) ' e, geçerli seçimin dizinini alın ve sonra [`LB_DELETESTRING`](/windows/desktop/Controls/lb-deletestring) öğeyi silin. Örnek ayrıca, öğelerin [`LB_GETCOUNT`](/windows/desktop/Controls/lb-getcount)sayısını gösteren görünümü güncelleştirmek için döndürülen değeri de gönderir ve kullanır. Bu örneklerin [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) her ikisi de önceki bölümde açıklanan PInvoke bildirimlerinden birini kullanır.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Kullanıcı bir öğe seçtiğinde veya seçimlerini değiştirdiğinde, denetim konak penceresine bir [ `WM_COMMAND` ileti](/windows/desktop/menurc/wm-command)göndererek bildirir ve bu da sayfanın <xref:System.Windows.Interop.HwndHost.MessageHook> olayını oluşturur. İşleyici, ana bilgisayar penceresinin ana pencere yordamıyla aynı bilgileri alır. Ayrıca, `handled`bir Boolean değerine bir başvuru geçirir. ' İ `handled` , `true` iletiyi işlediğinin ve başka bir işleme gerek olmadığını belirtecek şekilde ayarlayın.  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command)çeşitli nedenlerle gönderilir, bu nedenle, işlemek istediğiniz bir olay olup olmadığını öğrenmek için bildirim KIMLIĞINI incelemeniz gerekir. Kimliği, `wParam` parametresinin üst sözcüğünde bulunur. Örnek, KIMLIĞI ayıklamak için bit düzeyinde işleçler kullanır. Kullanıcı, seçimini yapmış veya değiştirmiştir, KIMLIK olur [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange).  
  
 Alındığında, örnek, denetim bir [ `LB_GETCURSEL` ileti](/windows/desktop/Controls/lb-getcursel)göndererek seçili öğenin dizinini alır. [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange) Metni almak için önce bir <xref:System.Text.StringBuilder>oluşturun. Ardından, denetimi bir [ `LB_GETTEXT` ileti](/windows/desktop/Controls/lb-gettext)gönderirsiniz. Boş <xref:System.Text.StringBuilder> nesneyi `wParam` parametre olarak geçirin. [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) Döndüğünde<xref:System.Text.StringBuilder> , seçili öğenin metnini içerir. Bu kullanımı, [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) henüz başka bir PInvoke bildirimi gerektirir.  
  
 Son olarak, `handled` iletinin `true` işlendiğini göstermek için olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.HwndHost>
- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
- [İzlenecek yol: İlk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
