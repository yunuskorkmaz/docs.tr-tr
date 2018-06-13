---
title: WPF ve Win32 Birlikte Çalışması
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
ms.openlocfilehash: 8a0e27d46248bdfd782c2cf650faaf8f3bc29960
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549428"
---
# <a name="wpf-and-win32-interoperation"></a>WPF ve Win32 Birlikte Çalışması
Bu konu çalışmasını nasıl bir bakış sunar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamaları oluşturmak için zengin bir ortam sağlar. Önemli ölçüde yatırımınız varsa [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kodu, onu olabilir bazı kodun yeniden kullanmak daha etkili.  
  

  
<a name="basics"></a>   
## <a name="wpf-and-win32-interoperation-basics"></a>WPF ve Win32 birlikte çalışabilirlik temelleri  
 Arasında birlikte çalışabilirlik için iki temel tekniği vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu.  
  
-   Ana bilgisayar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi. Bu teknik ile gelişmiş grafik yeteneklerini kullanabilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] standart çerçevesinin içinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresini açın ve uygulama.  
  
-   Konak bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Bu teknik ile var olan bir özel kullanabilirsiniz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] diğer bağlamında denetim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik ve veri sınırlarında geçirin.  
  
 Her tekniğin bu konudaki kavramsal olarak sunulmuştur. Barındırma daha kod odaklı bir çizim için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], bkz: [izlenecek yol: barındırma WPF içeriği Win32](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md). Barındırma daha kod odaklı bir çizim için [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [izlenecek yol: bir WPF Win32 denetimi barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md).  
  
<a name="projects"></a>   
## <a name="wpf-interoperation-projects"></a>WPF birlikte çalışabilirlik projeleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] yönetilen kod, ancak çoğu mevcut [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programları dilini yönetilmeyen [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Çağıramazsınız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] true program yönetilmeyen. Kullanarak ancak `/clr` seçeneğini [!INCLUDE[TLA#tla_visualcpp](../../../../includes/tlasharptla-visualcpp-md.md)] derleyici, yönetilen ve yönetilmeyen Burada, sorunsuz bir şekilde karışık bir karma yönetilen-yönetilmeyen program oluşturabilir [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] çağrıları.  
  
 Bir proje düzeyi olası olduğundan, derlenemiyor [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] içine dosyaları bir [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] projesi.  Bunu düzeltmek için birkaç proje bölme tekniği vardır.  
  
-   Bir C# tüm içeren dll dosyası oluşturun, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olarak derlenmiş bir bütünleştirilmiş kod sayfaları ve daha sonra [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] yürütülebilir dahil [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] bir başvuru olarak.  
  
-   C# için yürütülebilir oluşturma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik ve onu sahip başvuran bir [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] içeren [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] içeriği.  
  
-   Kullanım <xref:System.Windows.Markup.XamlReader.Load%2A> herhangi yüklemek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] derleme yerine çalışma zamanında, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
-   Kullanmayın [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] hiç ve tüm yazma, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesi ağacından derleme kodunda <xref:System.Windows.Application>.  
  
 Hangi yaklaşımın sizin için en iyi kullanın.  
  
> [!NOTE]
>  Değil kullandıysanız [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] önce "Yeni" bazı anahtar sözcükler gibi fark edebilirsiniz `gcnew` ve `nullptr` birlikte çalışabilirlik kod örnekleri içinde. Bu anahtar sözcükler eski çift alt çizgi sözdizimi yerine geçen (`__gc`) ve yönetilen kod için doğal bir söz dizimi sağlayın [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Daha fazla bilgi edinmek için [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] yönetilen özellikleri, bkz. [çalışma zamanı platformları için bileşen uzantıları](/cpp/windows/component-extensions-for-runtime-platforms) ve [, C + Hello +/ CLI](http://go.microsoft.com/fwlink/?LinkId=98739).  
  
<a name="hwnds"></a>   
## <a name="how-wpf-uses-hwnds"></a>WPF Cwnd'lerden nasıl kullanır  
 En iyi yapmak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] "HWND interop" ihtiyacınız anlamak nasıl [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Cwnd'lerden kullanır. Her HWND için karıştıramazsınız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ile işleme [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] işleme veya [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]  /  [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] işleme. Bu, etkileri sayısına sahip. Öncelikle, bu işleme modeller hiç karışımı için birlikte çalışabilirlik çözümünü oluşturun ve birlikte çalışabilirlik belirtilen kesimleri kullanmayı tercih ederseniz her bir işleme modeli için kullanmanız gerekir. Ayrıca, işleme davranışını ne birlikte çalışabilirlik çözümünüzü gerçekleştirmek için bir "Hava Sahası" kısıtlama oluşturur. "Hava Sahası" kavramı konusunda daha ayrıntılı açıklanmıştır [teknoloji bölgeleri genel bakış](../../../../docs/framework/wpf/advanced/technology-regions-overview.md).  
  
 Tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeleri ekranında sonuçta bir HWND tarafından yedeklenir. Oluştururken bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window>, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en üst düzey bir HWND oluşturduğu ve kullandığı bir <xref:System.Windows.Interop.HwndSource> yerleştirilecek <xref:System.Windows.Window> ve kendi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND içinde içerik.  Geri kalanı, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamadaki içerik, tekil HWND paylaşır. Menüleri, birleşik giriş kutusu açılan listelerini ve diğer açılır pencereleri bir özel durumdur. Bu öğeler, kendisini olmasının nedeni, kendi üst düzey bir pencere oluşturma bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] menü büyük olasılıkla içerdiği HWND penceresi kenar gidin. Kullandığınızda <xref:System.Windows.Interop.HwndHost> HWND içine yerleştirilecek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bildirir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] yeni alt HWND göreli konumunu nasıl [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND.  
  
 Bir ilişkili HWND için saydamlığı içinde ve arasında her HWND kavramdır. Bu konuda ayrıca ele alınmıştır [teknoloji bölgeleri genel bakış](../../../../docs/framework/wpf/advanced/technology-regions-overview.md).  
  
<a name="hosting_a_wpf_page"></a>   
## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>Bir Microsoft Win32 penceresinde WPF içeriği barındırma  
 Barındırma için anahtarı bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] üzerinde bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi <xref:System.Windows.Interop.HwndSource> sınıfı. Bu sınıf sarmalar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresinde, böylece [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik birleştirilmiş içine, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] alt pencere olarak. Aşağıdaki yaklaşımlardan birleştirir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tek bir uygulamada.  
  
1.  Uygulama, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği (içerik kök öğesi) olarak yönetilen bir sınıf. Genellikle, birden çok alt öğelerini içerebilir ve/veya bir kök öğe kullanılan sınıfları birinden sınıfının devraldığı <xref:System.Windows.Controls.DockPanel> veya <xref:System.Windows.Controls.Page>. Sonraki adımlarda bu sınıf olarak adlandırılır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik sınıfı ve sınıf örneklerini denir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesneleri.  
  
2.  Uygulama bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulama [!INCLUDE[TLA2#tla_cppcli](../../../../includes/tla2sharptla-cppcli-md.md)]. Var olan başlatıyorsanız yönetilmeyen [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] uygulama, genellikle etkinleştirebilirsiniz, yönetilen kod eklemek için proje ayarlarınızı değiştirerek çağırmak `/clr` derleyici bayrağını (ne desteklemekiçingerekliolabilirtamkapsamını`/clr`derleme bu konuda açıklanan değil).  
  
3.  İş parçacığı modelini tek iş parçacıklı grup (STA için) ayarlayın. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bu iş parçacığı modelini kullanır.  
  
4.  Pencere yordamı WM_CREATE bildiriminde işleyin.  
  
5.  İşleyici (veya işleyici çağıran bir işlev içinde) aşağıdakileri yapın:  
  
    1.  Yeni bir <xref:System.Windows.Interop.HwndSource> üst pencere HWND nesnesiyle olarak kendi `parent` parametresi.  
  
    2.  Bir örneğini oluşturun, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik sınıfı.  
  
    3.  Bir başvuru atamak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesnesine <xref:System.Windows.Interop.HwndSource> nesne <xref:System.Windows.Interop.HwndSource.RootVisual%2A> özelliği.  
  
    4.  <xref:System.Windows.Interop.HwndSource> Nesne <xref:System.Windows.Interop.HwndSource.Handle%2A> özelliği pencere işleyicisi (HWND) içerir. Uygulamanızın yönetilmeyen parçası kullanabileceğiniz bir HWND almak için cast `Handle.ToPointer()` HWND için.  
  
6.  Bir başvuru tutan statik bir alan içeren bir yönetilen sınıf uygulama, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesnesi. Bu sınıf için bir başvuru almanıza yardımcı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesnesinden, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu, ancak daha da önemlisi engeller, <xref:System.Windows.Interop.HwndSource> engeller yanlışlıkla toplanacak.  
  
7.  ' Den bildirim almak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] biri veya daha fazlası için bir işleyici ekleyerek içerik nesnesini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesne olayları.  
  
8.  İletişim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerini ayarlama, çağrı yöntemleri, vb. için statik alanda depolanan başvuru kullanarak içerik nesnesi.  
  
> [!NOTE]
>  Bazılarını veya tümünü yapabileceğiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik adım bir sınıf tanımı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ayrı bir derleme üretmek ve ardından referans içerik sınıfı varsayılan kısmi sınıfını kullanarak. Genellikle içerse de bir <xref:System.Windows.Application> nesnesi derleme bir parçası olarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir derlemeye, kullandığı bitmeyen <xref:System.Windows.Application> birlikte çalışabilirlik bir parçası olarak, yalnızca bir veya daha fazla kök sınıflar için kullandığınız [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvurulan dosyaları için uygulama tarafından ve bunların kısmi sınıflar başvuru. Yordamın geri kalanı, yukarıda özetlenen temelde benzer.  
>   
>  Bu adımların her biri kodlarda konuda gösterilmiştir [izlenecek yol: barındırma WPF içeriği Win32](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md).  
  
<a name="hosting_an_hwnd"></a>   
## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>WPF Microsoft Win32 penceresinde barındırma  
 Barındırma için anahtarı bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] diğer pencereye [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik <xref:System.Windows.Interop.HwndHost> sınıfı. Bu sınıf penceresinde saran bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eklenebilir öğesi bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğe ağacı. <xref:System.Windows.Interop.HwndHost> Ayrıca destekler [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] barındırılan pencere için iletilerini işlemek gibi görevleri yapmak izin verir. Temel yordamı şöyledir:  
  
1.  İçin bir öğe ağacı oluşturma bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama (olabilir kodu veya işaretleme). Öğe ağacındaki bir uygun ve izin verilen noktası bulmasını nerede <xref:System.Windows.Interop.HwndHost> uygulaması bir alt öğesi eklenebilir. Bu adımları kalanı bu öğe rezerve öğesi olarak adlandırılır.  
  
2.  Öğesinden türetilen <xref:System.Windows.Interop.HwndHost> tutan bir nesne oluşturmak için [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] içeriği.  
  
3.  Bu konak sınıfında geçersiz kılma <xref:System.Windows.Interop.HwndHost> yöntemi <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>. Barındırılan pencere HWND döndür. Döndürülen penceresinin alt pencere olarak gerçek control(s) sarmalamak isteyebilirsiniz; bir ana bilgisayar penceresinde denetimleri sarmalama için basit bir yol sağlar, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerden bildirimleri almak içerik. Bu teknik bazı için düzeltmek yardımcı [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] denetimden sınırlar ileti işleme ile ilgili sorunlar.  
  
4.  Geçersiz kılma <xref:System.Windows.Interop.HwndHost> yöntemleri <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> ve <xref:System.Windows.Interop.HwndHost.WndProc%2A>. Özellikle yönetilmeyen nesnelerin referansları oluşturduysanız Burada amaç temizleme işlemek ve barındırılan içerik başvuruları kaldırmak için ' dir.  
  
5.  Arka plan kodu dosyanızda, barındırma sınıfı denetim örneği oluşturun ve rezerve öğesinin bir alt yapın. Olay işleyici gibi genellikle kullanırsınız <xref:System.Windows.FrameworkElement.Loaded>, ya da parçalı sınıf oluşturucu kullanın. Ancak, bir çalışma zamanı davranışını birlikte çalışabilirlik içeriğinden de ekleyebilirsiniz.  
  
6.  Denetim bildirimleri gibi işlem seçilen pencere iletileri. İki yaklaşım vardır. Tercih ettiğiniz kolaylık programlama büyük ölçüde bir konudur şekilde her ikisi de aynı ileti akışı erişim sağlar.  
  
    -   Uygulama ileti geçersiz kılma (yalnızca kapatma iletileri) tüm iletiler için işleme <xref:System.Windows.Interop.HwndHost> yöntemi <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
    -   Barındırma sahip [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesi işlem iletileri işleyerek <xref:System.Windows.Interop.HwndHost.MessageHook> olay. Bu olay barındırılan pencere ana penceresi yordamına gönderilen her ileti için oluşturulur.  
  
    -   İşlem kullanımı dışında Windows iletileri işleyemez <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
7.  Platform kullanarak barındırılan pencere ile iletişim kuran yönetilmeyen çağrılacak çağırma `SendMessage` işlevi.  
  
 Aşağıdaki adımları fare girdisi ile çalışan bir uygulama oluşturur. Uygulama tarafından barındırılan pencerenizi için sekme destek ekleyebilmesi <xref:System.Windows.Interop.IKeyboardInputSink> arabirimi.  
  
 Bu adımların her biri kodlarda konuda gösterilmiştir [izlenecek yol: bir WPF Win32 denetimi barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md).  
  
### <a name="hwnds-inside-wpf"></a>Cwnd'lerden iç WPF  
 Düşünebilirsiniz <xref:System.Windows.Interop.HwndHost> özel bir denetim olarak. (Teknik olarak <xref:System.Windows.Interop.HwndHost> olan bir <xref:System.Windows.FrameworkElement> sınıfı, türetilmemiş bir <xref:System.Windows.Controls.Control> türetilmiş sınıf, ancak bir denetim birlikte çalışabilirlik amaçları için kabul edilebilir.) <xref:System.Windows.Interop.HwndHost> soyutlar arka plandaki [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] barındırılan içerik doğası şekilde geri kalanı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işlemek ve işlem giriş başka bir denetim benzeri nesnesi olacak barındırılan içerik göz önünde bulundurur. <xref:System.Windows.Interop.HwndHost> genellikle diğer gibi davranır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>, çıkış (çizim ve grafikler) çevresinde önemli bazı farklar vardır ve temel Cwnd'lerden sınırlamalar göre giriş (fare ve klavye) destekler.  
  
#### <a name="notable-differences-in-output-behavior"></a>Çıktı davranış önemli farklılıkları  
  
-   <xref:System.Windows.FrameworkElement>, olduğu <xref:System.Windows.Interop.HwndHost> temel sınıfı, UI değişiklikleri kapsıyor çeşitli özelliklere sahiptir. Bunlar gibi özellikler içeren <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>, o öğesi üst öğe olarak içinde öğelerin düzenini değiştirir. Ancak, bu özelliklerin çoğu, olabildiğince eşlenmemiş [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] eşdeğerleri, olsa da bu tür eşdeğerleri mevcut olabilir. Çok bu özelliklerin ve anlamlarını pratik olmasını eşlemeleri çok oluşturma teknolojisi özgüdür. Bu nedenle, gibi özellikleri ayarlamak <xref:System.Windows.FrameworkElement.FlowDirection%2A> üzerinde <xref:System.Windows.Interop.HwndHost> hiçbir etkisi olmaz.  
  
-   <xref:System.Windows.Interop.HwndHost> bir dönüşüm tarafından etkilenen Döndürülmüş, ölçeklendirilmiş, çarpık veya aksi olamaz.  
  
-   <xref:System.Windows.Interop.HwndHost> desteklemediği <xref:System.Windows.UIElement.Opacity%2A> özelliği (Alfa karışım). İçindeki içerik varsa <xref:System.Windows.Interop.HwndHost> gerçekleştirir <xref:System.Drawing> kendisini ihlalinin değil, alfa bilgi, içeren işlemlere ancak <xref:System.Windows.Interop.HwndHost> tamamını yalnızca opaklık desteklediği = 1.0 (% 100).  
  
-   <xref:System.Windows.Interop.HwndHost> diğer en üstünde görünür [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aynı üst düzey pencere öğeleri. Ancak, bir <xref:System.Windows.Controls.ToolTip> veya <xref:System.Windows.Controls.ContextMenu> oluşturulan menü ayrı bir üst düzey penceresi ve bu nedenle doğru ile davranacak <xref:System.Windows.Interop.HwndHost>.  
  
-   <xref:System.Windows.Interop.HwndHost> Kırpma bölgesinin kendi üst uymaz <xref:System.Windows.UIElement>. Put çalışırsanız, bu büyük olasılıkla söz konusu bir <xref:System.Windows.Interop.HwndHost> kaydırma bölgesi sınıfında veya <xref:System.Windows.Controls.Canvas>.  
  
#### <a name="notable-differences-in-input-behavior"></a>Giriş davranış önemli farklılıkları  
  
-   Giriş aygıtları içinde kapsamındaki sırada genel olarak, <xref:System.Windows.Interop.HwndHost> barındırılan [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bölge, giriş olaylarını Git doğrudan [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
-   Fare üzerinden olsa <xref:System.Windows.Interop.HwndHost>, uygulamanızın ROM'u [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fare olayları ve değerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliği <xref:System.Windows.UIElement.IsMouseOver%2A> olacaktır `false`.  
  
-   Sırada <xref:System.Windows.Interop.HwndHost> klavye odağı olan uygulamanızı değil alacak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klavye olayları ve değerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliği <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> olacaktır `false`.  
  
-   Zaman içinde olduğunu <xref:System.Windows.Interop.HwndHost> ve içinde başka bir denetim dönüştüğünde <xref:System.Windows.Interop.HwndHost>, uygulamanızın değil alacak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olayları <xref:System.Windows.UIElement.GotFocus> veya <xref:System.Windows.UIElement.LostFocus>.  
  
-   Kalem özellikleri ve olayları benzer ve Kalem üzerinden olsa bilgi bildirmeyen ilgili <xref:System.Windows.Interop.HwndHost>.  
  
<a name="tabbing_mnemonics_accelerators"></a>   
## <a name="tabbing-mnemonics-and-accelerators"></a>Sekme, anımsatıcıları ve Hızlandırıcıları  
 <xref:System.Windows.Interop.IKeyboardInputSink> Ve <xref:System.Windows.Interop.IKeyboardInputSite> arabirimleri bir sorunsuz klavye deneyimi mixed oluşturmanıza izin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamalar:  
  
-   Arasında sekmeyle gitmeyi [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşenleri  
  
-   Anımsatıcıları ve odak Win32 bileşeni içinde ve WPF bileşeni içinde olduğunda olduğunda, hem de iş Hızlandırıcıları.  
  
 <xref:System.Windows.Interop.HwndHost> Ve <xref:System.Windows.Interop.HwndSource> sınıflarının her ikisi de sağlayan uygulamaları <xref:System.Windows.Interop.IKeyboardInputSink>, ancak bunlar daha Gelişmiş senaryolar için istediğiniz tüm giriş iletileri işlemek değil. İstediğiniz klavye davranışı elde etmek üzere uygun yöntemleri geçersiz kılın.  
  
 Yalnızca arabirimler arasında geçiş üzerinde olanlar için destek sağlayan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bölgeleri. İçinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bölge davranışı sekme tamamen tarafından denetlenir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] iletmelisiniz mantığı varsa uygulanmadı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Interop.HwndHost>  
 <xref:System.Windows.Interop.HwndSource>  
 <xref:System.Windows.Interop>  
 [İzlenecek yol: WPF'te Win32 Denetimi Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md)  
 [İzlenecek yol: Win32'de WPF Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md)
