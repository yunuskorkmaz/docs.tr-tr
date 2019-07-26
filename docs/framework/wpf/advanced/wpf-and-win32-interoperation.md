---
title: WPF ve Win32 Birlikte Çalışması
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
ms.openlocfilehash: a942d72f27d394d31a52fd02ecaa158add4d2e0f
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484627"
---
# <a name="wpf-and-win32-interoperation"></a>WPF ve Win32 Birlikte Çalışması
Bu konu, birlikte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çalışma ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodun nasıl kullanılacağına ilişkin bir genel bakış sağlar. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]uygulamalar oluşturmak için zengin bir ortam sağlar. Ancak, kod içinde [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] önemli bir yatırımınız olduğunda, bu kodların bazılarını yeniden kullanmak daha etkili olabilir.  

<a name="basics"></a>   
## <a name="wpf-and-win32-interoperation-basics"></a>WPF ve Win32 birlikte çalışabilirlik temelleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ve[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu arasında birlikte çalışabilirlik için iki temel teknik vardır.  
  
- İçeriği [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pencerede barındırın. Bu teknikle, standart [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bir pencere ve uygulamanın çerçevesi içinde gelişmiş grafik yeteneklerini kullanabilirsiniz.  
  
- İçerikte bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pencere barındırın [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Bu teknikle, diğer [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik bağlamında mevcut bir özel denetimi kullanabilir ve verileri sınırlar arasında geçirebilirsiniz.  
  
 Bu tekniklerin her biri kavramsal olarak bu konuda sunulmuştur. [İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] barındırmanındahafazlakododaklıbirgösterimiiçinbkz.İzlenecekyol:[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Win32](walkthrough-hosting-wpf-content-in-win32.md)'de WPF içeriğini barındırma. [İçinde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] barındırmanındahafazlakododaklıbirgösterimiiçinbkz.İzlenecekyol:[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] WPF](walkthrough-hosting-a-win32-control-in-wpf.md)'te Win32 denetimi barındırma.  
  
<a name="projects"></a>   
## <a name="wpf-interoperation-projects"></a>WPF birlikte çalışma projeleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]API 'ler yönetilen koddur, ancak var olan [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] çoğu program yönetilmeyen C++olarak yazılmıştır.  Doğru yönetilmeyen bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programdan API 'leri çağıramezsiniz. Bununla birlikte, `/clr` [!INCLUDE[TLA#tla_visualcpp](../../../../includes/tlasharptla-visualcpp-md.md)] derleyici seçeneğini kullanarak, yönetilen ve yönetilmeyen API çağrılarını sorunsuzca karıştırabileceğiniz, karma yönetilen, yönetilmeyen bir program oluşturabilirsiniz.  
  
 Proje düzeyinde bir karmaşıkma, dosyaları bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] C++ projede derleyemezsiniz.  Bunun için telafi eden çeşitli proje bölmesi teknikleri vardır.  
  
- Tüm [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] C# [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfalarınızı derlenmiş derleme olarak içeren bir DLL oluşturun ve ardından çalıştırılabilir dosyanızı C++ bir başvuru olarak ekleyin.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçerik için C# bir yürütülebilir dosya oluşturun ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] içeriği içeren bir C++ [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] öğesine başvurın.  
  
- [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Uygulamanızı <xref:System.Windows.Markup.XamlReader.Load%2A> derlemek[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]yerine çalışma zamanında yüklemek için kullanın.  
  
- Hiç kullanmayın [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve ' den <xref:System.Windows.Application>öğe ağacını oluşturarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tüm kodunuzu yazın.  
  
 Sizin için en uygun yaklaşımı kullanın.  
  
> [!NOTE]
>  Daha önce/CLI kullandıysanız C++, birlikte çalışabilirlik kod örneklerinde `gcnew` ve `nullptr` gibi bazı "yeni" anahtar kelimeleriyle karşılaşabilirsiniz. Bu anahtar sözcükler, eski çift alt çizgi söz dizimini`__gc`() yerine ekler ve içindeki C++yönetilen kod için daha doğal bir sözdizimi sağlar.  /CLI yönetilen özellikleri hakkında daha fazla bilgi edinmek için bkz. [çalışma zamanı platformları Için bileşen uzantıları](/cpp/windows/component-extensions-for-runtime-platforms) ve [Merhaba, C++/CLI.](https://go.microsoft.com/fwlink/?LinkId=98739) C++  
  
<a name="hwnds"></a>   
## <a name="how-wpf-uses-hwnds"></a>WPF, HWNDs 'yi nasıl kullanır?  
 "HWND birlikte çalışabilirliği" [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nin en iyi şekilde kullanılabilmesini sağlamak için, HWNDs [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 'i nasıl kullandığını anlamanız gerekir. Herhangi bir HWND için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işleme veya [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]  /  işleme ileişlemekarıştırılamaz.[!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] Bu bir dizi etkilere sahiptir. Öncelikle, bu işleme modellerini hiç karıştırmak için, birlikte çalışabilirlik çözümü oluşturmanız ve kullanmayı seçtiğiniz her bir işleme modeli için birlikte çalışabilirlik 'nin belirlenen segmentlerini kullanmanız gerekir. Ayrıca, işleme davranışı, birlikte çalışma çözümünüzün gerçekleştirebilecekleri bir "hava sahası" kısıtlaması oluşturur. "Hava sahası" kavramı, [teknoloji bölgelerine genel bakış](technology-regions-overview.md)konusunda daha ayrıntılı olarak açıklanmıştır.  
  
 Ekrandaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tüm öğeler sonunda bir HWND tarafından desteklenir. Oluşturduğunuzda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ,üst[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzey bir <xref:System.Windows.Interop.HwndSource> HWNDoluşturur[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve içeriğini HWND içine koymak içinbirkullanır.<xref:System.Windows.Window> <xref:System.Windows.Window>  Uygulamanın geri kalanı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , bu tekil HWND paylaşır. Menüler, Birleşik giriş kutusu açılan listeleri ve diğer açılır pencereler özel bir durumdur. Bu öğeler kendi üst düzey penceresini oluşturur, bu nedenle bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] menü, kendisini içeren pencere HWND 'nin kenarını büyük olasılıkla geçebilirler. İçine <xref:System.Windows.Interop.HwndHost> [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] <xref:System.Windows.Window> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir HWND koymak için kullandığınızda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yeni alt HWND 'yi HWND 'ye göre nasıl konumlandırmaya bildirilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
 HWND ile ilgili bir kavram, her HWND içinde ve arasında saydamdır. Bu, [teknoloji bölgelerine genel bakış](technology-regions-overview.md)konusunda da ele alınmıştır.  
  
<a name="hosting_a_wpf_page"></a>   
## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>Microsoft Win32 penceresinde WPF Içeriğini barındırma  
 Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pencere[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] üzerindebarındırılacakanahtar,sınıftır.<xref:System.Windows.Interop.HwndSource> Bu sınıf içeriği bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pencerede sarmaladığı için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğin bir alt pencere [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] olarak birleştirilebilir. Aşağıdaki yaklaşım, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesini tek bir uygulamada birleştirir.  
  
1. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçeriğinizi (içerik kök öğesi) yönetilen bir sınıf olarak uygulayın. Genellikle, sınıfı birden çok alt öğe içerebilen ve/veya gibi bir kök öğe <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Page>olarak kullanılan sınıflardan birinden devralır. Sonraki adımlarda, bu sınıfa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik sınıfı olarak başvurulur ve sınıfın örnekleri içerik nesneleri olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] adlandırılır.  
  
2. /Cliile C++bir Windows uygulaması uygulayın. Mevcut bir yönetilmeyen C++ uygulamayla başlıyorsanız, genellikle proje ayarlarınızı `/clr` derleyici bayrağını içerecek şekilde değiştirerek yönetilen kodu çağırmak için bu ayarı etkinleştirebilirsiniz (desteklemek `/clr` için gerekli olabilecek tam kapsam). derleme bu konuda açıklanmamaktadır.  
  
3. İş parçacığı modelini tek Iş parçacıklı Apartment (STA) olarak ayarlayın. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Bu iş parçacığı modelini kullanır.  
  
4. WM_CREATE bildirimini pencere yordamınıza işleyin.  
  
5. İşleyici içinde (veya işleyicinin çağırdığı bir işlev), aşağıdakileri yapın:  
  
    1. Parametresi olarak üst <xref:System.Windows.Interop.HwndSource> pencere HWND ile yeni bir nesne oluşturun. `parent`  
  
    2. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçerik sınıfınızın bir örneğini oluşturun.  
  
    3. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Nesne<xref:System.Windows.Interop.HwndSource.RootVisual%2A>özelliğine içerik nesnesine bir başvuru atayın. <xref:System.Windows.Interop.HwndSource>  
  
    4. <xref:System.Windows.Interop.HwndSource> Object<xref:System.Windows.Interop.HwndSource.Handle%2A> özelliği, pencere tanıtıcısını (hwnd) içerir. Uygulamanızın yönetilmeyen bölümünde kullanabileceğiniz bir hwnd almak için bir HWND 'ye atayın `Handle.ToPointer()` .  
  
6. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçerik nesneniz için bir başvuru tutan bir statik alan içeren yönetilen bir sınıf uygulayın. Bu sınıf, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodunuzdaki içerik nesnesine bir başvuru almanızı sağlar, ancak <xref:System.Windows.Interop.HwndSource> daha da önemlisi, istemeden atık olarak toplanmasını önler.  
  
7. İçerik nesnesi olaylarına bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veya daha fazla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işleyici ekleyerek içerik nesnesinden bildirim alın.  
  
8. Özellikleri ayarlamak için statik alanda depoladığınız başvuruyu kullanarak içeriknesnesiyleiletişimkurun,yöntemleriçağırın,vb.[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
> [!NOTE]
>  İçerik sınıfının bir kısmını veya tümünü [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , içerik sınıfının varsayılan kısmi sınıfını kullanarak, ayrı bir derleme üretemiyor ve sonra başvurdıysanız yapabilirsiniz. Bir <xref:System.Windows.Application> nesneyi bir derlemeye derlemenin bir parçası [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olarak genellikle dahil olsanız da, birlikte çalışma <xref:System.Windows.Application> 'nin bir parçası olarak, bir veya daha fazla başvurulan dosya için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir veya daha fazla kök sınıfı kullanmanız gerekir uygulamasına göre ve kısmi sınıflarına başvuru yapın. Yordamın geri kalanı temelde yukarıda ana hatlarıyla benzerdir.  
>   
>  Bu adımların her biri, konu başlığı [altında kod aracılığıyla gösterilmiştir: Win32](walkthrough-hosting-wpf-content-in-win32.md)'de WPF içeriğini barındırma.  
  
<a name="hosting_an_hwnd"></a>   
## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>WPF 'de Microsoft Win32 penceresi barındırma  
 Diğer [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] içerik[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içindebirpencereninbarındırılmasınayönelik<xref:System.Windows.Interop.HwndHost> anahtar, sınıftır. Bu sınıf, pencereyi bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğe ağacına eklenebilen bir öğe içinde kaydırır. <xref:System.Windows.Interop.HwndHost>Ayrıca, bu gibi görevleri barındırılan pencere için işlem iletileri olarak yapmanıza imkan tanıyan API 'Leri destekler. Temel yordam:  
  
1. Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama için bir öğe ağacı oluşturun (kod veya biçimlendirme aracılığıyla olabilir). Öğe ağacında <xref:System.Windows.Interop.HwndHost> , uygulamanın bir alt öğe olarak eklenebileceği uygun ve izin verilen bir nokta bulun. Bu adımların geri kalanında, bu öğe, ayırma öğesi olarak adlandırılır.  
  
2. İçeriğinizi tutan bir nesne oluşturmak için öğesinden <xref:System.Windows.Interop.HwndHost> türetirsiniz. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]  
  
3. Bu ana bilgisayar sınıfında, <xref:System.Windows.Interop.HwndHost> yöntemini <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>geçersiz kılın. Barındırılan pencerenin HWND 'sini döndürün. Gerçek denetimleri döndürülen pencerenin alt penceresi olarak kaydırmak isteyebilirsiniz; denetimleri bir ana bilgisayar penceresinde sarmalama, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğinizin denetimlerden bildirimleri alması için basit bir yol sağlar. Bu teknik, barındırılan denetim sınırında [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ileti işleme ile ilgili bazı sorunlar için düzeltmeye yardımcı olur.  
  
4. <xref:System.Windows.Interop.HwndHost> Ve <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> yöntemlerini geçersizkılın.<xref:System.Windows.Interop.HwndHost.WndProc%2A> Buradaki amaç, özellikle yönetilmeyen nesnelere başvurular oluşturduysanız, temizleme işlemini ve barındırılan içeriğe başvuruları kaldırmayı sağlar.  
  
5. Arka plan kod dosyanızda, denetim barındırma sınıfının bir örneğini oluşturun ve bunu ayırma öğesinin bir alt öğesi yapın. Genellikle gibi bir olay işleyicisi <xref:System.Windows.FrameworkElement.Loaded>kullanır veya kısmi sınıf oluşturucusunu kullanabilirsiniz. Ancak, birlikte çalışabilirlik içeriğini çalışma zamanı davranışı ile de ekleyebilirsiniz.  
  
6. Denetim bildirimleri gibi seçili pencere iletilerini işleyin. İki yaklaşım vardır. Her ikisi de ileti akışına özdeş erişim sağlar, böylece seçiminiz programlama kolaylığına göre büyük ölçüde önemlidir.  
  
    - <xref:System.Windows.Interop.HwndHost> Yöntemi<xref:System.Windows.Interop.HwndHost.WndProc%2A>geçersiz kılmanızda tüm iletiler için ileti işlemeyi uygulayın (yalnızca kapalı iletiler değil).  
  
    - Barındırma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesinin, <xref:System.Windows.Interop.HwndHost.MessageHook> olayı işleyerek iletileri işlemesini sağlayabilirsiniz. Bu olay barındırılan pencerenin ana pencere yordamına gönderilen her ileti için oluşturulur.  
  
    - Kullanarak <xref:System.Windows.Interop.HwndHost.WndProc%2A>işlem dışı olan Windows iletilerini işleyemez.  
  
7. Yönetilmeyen `SendMessage` işlevi çağırmak için platform Invoke kullanarak barındırılan pencereyle iletişim kurun.  
  
 Bu adımları takip etmek, fare girişi ile birlikte çalışarak bir uygulama oluşturur. <xref:System.Windows.Interop.IKeyboardInputSink> Arabirimini uygulayarak barındırılan pencereniz için sekme desteği ekleyebilirsiniz.  
  
 Bu adımların her biri, konu başlığı [altında kod aracılığıyla gösterilmiştir: WPF](walkthrough-hosting-a-win32-control-in-wpf.md)'te Win32 denetimi barındırma.  
  
### <a name="hwnds-inside-wpf"></a>WPF Içinde HWNDs  
 Özel bir denetim <xref:System.Windows.Interop.HwndHost> olarak düşünebilirsiniz. (Teknik olarak <xref:System.Windows.Interop.HwndHost> , <xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.Control> türetilmiş sınıf değil, türetilmiş bir sınıftır, ancak birlikte çalışma amacıyla bir denetim olarak kabul edilebilir.) barındırılan içeriğin temel [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] yapısını[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , barındırılan içeriği, girişi oluşturması ve işlemek gereken başka bir denetim benzeri nesne olacak şekilde soyutlar. <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost>genellikle herhangi bir diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>gibi davranır, ancak çıktı (çizim ve grafik) ve giriş (fare ve klavye) temelinde, temel alınan HWND NDS 'nin destekleyebilecekleri sınırlamalara göre bazı önemli farklılıklar vardır.  
  
#### <a name="notable-differences-in-output-behavior"></a>Çıkış davranışındaki önemli farklılıklar  
  
- <xref:System.Windows.FrameworkElement><xref:System.Windows.Interop.HwndHost> temel sınıf olan, Kullanıcı arabiriminde yapılan değişiklikleri belirten birkaç özelliği vardır. Bunlar gibi <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>, bu öğe içindeki öğelerin yerleşimini üst öğe olarak değiştiren özellikler içerir. Bununla birlikte, bu özelliklerin çoğu olası [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] eşdeğerlerine eşlenmez, bu da bu tür eşdeğerleri var olabilir. Bu özelliklerden çok fazla ve anlamları, eşlemelerin pratik olması için çok fazla işleme teknolojisine özgüdür. Bu nedenle, gibi özelliklerinin <xref:System.Windows.FrameworkElement.FlowDirection%2A> <xref:System.Windows.Interop.HwndHost> ayarlanması hiçbir etkiye sahip değildir.  
  
- <xref:System.Windows.Interop.HwndHost>bir dönüşümden döndürülemez, ölçeklendirilemez, çarpıtılmış veya başka bir şekilde etkilenmemelidir.  
  
- <xref:System.Windows.Interop.HwndHost><xref:System.Windows.UIElement.Opacity%2A> özelliği desteklemez (Alfa karıştırma). İçindeki içerik, <xref:System.Windows.Interop.HwndHost> birihlal<xref:System.Drawing> olmayan alfa bilgilerini içeren işlemler gerçekleştirirse, ancak tam olarakyalnızcaopaklığıdestekler=1,0(100%).<xref:System.Windows.Interop.HwndHost>  
  
- <xref:System.Windows.Interop.HwndHost>, aynı üst düzey penceredeki diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğelerin üst kısmında görünür. Ancak, veya <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ContextMenu> oluşturulmuş bir menü ayrı bir üst düzey penceredir ve bu nedenle ile <xref:System.Windows.Interop.HwndHost>doğru şekilde davranır.  
  
- <xref:System.Windows.Interop.HwndHost>üst <xref:System.Windows.UIElement>öğesinin kırpma bölgesine göre değil. Bu, bir <xref:System.Windows.Interop.HwndHost> sınıfı kaydırılan bir bölgenin içine veya <xref:System.Windows.Controls.Canvas>bir sınıf koymaya çalışırsanız sorun olabilir.  
  
#### <a name="notable-differences-in-input-behavior"></a>Giriş davranışında önemli farklılıklar  
  
- Genel olarak, giriş cihazları <xref:System.Windows.Interop.HwndHost> barındırılan [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bölge kapsamında olduğunda, giriş olayları doğrudan öğesine [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]gider.  
  
- Fare <xref:System.Windows.Interop.HwndHost>üzerindeyken, uygulamanız fare olaylarını almaz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve özelliğin <xref:System.Windows.UIElement.IsMouseOver%2A> `false`değeri olacaktır.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `false` <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> Klavye odağı olsa da, uygulamanız klavye olaylarını almaz ve özelliğin değeri olacaktır. <xref:System.Windows.Interop.HwndHost>  
  
- Odak <xref:System.Windows.Interop.HwndHost> içinde olduğunda ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Interop.HwndHost>içindeki başka bir denetimdeki değişiklikler olduğunda, uygulamanız olayları <xref:System.Windows.UIElement.GotFocus> almaz veya <xref:System.Windows.UIElement.LostFocus>olur.  
  
- İlgili ekran kalemi özellikleri ve olayları benzerdir ve ekran kalemi üzerindeyken <xref:System.Windows.Interop.HwndHost>bilgileri rapor etmez.  
  
<a name="tabbing_mnemonics_accelerators"></a>   
## <a name="tabbing-mnemonics-and-accelerators"></a>Sekme, anımsatıcı ve Hızlandırıcılar  
 Ve <xref:System.Windows.Interop.IKeyboardInputSink> arabirimleri<xref:System.Windows.Interop.IKeyboardInputSite> , karışık[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamalar için sorunsuz bir klavye deneyimi oluşturmanıza imkan tanır:  
  
- [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Ve[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşenleri arasında sekme  
  
- Odak bir Win32 bileşeni içindeyse ve bir WPF bileşeni içindeyse her ikisi de çalışan anımsatıcıları ve Hızlandırıcılar.  
  
 <xref:System.Windows.Interop.HwndHost> Ve<xref:System.Windows.Interop.HwndSource>sınıflarınınher ikisi de uygulamalarını sağlar ,ancakdahagelişmişsenaryolariçinistediğiniztümgirişiletileriniişleyemeyebilir.<xref:System.Windows.Interop.IKeyboardInputSink> İstediğiniz klavye davranışını almak için uygun yöntemleri geçersiz kılın.  
  
 Arabirimler yalnızca [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bölgeleri arasındaki geçişte ne olacağı için destek sağlar. Bölge içinde sekme davranışı, varsa sekme için [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulanan mantık tarafından tamamen denetlenir. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.HwndHost>
- <xref:System.Windows.Interop.HwndSource>
- <xref:System.Windows.Interop>
- [İzlenecek yol: WPF 'te Win32 denetimi barındırma](walkthrough-hosting-a-win32-control-in-wpf.md)
- [İzlenecek yol: Win32 'de WPF Içeriğini barındırma](walkthrough-hosting-wpf-content-in-win32.md)
