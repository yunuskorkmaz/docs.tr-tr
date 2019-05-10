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
ms.openlocfilehash: 2cfd8699afe48cb936ecf600c47508ef45781b43
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64605512"
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>İzlenecek yol: WPF içinde Win32 Denetimini Barındırma
Windows Presentation Foundation (WPF) uygulamaları oluşturmak için zengin bir ortam sağlar. Win32 kodu önemli ölçüde yatırımınız varsa, ancak bu en az bazılarını yeniden daha etkili olabilir, söz konusu kodu WPF uygulamanızda yerine tamamen yeniden yazın. WPF WPF sayfasında bir Win32 penceresinde barındırma için basit bir mekanizma sağlar.  
  
 Bu konu size uygulama [örnek WPF içinde Win32 ListBox denetimi barındırma](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control), konakları Win32 liste kutusu denetimi. Bu genel yordam herhangi bir Win32 penceresinde barındırma için genişletilebilir.  

<a name="requirements"></a>   
## <a name="requirements"></a>Gereksinimler  
 Bu konu, hem WPF hem de Windows API programlama temel olarak bilindiğini varsayar. WPF programlama temel bir giriş için bkz: [Başlarken](../getting-started/index.md). Windows API programlamaya giriş için çok sayıda kitaplardan herhangi birine konuyla ilgili özellikle bkz *Windows programlama* Charles Petzold ile.  
  
 Bu konuda eşlik eden örnek uygulandığından C#, kolaylaştırır Windows API'sine erişmeniz için Platform çağırma Hizmetleri (PInvoke) kullanın. PInvoke bazı konusunda yararlı ancak temel değildir.  
  
> [!NOTE]
>  Bu konuda, ilişkili örnekteki kod örnekleri içerir. Ancak, okunabilirlik için tam örnek kod içermez. Edinebilir veya gelen tam kod [bir WPF Örneği Win32 ListBox denetiminde barındırma](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Temel yordamı  
 Bu bölümde, bir WPF sayfasındaki bir Win32 penceresinde barındırma için temel yordamı açıklar. Kalan bölümler her adımın ayrıntılara gidin.  
  
 Temel barındırma yordam aynıdır:  
  
1. Pencereyi barındırmak için bir WPF sayfa uygulayın. Bir tekniktir oluşturmak için bir <xref:System.Windows.Controls.Border> barındırılan pencere için sayfanın bir bölümünü ayırmak için öğesi.  
  
2. Devralınan denetimini barındırmak için bir sınıf uygulamak <xref:System.Windows.Interop.HwndHost>.  
  
3. Bu sınıfta geçersiz kılma <xref:System.Windows.Interop.HwndHost> sınıf üyesi <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>.  
  
4. Barındırılan pencerenin alt WPF sayfasını içeren bir pencere öğesi olarak oluşturun. Geleneksel WPF programlama açıkça gerekmez ancak bunu kullanacağından, barındırma sayfası işleyici (HWND) ile bir penceredir. HWND sayfasını aldığınız aracılığıyla `hwndParent` parametresinin <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> yöntemi. Bu HWND alt sitesi olarak barındırılan pencere oluşturulmalıdır.  
  
5. Ana pencere oluşturduktan sonra barındırılan penceresinin HWND döndürür. Bir veya daha fazla Win32 denetimini barındırmak istiyorsanız, genellikle bir konak penceresini HWND alt sitesi olarak oluşturur ve konak penceresinin denetimleri alt öğesi yapın. Bir ana penceresinde denetimleri sarmalama HWND sınırında bildirimleri ile belirli bazı Win32 sorunlarla ilgilenen denetimlerden bildirim almak, WPF sayfası için basit bir yol sağlar.  
  
6. Bildirim alt denetimler gibi ana pencerenin gönderilen Seçili iletileri işler. Bunu yapmanın iki yolu vardır.  
  
    - Barındırma sınıfınızdaki iletileri işlemek isterseniz, geçersiz kılma <xref:System.Windows.Interop.HwndHost.WndProc%2A> yöntemi <xref:System.Windows.Interop.HwndHost> sınıfı.  
  
    - WPF iletileri işleyen, işlemek isterseniz <xref:System.Windows.Interop.HwndHost> sınıfı <xref:System.Windows.Interop.HwndHost.MessageHook> arka plan kod olayı. Bu olay, barındırılan pencere tarafından alınan her ileti için gerçekleşir. Bu seçeneği belirlerseniz, hala tanımlamalısınız <xref:System.Windows.Interop.HwndHost.WndProc%2A>, ancak yalnızca en az bir uygulama gerekir.  
  
7. Geçersiz kılma <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> ve <xref:System.Windows.Interop.HwndHost.WndProc%2A> yöntemlerinin <xref:System.Windows.Interop.HwndHost>. Karşılamak için bu yöntemleri geçersiz kılmanız gerekir <xref:System.Windows.Interop.HwndHost> sözleşme, ancak yalnızca gerekebilir en az bir uygulama sağlamak.  
  
8. Arka plan kod dosyanızı denetim sınıf barındırma örneği oluşturun ve bir alt öğesi yapın <xref:System.Windows.Controls.Border> pencereyi barındırması amaçlanan öğesi.  
  
9. Göndererek barındırılan pencere ile iletişim kurmak [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] iletilerini ve denetimlerinin gönderdiği bildirimler gibi kendi alt Windows iletilerini işleme.  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>Sayfa düzeni uygulama  
 ListBox denetimi barındıran WPF sayfanın düzeni, iki bölgeleri oluşur. Sayfanın sol tarafındaki sağlayan birkaç WPF denetimleri barındıran bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Win32 denetimi işlemek sağlar. Sayfanın sağ üst köşesinde kare bölgesi için barındırılan ListBox denetimi vardır.  
  
 Bu düzen uygulayan bir kod oldukça basittir. Kök öğe bir <xref:System.Windows.Controls.DockPanel> iki alt öğeye sahip. İlki bir <xref:System.Windows.Controls.Border> ListBox denetiminde bir öğe. Bu, 200 x 200 kare açılırken bir sayfanın sağ üst köşesinde kaplar. İkinci bir <xref:System.Windows.Controls.StackPanel> bilgileri görüntüleyen ve ListBox denetimini ayarlayarak değiştirmenize izin veren WPF denetimleri kümesini içeren bir öğe kullanıma sunulan birlikte çalışabilirlik özellikleri. Alt öğelerin her biri için <xref:System.Windows.Controls.StackPanel>, bu öğeler nelerdir veya ne yaptıklarıyla ilgili ayrıntılar için kullanılan çeşitli öğeleri için başvuru materyalleri bakın, bu örnek kodda listelenmiştir, ancak değişmeyecek (temel burada açıklanan birlikte çalışabilirlik modeli herhangi biri gerekmez, bunlar için örnek bazı etkileşim eklemek için sağlanır).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Microsoft Win32 denetimini barındırmak için bir sınıf uygulama  
 Bu örnek setinin aslında ControlHost.cs denetimi barındıran sınıftır. Devraldığı <xref:System.Windows.Interop.HwndHost>. Genişliği ve yüksekliği için karşılık gelen iki parametre, yükseklik ve genişlik, Oluşturucusu alır <xref:System.Windows.Controls.Border> ListBox denetiminde bir öğe. Bu değerler daha sonra Denetim eşleşmeleri boyutunu emin olmak için kullanılan <xref:System.Windows.Controls.Border> öğesi.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Yok sabitleri de bir dizi. Bu sabitler Winuser.H'den büyük ölçüde alınır ve geleneksel adlarını Win32 işlevlerini çağırırken kullanmanıza izin verir.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Microsoft Win32 pencere oluşturmak için BuildWindowCore'u Geçersiz kılma  
 Sayfa tarafından barındırılan ve sayfa penceresi arasında bağlantı yapmak Win32 pencere oluşturmak için bu yöntemi geçersiz. Bu örnek bir ListBox denetimini barındırma gerektirdiğinden, iki windows oluşturulur. İlk WPF sayfası tarafından gerçekten barındırılan bir penceredir. ListBox denetimi, bir pencerenin alt öğesi oluşturulur.  
  
 Bu yaklaşım denetiminden bildirim alma işlemini basitleştirmek için nedeni. <xref:System.Windows.Interop.HwndHost> Sınıfı barındırması penceresine gönderilen iletileri işlemek olanak tanır. Bir Win32 Konak doğrudan denetim, denetimin iç ileti döngüsü için gönderilen iletiler alırsınız. Denetim ve bu iletileri gönderme görüntüleyebilirsiniz, ancak denetimin üst pencereye gönderen bildirimleri almazsınız. Bu, diğerlerinin yanı sıra kullanıcı denetimle etkileşim kurduğunda hiçbir şekilde algılama sahip olduğunuz anlamına gelir. Bunun yerine, bir konak penceresini oluşturun ve bu pencerenin alt denetimi yapın. Bu, denetim tarafından gönderilen bildirimleri dahil olmak üzere ana pencere için iletileri işlemek üzere sağlar. Ana pencerenin daha basit bir sarmalayıcı denetimi için biraz daha fazla olduğundan kolaylık olması için paket için bir ListBox denetimi olarak adlandırılır.  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>ListBox denetimi ve konak penceresinin oluşturma  
 PInvoke denetimi için ana pencere oluşturma ve kaydetme pencere sınıfı oluşturmak için kullanın ve benzeri. Ancak, bir çok basit bir yaklaşım bir pencere ile önceden tanımlanmış "statik" Pencere sınıfını oluşturmaktır. Bu pencere yordamını denetiminden bildirim almak isteyen ve minimum kodlama gerektiren sağlar.  
  
 Ana sayfa için Denetim iletileri göndermek için kullanabilir HWND denetimi salt okunur özelliği aracılığıyla kullanıma sunulur.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 ListBox denetimi ana penceresinin alt olarak oluşturulur. Hem windows genişliği ve yüksekliği yukarıda açıklanan oluşturucuya geçirilen değerlere ayarlanır. Bu, Denetim ve konak penceresinin boyutunu ayrılmış alanı sayfasında aynı olmasını sağlar.  Windows oluşturulduktan sonra örnek döndüren bir <xref:System.Runtime.InteropServices.HandleRef> ana penceresinin HWND içeren nesne.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>DestroyWindow ve WndProc  
 Ek olarak <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>, geçersiz kılmalısınız <xref:System.Windows.Interop.HwndHost.WndProc%2A> ve <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> yöntemlerinin <xref:System.Windows.Interop.HwndHost>. Bu örnekte, Denetim iletileri tarafından işlenen <xref:System.Windows.Interop.HwndHost.MessageHook> işleyicisi, bu nedenle uygulamasını <xref:System.Windows.Interop.HwndHost.WndProc%2A> ve <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> düzeydedir. Durumunda, <xref:System.Windows.Interop.HwndHost.WndProc%2A>ayarlayın `handled` için `false` ileti işlenmedi belirtmek ve 0 döndürür. İçin <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, pencere sadece yok.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>Ana sayfada denetimi  
 Sayfasında denetimini barındırmak için önce yeni bir örneğini oluşturun `ControlHost` sınıfı. Denetimi içeren kenarlık öğe genişliği ve yüksekliği geçirin (`ControlHostElement`) için `ControlHost` Oluşturucusu. Bu liste doğru boyutlandırılır sağlar. Ardından atayarak sayfasındaki denetimi ana `ControlHost` nesnesini <xref:System.Windows.Controls.Decorator.Child%2A> özelliği konağının <xref:System.Windows.Controls.Border>.  
  
 Örnek bir işleyici ekler <xref:System.Windows.Interop.HwndHost.MessageHook> olayı `ControlHost` denetim iletileri almak için. Bu olay, barındırılan penceresine gönderilen her ileti için tetiklenir. Bu durumda, denetimin bildirimleri dahil olmak üzere gerçek ListBox denetimini sarar penceresine gönderilen iletileri şunlardır. Örnek SendMessage denetiminden bilgi edinmek ve içeriğini değiştirmek için çağırır. Sayfa denetimiyle nasıl iletişim kurduğu ayrıntılarını, sonraki bölümde ele alınmıştır.  
  
> [!NOTE]
>  İki PInvoke bildirimi için SendMessage olduğuna dikkat edin. Bunun gerekli olmasının nedeni kullanan tek `wParam` parametresi bir dize ve diğer iletmek için bir tamsayı geçirmek için bunu kullanır. Verileri doğru şekilde sıralanmış olduğundan emin olmak her bir imza için ayrı bir bildirim ihtiyacınız vardır.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>Uygulama sayfası ile Denetim arasındaki iletişimi  
 Windows iletiler göndererek denetimi değiştirebilirsiniz. Kullanıcı için konak penceresinin bildirim göndererek ile etkileşim kurduğunda denetimi size bildirir. [WPF'de Win32 ListBox denetimini barındırma](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control) örnek bunun nasıl çalıştığını, çeşitli örnekler sağlayan bir kullanıcı Arabirimi içerir:  
  
- Bir öğeyi listeye ekleyin.  
  
- Seçili öğeyi listeden silin  
  
- Seçili öğenin metni görüntüler.  
  
- Öğe, listede görüntüler.  
  
 Geleneksel bir Win32 uygulaması için olduğu gibi kullanıcının da öğeyi liste kutusunda üzerine tıklayarak seçebilirsiniz. Görüntülenen verileri seçme, ekleme veya bir öğe ekleme kullanıcının liste kutusunun durumu her değiştiğinde güncelleştirilir.  
  
 Liste kutusu öğeleri eklemek için göndermek bir [ `LB_ADDSTRING` ileti](/windows/desktop/Controls/lb-addstring). Öğeleri silmek için gönderme [ `LB_GETCURSEL` ](/windows/desktop/Controls/lb-getcursel) geçerli seçimin indisini almak ve ardından [ `LB_DELETESTRING` ](/windows/desktop/Controls/lb-deletestring) öğeyi silmek için. Örnek ayrıca gönderir [ `LB_GETCOUNT` ](/windows/desktop/Controls/lb-getcount)ve öğe sayısını gösteren görüntü güncelleştirmek için döndürülen değer kullanır. ' In iki örneği [ `SendMessage` ](/windows/desktop/api/winuser/nf-winuser-sendmessage) önceki bölümde açıklanan PInvoke bildirimleri birini kullanın.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Kullanıcı bir öğeyi seçer veya seçimi değiştirir denetimin ana penceresine göndererek bildirir bir [ `WM_COMMAND` ileti](/windows/desktop/menurc/wm-command), oluşturursa <xref:System.Windows.Interop.HwndHost.MessageHook> sayfa için olay. Ana pencere yordamına aynı bilgileri ana penceresinin işleyici alır. Ayrıca bir Boolean değerine bir başvuru geçirir `handled`. Ayarladığınız `handled` için `true` ileti işlenmiş olduğunu ve başka bir işleme gerek olmadığını göstermek için.  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command) işlemek istediğiniz bir olay olup olmadığını belirlemek için bildirim kimliği incelemeniz gerekir böylece çeşitli nedenlerle gönderilir. Kimliği üst sınırı içinde yer alan `wParam` parametresi. Örnek kimliği ayıklamak için bit düzeyinde işleçler kullanır. Kullanıcının yapılan veya değiştirilen seçimi, kimliği olacaktır [ `LBN_SELCHANGE` ](/windows/desktop/Controls/lbn-selchange).  
  
 Zaman [ `LBN_SELCHANGE` ](/windows/desktop/Controls/lbn-selchange) olan alınan örnek seçili öğenin dizinini denetimi göndererek alır bir [ `LB_GETCURSEL` ileti](/windows/desktop/Controls/lb-getcursel). Metin iletisini almanız için önce oluşturmanız bir <xref:System.Text.StringBuilder>. Ardından Denetim gönderdiğiniz bir [ `LB_GETTEXT` ileti](/windows/desktop/Controls/lb-gettext). Boş geçmesi <xref:System.Text.StringBuilder> nesnesinin `wParam` parametresi. Zaman [ `SendMessage` ](/windows/desktop/api/winuser/nf-winuser-sendmessage) döndürür, <xref:System.Text.StringBuilder> seçilen öğenin metnini içerir. Bu kullanımı [ `SendMessage` ](/windows/desktop/api/winuser/nf-winuser-sendmessage) henüz başka bir PInvoke bildirimi gerektirir.  
  
 Son olarak, ayarlama `handled` için `true` iletinin işlendiğini göstermek için.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.HwndHost>
- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
- [İzlenecek yol: İlk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
