---
title: WPF ve Win32 Birlikte Çalışması
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
ms.openlocfilehash: 71c454edc6a124f732f1e6b56e25c28671fa11b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053177"
---
# <a name="wpf-and-win32-interoperation"></a>WPF ve Win32 Birlikte Çalışması
Bu konuda çalışmak bir bakış sunulmaktadır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kod. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamaları oluşturmak için zengin bir ortam sağlar. Önemli ölçüde yatırımınız varsa [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kodu olabilir bazı kodu yeniden kullanmak daha etkili.  

<a name="basics"></a>   
## <a name="wpf-and-win32-interoperation-basics"></a>WPF ve Win32 birlikte çalışabilirlik temelleri  
 Arasında birlikte çalışma için iki temel teknik vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kod.  
  
- Konak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi. Bu teknikte Gelişmiş grafik yeteneklerini kullanabilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] standart framework içindeki [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pencere ve uygulama.  
  
- Konak bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Bu teknik ile var olan bir özel kullanabilirsiniz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] denetim diğer bağlamında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik ve sınırları arasında verileri geçirebilirsiniz.  
  
 Bu tekniklerin, bu konudaki kavramsal olarak sunulmuştur. Daha fazla kod odaklı bir gösterim barındırma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], bkz: [izlenecek yol: Win32'de WPF barındırma](walkthrough-hosting-wpf-content-in-win32.md). Daha fazla kod odaklı bir gösterim barındırma [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [izlenecek yol: WPF içinde Win32 denetimini barındırma](walkthrough-hosting-a-win32-control-in-wpf.md).  
  
<a name="projects"></a>   
## <a name="wpf-interoperation-projects"></a>WPF birlikte çalışabilirlik projeleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] yönetilen kod, ancak çoğu mevcut [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programlar yazılır yönetilmeyen [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Çağıramazsınız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] gerçek bir program yönetilmeyen. Kullanarak ancak `/clr` seçeneğini [!INCLUDE[TLA#tla_visualcpp](../../../../includes/tlasharptla-visualcpp-md.md)] derleyici, yönetilen ve yönetilmeyen Burada, sorunsuz bir şekilde karışık bir karışık yönetilen-yönetilmeyen program oluşturabilirsiniz [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] çağırır.  
  
 Bir proje düzeyi komplikasyon olduğundan, derlenemez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyalarınızı bir [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] proje.  Bunu düzeltmek için birçok proje bölme teknikler vardır.  
  
- Bir C# tüm içeren DLL oluşturma, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olarak derlenmiş bir bütünleştirilmiş kod sayfaları ve ardından, [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] yürütülebilir dosya içeren [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] başvuru olarak.  
  
- C# için yürütülebilir oluşturma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik ve bu başvuru bir [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] içeren [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] içeriği.  
  
- Kullanım <xref:System.Windows.Markup.XamlReader.Load%2A> herhangi yüklenecek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] derleme yerine çalışma zamanında, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
- Kullanmayın [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] hiç ve tüm yazma, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğe ağacı oluşturma kodunda <xref:System.Windows.Application>.  
  
 Hangi yaklaşımın sizin için en uygun kullanın.  
  
> [!NOTE]
>  Kullanmadıysanız, [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] önce "Yeni" bazı anahtar sözcükler gibi fark edebilirsiniz `gcnew` ve `nullptr` birlikte çalışabilirlik kod örneklerinde. Bu anahtar sözcükler eski çift alt çizgi söz dizimi yerine geçen (`__gc`) ve yönetilen kod için daha doğal bir söz dizimi sağlar [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Hakkında daha fazla bilgi edinmek için [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] yönetilen özellikler bkz [çalışma zamanı platformları için bileşen uzantıları](/cpp/windows/component-extensions-for-runtime-platforms) ve [, C + Hello +/ CLI](https://go.microsoft.com/fwlink/?LinkId=98739).  
  
<a name="hwnds"></a>   
## <a name="how-wpf-uses-hwnds"></a>WPF Cwnd'lerden kullanma  
 En iyi hale getirmek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] "HWND birlikte" ihtiyacınız anlamak nasıl [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Cwnd'lerden kullanır. Herhangi bir HWND, karıştırılamaz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ile işleme [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] işleme veya [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]  /  [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] işleme. Bu, birkaç etkileri vardır. Öncelikle, tüm bu işleme modellerini karıştırmak için birlikte çalışabilirlik çözümünü oluşturun ve belirtilen kesimleri birlikte çalışabilirlik kullanmak için seçtiğiniz her bir işleme modeli için kullanmanız gerekir. Ayrıca, işleme davranışını ne birlikte çalışabilirlik çözümünüzü gerçekleştirmek için bir "Hava Sahası" kısıtlama oluşturur. "Hava Sahası" kavramı konusunda daha ayrıntılı açıklanmıştır [teknoloji bölgelerine genel bakış](technology-regions-overview.md).  
  
 Tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekranında öğeleri sonuçta bir HWND tarafından desteklenen. Oluştururken bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window>, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en üst düzey bir HWND oluşturur ve bir <xref:System.Windows.Interop.HwndSource> koymak <xref:System.Windows.Window> ve kendi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND içindeki içerik.  Geri kalanı, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama içeriği, tekil HWND paylaşır. Menüleri, birleşik giriş kutusu açılan listeler ve diğer pencereleri, bir özel durumdur. Bu öğeleri olmasının nedeni, kendi üst düzey pencere oluşturma bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] menü potansiyel olarak içerdiği HWND penceresinin kenar gidin. Kullanırken <xref:System.Windows.Interop.HwndHost> HWND içine yerleştirileceği [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bildirir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] nasıl yeni alt HWND göreli konum [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND.  
  
 Bir ilgili HWND için saydamlık içindeki ve arasındaki her HWND kavramıdır. Bu konuda ayrıca bahsedilen [teknoloji bölgelerine genel bakış](technology-regions-overview.md).  
  
<a name="hosting_a_wpf_page"></a>   
## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>WPF içeriği Microsoft Win32 penceresinde barındırma  
 Barındırma anahtarını bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] üzerinde bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi <xref:System.Windows.Interop.HwndSource> sınıfı. Bu sınıf sarmalar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi, böylece [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği dahil içine, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] bir alt pencere olarak. Aşağıdaki yaklaşımı birleştirir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tek bir uygulamada.  
  
1. Uygulama, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği (içerik kök öğesi) olarak yönetilen bir sınıf. Genellikle, sınıfı birden çok alt öğe içerebilir ve/veya bir kök öğe gibi kullanılan sınıflarının birinden devralan <xref:System.Windows.Controls.DockPanel> veya <xref:System.Windows.Controls.Page>. Sonraki adımlarda bu sınıf olarak adlandırılır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik sınıfı ve sınıf örnekleri verilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesneleri.  
  
2. Uygulama bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ile uygulama [!INCLUDE[TLA2#tla_cppcli](../../../../includes/tla2sharptla-cppcli-md.md)]. Varolan ile başlıyorsanız yönetilmeyen [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] uygulama, genellikle etkinleştirebilirsiniz yönetilen kod eklemek için proje ayarlarınızı değiştirerek çağıracak şekilde `/clr` derleyici bayrağı (ne desteklemekgerekliolabilir,tamkapsam`/clr`derleme bu konuda açıklanan değil).  
  
3. İş parçacığı modeli tek iş parçacıklı grup (STA için) ayarlayın. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bu iş parçacığı modeli kullanır.  
  
4. Pencere yordamını WM_CREATE bildiriminde işleyin.  
  
5. İşleyici (veya işleyici çağıran bir işlev içinde), aşağıdakileri yapın:  
  
    1. Yeni bir <xref:System.Windows.Interop.HwndSource> HWND üst pencere nesnesi olarak kendi `parent` parametresi.  
  
    2. Öğesinin bir örneğini oluşturur, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik sınıfı.  
  
    3. Bir başvuru atama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesnesine <xref:System.Windows.Interop.HwndSource> nesne <xref:System.Windows.Interop.HwndSource.RootVisual%2A> özelliği.  
  
    4. <xref:System.Windows.Interop.HwndSource> Nesne <xref:System.Windows.Interop.HwndSource.Handle%2A> özelliği, pencere işleyicisi (HWND) içerir. Uygulamanızın yönetilmeyen parçası kullanabileceğiniz bir HWND almak için cast `Handle.ToPointer()` HWND için.  
  
6. Bir başvuru tutan bir statik alan içeren bir yönetilen sınıf uygulamak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesne. Bu sınıf, bir başvuru almak sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesneden, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kod, ancak daha da önemlisi, engeller, <xref:System.Windows.Interop.HwndSource> engeller yanlışlıkla çöp olarak toplanacak.  
  
7. Bildirimleri almak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] biri veya daha fazlası için bir işleyici ekleyerek içerik nesne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesne olayları.  
  
8. İletişim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kümesi özellikleri, yöntemleri çağırabilir, vb. için statik alanında depolanan başvuru kullanarak içerik nesne.  
  
> [!NOTE]
>  Bazılarını veya tümünü yapabileceğiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik için adım bir sınıf tanımının [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ayrı bir derleme oluşturmak ve ardından ona başvuran içerik sınıfının varsayılan kısmi sınıf kullanarak. Genellikle içerse bir <xref:System.Windows.Application> derleme işleminin parçası olarak nesne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir derlemeye, söz konusu bitmeyen <xref:System.Windows.Application> birlikte çalışma işleminin bir parçası olarak, yalnızca bir veya daha fazla kök sınıflar için kullandığınız [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] başvurulan dosyaları için uygulama tarafından ve bunların kısmi sınıflar başvuru. Yordamın geri kalanını, yukarıda özetlenen temelde benzerdir.  
>   
>  Bu adımların her biri konusunda daha fazla kod aracılığıyla gösterilmiştir [izlenecek yol: Win32'de WPF barındırma](walkthrough-hosting-wpf-content-in-win32.md).  
  
<a name="hosting_an_hwnd"></a>   
## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>WPF Microsoft Win32 penceresinde barındırma  
 Barındırma anahtarını bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] diğer pencereye [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik <xref:System.Windows.Interop.HwndHost> sınıfı. Bu sınıf penceresinde sarmalar bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eklenebilir öğesi bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğe ağacı. <xref:System.Windows.Interop.HwndHost> Ayrıca destekler [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] iletilerini barındırılan pencere için işleme gibi görevleri yapmak izin. Temel yordam aynıdır:  
  
1. İçin bir öğe ağacı oluşturma bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama (olabilir başladığınız kodun veya). Öğe ağacındaki bir uygun ve izin verilen noktası bulmasını burada <xref:System.Windows.Interop.HwndHost> uygulaması bir alt öğesi eklenebilir. Kalanı Bu adımlar, bu öğe rezerve öğesi olarak adlandırılır.  
  
2. Öğesinden türetilen <xref:System.Windows.Interop.HwndHost> tutan bir nesne oluşturmak için [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] içeriği.  
  
3. Bu konak sınıfında geçersiz kılma <xref:System.Windows.Interop.HwndHost> yöntemi <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>. Barındırılan penceresinin HWND döndürür. Döndürülen penceresinin alt pencere olarak gerçek denetim kaydırma isteyebilirsiniz; bir ana penceresinde denetimleri sarmalama için basit bir yol sağlar, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerden bildirim almak içerik. Bu teknik düzeltmek için bazı yardımcı olur. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] denetimden sınırında ileti işleme ile ilgili sorunlar.  
  
4. Geçersiz kılma <xref:System.Windows.Interop.HwndHost> yöntemleri <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> ve <xref:System.Windows.Interop.HwndHost.WndProc%2A>. Özellikle yönetilmeyen nesnelere başvurular oluşturduysanız niyetini burada barındırılan içerik başvuruları kaldırın ve temizleme işlemi oluşturmaktır.  
  
5. Arka plan kod dosyasında, denetim sınıf barındırma örneği oluşturun ve bunu rezerve öğesinin bir alt öğesi yapın. Genellikle, bir olay işleyicisi aşağıdaki gibi kullanırsınız <xref:System.Windows.FrameworkElement.Loaded>, ya da kısmi sınıf oluşturucusunu kullanın. Ancak, bir çalışma zamanı davranışı ile birlikte çalışabilirlik içeriği de ekleyebilirsiniz.  
  
6. Denetim bildirimleri gibi işlem seçilen pencere iletileri. İki yaklaşım vardır. Seçtiğiniz kolaylık programlama büyük ölçüde olursa olsun, bu nedenle her iki için ileti akışına, aynı erişim sağlar.  
  
    - Uygulama ileti kılacağınızı içindeki tüm iletileri (yalnızca kapatma iletiler) için işleme <xref:System.Windows.Interop.HwndHost> yöntemi <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
    - Barındırma sahip [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesi işleyerek iletileri işleyecek <xref:System.Windows.Interop.HwndHost.MessageHook> olay. Bu olay, barındırılan pencere ana pencere yordamına gönderilen her ileti için tetiklenir.  
  
    - İşlem kullanımı dışında windows iletilerini işleme koyamıyoruz <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
7. Platform kullanarak barındırılan pencere ile iletişim kurmak yönetilmeyen çağırmak için Çağır `SendMessage` işlevi.  
  
 Aşağıdaki adımları fare girişi ile çalışan bir uygulama oluşturur. Uygulama tarafından barındırılan pencereniz sekme desteği ekleyebilirsiniz <xref:System.Windows.Interop.IKeyboardInputSink> arabirimi.  
  
 Bu adımların her biri konusunda daha fazla kod aracılığıyla gösterilmiştir [izlenecek yol: WPF içinde Win32 denetimini barındırma](walkthrough-hosting-a-win32-control-in-wpf.md).  
  
### <a name="hwnds-inside-wpf"></a>Cwnd'lerden içinde WPF  
 Düşünebilirsiniz <xref:System.Windows.Interop.HwndHost> bir özel denetim olarak. (Teknik olarak <xref:System.Windows.Interop.HwndHost> olduğu bir <xref:System.Windows.FrameworkElement> sınıfı türetilmemiş bir <xref:System.Windows.Controls.Control> türetilmiş sınıf, ancak bir denetim birlikte çalışabilirlik amaçları için kabul edilebilir.) <xref:System.Windows.Interop.HwndHost> soyutlar arka plandaki [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] barındırılan içeriğin doğasını şekilde geri kalanında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işlemek ve işlem girişi gereken başka bir denetim benzeri nesne olmasını barındırılan içeriğe göz önünde bulundurur. <xref:System.Windows.Interop.HwndHost> genellikle diğer gibi davranır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>, ancak çıkış (çizim ve grafikler) etrafında önemli bazı farklar vardır ve temel alınan Cwnd'lerden sınırlamalar göre giriş (fare ve klavye) destekleyebilir.  
  
#### <a name="notable-differences-in-output-behavior"></a>Çıkış davranış önemli farklılıkları  
  
- <xref:System.Windows.FrameworkElement>, olduğu <xref:System.Windows.Interop.HwndHost> temel sınıfı, kullanıcı Arabirimi değişiklikleri yaptığından oldukça az özelliği vardır. Bu gibi özellikleri içeren <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>, üst öğe olarak bu öğe içindeki öğe düzenini değiştirir. Ancak, bu özelliklerin çoğu, olabildiğince eşlenmedi [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] eşdeğerleri olsa da bu tür eşdeğerleri mevcut olmayabilir. Bu özelliklerin çok fazla ve anlamlarını pratik olmasını eşlemeleri için çok işleme teknoloji özgüdür. Bu nedenle, gibi özellikleri ayarlamak <xref:System.Windows.FrameworkElement.FlowDirection%2A> üzerinde <xref:System.Windows.Interop.HwndHost> hiçbir etkisi olmaz.  
  
- <xref:System.Windows.Interop.HwndHost> etkilenen bir dönüştürme işlemi tarafından döndürülen, ölçeklenen, dengesiz veya aksi olamaz.  
  
- <xref:System.Windows.Interop.HwndHost> desteklemediği <xref:System.Windows.UIElement.Opacity%2A> (alfa karıştırma) özelliği. İçindeki içerik varsa <xref:System.Windows.Interop.HwndHost> gerçekleştirir <xref:System.Drawing> kendisi bir ihlali değil, alfa bilgileri de yer operations ancak <xref:System.Windows.Interop.HwndHost> bütün yalnızca opaklık desteklediği 1.0 (% 100) =.  
  
- <xref:System.Windows.Interop.HwndHost> diğer en üstünde görünür [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aynı üst düzey pencere öğeleri. Ancak, bir <xref:System.Windows.Controls.ToolTip> veya <xref:System.Windows.Controls.ContextMenu> oluşturulan menü ayrı bir üst düzey penceresi ve bu nedenle doğru ile davranış göstereceği <xref:System.Windows.Interop.HwndHost>.  
  
- <xref:System.Windows.Interop.HwndHost> kırpma bölgesini üst uymaz <xref:System.Windows.UIElement>. Put denerseniz, bu büyük olasılıkla bir sorundur bir <xref:System.Windows.Interop.HwndHost> sınıf kayan bir bölge içinde veya <xref:System.Windows.Controls.Canvas>.  
  
#### <a name="notable-differences-in-input-behavior"></a>Giriş davranış önemli farklılıkları  
  
- İçinde giriş cihazları kapsamlı sırada genel <xref:System.Windows.Interop.HwndHost> barındırılan [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bölge giriş olayları Git doğrudan [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
- Üzerine Fare üzerindeyken <xref:System.Windows.Interop.HwndHost>, uygulamanızın ROM'u [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fare olayları ve değerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliği <xref:System.Windows.UIElement.IsMouseOver%2A> olacaktır `false`.  
  
- Sırada <xref:System.Windows.Interop.HwndHost> klavye girintisine sahip uygulamanızı değil alırsınız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klavye olayları ve değerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliği <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> olacaktır `false`.  
  
- Zaman içinde olduğunu <xref:System.Windows.Interop.HwndHost> ve içindeki başka bir denetim değişiklikleri <xref:System.Windows.Interop.HwndHost>, uygulamanızın değil alırsınız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olayları <xref:System.Windows.UIElement.GotFocus> veya <xref:System.Windows.UIElement.LostFocus>.  
  
- Ekran kalemi özellikleri ve olayları benzer ve kalemi üzerinden üzerindeyken bilgi bildirmeyen ilgili <xref:System.Windows.Interop.HwndHost>.  
  
<a name="tabbing_mnemonics_accelerators"></a>   
## <a name="tabbing-mnemonics-and-accelerators"></a>Sekme, anımsatıcıları ve Hızlandırıcıları  
 <xref:System.Windows.Interop.IKeyboardInputSink> Ve <xref:System.Windows.Interop.IKeyboardInputSite> arabirimleri karma sorunsuz klavye deneyimi oluşturmak izin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamalar:  
  
- Arasında sekmeyle gitmeyi [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşenleri  
  
- Anımsatıcıları ve odak WPF bileşeni içinde olduğunda ve bir Win32 bileşeni içinde olduğunda, hem de çalışan Hızlandırıcılar.  
  
 <xref:System.Windows.Interop.HwndHost> Ve <xref:System.Windows.Interop.HwndSource> sınıflarının her ikisi de uygulamaları sağlamak <xref:System.Windows.Interop.IKeyboardInputSink>, ancak bunlar, daha Gelişmiş senaryolar için istediğiniz tüm giriş iletileri işleyen değil. Kullanmak istediğiniz klavye davranışı elde etmek için uygun yöntemleri geçersiz kılın.  
  
 Yalnızca arabirimleri arasında geçiş hakkında neler için destek sağlamak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bölgeleri. İçinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bölge davranışı sekmeyle gitmeyi tamamen tarafından denetlenir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] iletmelisiniz mantığı varsa uygulanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.HwndHost>
- <xref:System.Windows.Interop.HwndSource>
- <xref:System.Windows.Interop>
- [İzlenecek yol: WPF içinde Win32 denetimini barındırma](walkthrough-hosting-a-win32-control-in-wpf.md)
- [İzlenecek yol: Win32'de WPF barındırma](walkthrough-hosting-wpf-content-in-win32.md)
