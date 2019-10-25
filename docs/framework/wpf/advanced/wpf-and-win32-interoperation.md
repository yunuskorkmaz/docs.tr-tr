---
title: WPF ve Win32 Birlikte Çalışması
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
ms.openlocfilehash: 7248b0e5abcf2c6357dc7ce7c708eaa85358061a
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846802"
---
# <a name="wpf-and-win32-interoperation"></a>WPF ve Win32 Birlikte Çalışması

Bu konu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodunun nasıl kullanılacağına ilişkin bir genel bakış sağlar. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], uygulamalar oluşturmak için zengin bir ortam sağlar. Ancak, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kodda önemli bir yatırımınız varsa, bu kodların bazılarını yeniden kullanmak daha etkili olabilir.

<a name="basics"></a>

## <a name="wpf-and-win32-interoperation-basics"></a>WPF ve Win32 birlikte çalışabilirlik temelleri

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu arasında birlikte çalışabilirlik için iki temel teknik vardır.

- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bir pencerede barındırın. Bu teknikle, standart bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pencere ve uygulamanın çerçevesi içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gelişmiş grafik yeteneklerini kullanabilirsiniz.

- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerikte bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi barındırın. Bu teknikle, diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik bağlamında mevcut bir özel [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] denetimini kullanabilir ve verileri sınırlar arasında geçirebilirsiniz.

Bu tekniklerin her biri kavramsal olarak bu konuda sunulmuştur. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)][!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] barındırmanın daha fazla kod odaklı bir gösterimi için bkz. [Izlenecek yol: Win32 'de WPF Içeriğini barındırma](walkthrough-hosting-wpf-content-in-win32.md). [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] barındırma için daha fazla kod odaklı bir çizim için bkz. [Izlenecek yol: WPF 'Te Win32 denetimi barındırma](walkthrough-hosting-a-win32-control-in-wpf.md).

<a name="projects"></a>

## <a name="wpf-interoperation-projects"></a>WPF birlikte çalışma projeleri

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API 'Ler yönetilen koddur, ancak mevcut [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programlarının çoğu yönetilmeyen C++olarak yazılmıştır.  Doğru yönetilmeyen bir programdan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API 'Leri çağrılamaz. Ancak, Microsoft Visual C++ derleyicisi ile `/clr` seçeneğini kullanarak, yönetilen ve yönetilmeyen API çağrılarını sorunsuzca karıştırabileceğiniz, karma yönetilen, yönetilmeyen bir program oluşturabilirsiniz.

Proje düzeyinde bir karmaşıkma, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyaları bir C++ projeye derleyemezsiniz.  Bunun için telafi eden çeşitli proje bölmesi teknikleri vardır.

- Derlenmiş derleme C# olarak tüm [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]sayfalarınızı içeren bir DLL oluşturun ve sonra yürütülebilir dosyanızı C++ BIR başvuru olarak bu DLL 'yi içermesini sağlayabilirsiniz.

- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]içerik C# için bir yürütülebilir dosya oluşturun ve[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]içeriğini içeren bir C++ dll 'ye başvurın.

- [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]derlemek yerine, çalışma zamanında [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yüklemek için <xref:System.Windows.Markup.XamlReader.Load%2A> kullanın.

- [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir bütün olarak kullanmayın ve <xref:System.Windows.Application>öğe ağacını oluşturarak tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] koda yazın.

Sizin için en uygun yaklaşımı kullanın.

> [!NOTE]
> Daha önce/CLI kullandıysanız C++, birlikte çalışabilirlik kod örneklerinde`gcnew`ve`nullptr`gibi bazı "yeni" anahtar kelimeleriyle karşılaşabilirsiniz. Bu anahtar sözcükler, eski çift alt çizgi sözdiziminin yerini alır (`__gc`) ve içinde C++yönetilen kod için daha doğal bir sözdizimi sağlar.  C++/CLI yönetilen özellikleri hakkında daha fazla bilgi edinmek için bkz. [çalışma zamanı platformları için bileşen uzantıları](/cpp/windows/component-extensions-for-runtime-platforms).

<a name="hwnds"></a>

## <a name="how-wpf-uses-hwnds"></a>WPF, HWNDs 'yi nasıl kullanır?

"HWND birlikte çalışma" [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en iyi şekilde sağlamak için, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWNDs 'yi nasıl kullandığını anlamanız gerekir. Herhangi bir HWND için, DirectX işleme veya GDI/GDI+ işlemesi ile [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işleme karıştırılamaz. Bu bir dizi etkilere sahiptir. Öncelikle, bu işleme modellerini hiç karıştırmak için, birlikte çalışabilirlik çözümü oluşturmanız ve kullanmayı seçtiğiniz her bir işleme modeli için birlikte çalışabilirlik 'nin belirlenen segmentlerini kullanmanız gerekir. Ayrıca, işleme davranışı, birlikte çalışma çözümünüzün gerçekleştirebilecekleri bir "hava sahası" kısıtlaması oluşturur. "Hava sahası" kavramı, [teknoloji bölgelerine genel bakış](technology-regions-overview.md)konusunda daha ayrıntılı olarak açıklanmıştır.

Ekrandaki tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeleri, sonunda bir HWND tarafından desteklenir. Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window>oluşturduğunuzda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en üst düzey HWND oluşturur ve <xref:System.Windows.Window> ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğini HWND içine yerleştirmek için bir <xref:System.Windows.Interop.HwndSource> kullanır.  Uygulamanın geri kalanı, bu tekil HWND paylaşımlarında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Menüler, Birleşik giriş kutusu açılan listeleri ve diğer açılır pencereler özel bir durumdur. Bu öğeler kendi üst düzey penceresini oluşturur, bu nedenle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir menü, kendisini içeren pencere HWND 'nin kenarını büyük olasılıkla geçebilirler. Bir HWND 'yi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]içine yerleştirmek için <xref:System.Windows.Interop.HwndHost> kullandığınızda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yeni alt HWND [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND 'ye göre nasıl konumlandırdığını [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bilgilendirir.

HWND ile ilgili bir kavram, her HWND içinde ve arasında saydamdır. Bu, [teknoloji bölgelerine genel bakış](technology-regions-overview.md)konusunda da ele alınmıştır.

<a name="hosting_a_wpf_page"></a>

## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>Microsoft Win32 penceresinde WPF Içeriğini barındırma

[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bir pencere üzerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] barındırmak için anahtar <xref:System.Windows.Interop.HwndSource> sınıftır. Bu sınıf, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğinin bir alt pencere olarak [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dahil edebilmesi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğini bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresinde sarmalanmış hale getirebilirsiniz. Aşağıdaki yaklaşım [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tek bir uygulamada birleştirir.

1. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğinizi (içerik kök öğesi) yönetilen bir sınıf olarak uygulayın. Genellikle, sınıfı birden çok alt öğe içerebilen sınıflardan birinden devralır ve/veya <xref:System.Windows.Controls.DockPanel> ya da <xref:System.Windows.Controls.Page>gibi bir kök öğe olarak kullanılır. Sonraki adımlarda, bu sınıf [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik sınıfı olarak adlandırılır ve sınıfın örnekleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesneleri olarak adlandırılır.

2. /Cliile C++bir Windows uygulaması uygulayın. Var olan bir yönetilmeyen C++ uygulamayla başlıyorsanız, genellikle proje ayarlarınızı`/clr`derleyici bayrağını içerecek şekilde değiştirerek yönetilen kodu çağırmak için etkinleştirebilirsiniz (`/clr`derlemeyi desteklemek için gerekli olabilecek tam kapsam Bu konuda açıklanmamaktadır).

3. İş parçacığı modelini tek Iş parçacıklı Apartment (STA) olarak ayarlayın. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bu iş parçacığı modelini kullanır.

4. WM_CREATE bildirimini pencere yordamınıza işleyin.

5. İşleyici içinde (veya işleyicinin çağırdığı bir işlev), aşağıdakileri yapın:

    1. `parent` parametresi olarak üst pencere HWND 'si ile yeni bir <xref:System.Windows.Interop.HwndSource> nesnesi oluşturun.

    2. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik sınıfınızın bir örneğini oluşturun.

    3. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Content nesnesine bir başvuruyu <xref:System.Windows.Interop.HwndSource> nesne <xref:System.Windows.Interop.HwndSource.RootVisual%2A> özelliğine atayın.

    4. <xref:System.Windows.Interop.HwndSource> nesnesi <xref:System.Windows.Interop.HwndSource.Handle%2A> özelliği pencere tanıtıcısını (HWND) içerir. Uygulamanızın yönetilmeyen bölümünde kullanabileceğiniz bir HWND almak için `Handle.ToPointer()` HWND 'ye atayın.

6. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesneniz için bir başvuru tutan bir statik alan içeren yönetilen bir sınıf uygulayın. Bu sınıf, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodunuzda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesnesine bir başvuru almanızı sağlar, ancak daha da önemlisi <xref:System.Windows.Interop.HwndSource> istenmeden atık toplanmasını önler.

7. Bir veya daha fazla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesnesi olayına işleyici ekleyerek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesnesinden bildirim alın.

8. Özellikleri ayarlamak için statik alanda depoladığınız başvuruyu kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesnesiyle iletişim kurun, yöntemleri çağırın, vb.

> [!NOTE]
> Farklı bir derleme üretemiyor ve sonra başvurdıysanız, içerik sınıfının varsayılan kısmi sınıfını kullanarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] adım adım için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik sınıfı tanımının bir kısmını veya tümünü yapabilirsiniz. Bir <xref:System.Windows.Application> nesnesini, bir derlemeye [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] derlemenin bir parçası olarak dahil etse de, bu <xref:System.Windows.Application> bir veya daha fazla uygulama tarafından başvurulan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları için yalnızca bir veya daha fazla kullanın. ve kısmi sınıflarına başvurur. Yordamın geri kalanı temelde yukarıda ana hatlarıyla benzerdir.
>
> Bu adımların her biri, [Izlenecek yol: Win32 'de WPF Içeriğini barındırma](walkthrough-hosting-wpf-content-in-win32.md)konusundaki kod aracılığıyla gösterilmiştir.

<a name="hosting_an_hwnd"></a>

## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>WPF 'de Microsoft Win32 penceresi barındırma

Diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriklerde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bir pencere barındırmak için anahtar <xref:System.Windows.Interop.HwndHost> sınıftır. Bu sınıf, bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğe ağacına eklenebilen bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesinde pencereyi sarmalanmış. <xref:System.Windows.Interop.HwndHost> Ayrıca, bu gibi görevleri barındırılan pencere için işlem iletileri olarak yapmanıza imkan tanıyan API 'Leri destekler. Temel yordam:

1. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulaması için bir öğe ağacı oluşturun (kod veya biçimlendirme aracılığıyla olabilir). <xref:System.Windows.Interop.HwndHost> uygulamasının alt öğe olarak eklenebildiği öğe ağacında uygun ve izin verilebilir bir nokta bulun. Bu adımların geri kalanında, bu öğe, ayırma öğesi olarak adlandırılır.

2. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] içeriğinizi tutan bir nesne oluşturmak için <xref:System.Windows.Interop.HwndHost> türetilir.

3. Bu ana bilgisayar sınıfında <xref:System.Windows.Interop.HwndHost> yöntemi <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>geçersiz kılın. Barındırılan pencerenin HWND 'sini döndürün. Gerçek denetimleri döndürülen pencerenin alt penceresi olarak kaydırmak isteyebilirsiniz; denetimleri bir ana bilgisayar penceresinde sarmalama, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğiniz için denetimlerden bildirimleri almak için basit bir yol sağlar. Bu teknik, barındırılan denetim sınırında ileti işleme ile ilgili bazı [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] sorunlara yönelik düzeltme sağlanmasına yardımcı olur.

4. <xref:System.Windows.Interop.HwndHost> yöntemleri <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> ve <xref:System.Windows.Interop.HwndHost.WndProc%2A>geçersiz kılın. Buradaki amaç, özellikle yönetilmeyen nesnelere başvurular oluşturduysanız, temizleme işlemini ve barındırılan içeriğe başvuruları kaldırmayı sağlar.

5. Arka plan kod dosyanızda, denetim barındırma sınıfının bir örneğini oluşturun ve bunu ayırma öğesinin bir alt öğesi yapın. Genellikle <xref:System.Windows.FrameworkElement.Loaded>gibi bir olay işleyicisi kullanır veya kısmi sınıf oluşturucusunu kullanabilirsiniz. Ancak, birlikte çalışabilirlik içeriğini çalışma zamanı davranışı ile de ekleyebilirsiniz.

6. Denetim bildirimleri gibi seçili pencere iletilerini işleyin. İki yaklaşım vardır. Her ikisi de ileti akışına özdeş erişim sağlar, böylece seçiminiz programlama kolaylığına göre büyük ölçüde önemlidir.

    - <xref:System.Windows.Interop.HwndHost> yöntemi <xref:System.Windows.Interop.HwndHost.WndProc%2A>geçersiz kılmada tüm iletiler için ileti işlemeyi (yalnızca kapalı iletiler değil) uygulayın.

    - Barındırma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesinin, <xref:System.Windows.Interop.HwndHost.MessageHook> olayını işleyerek iletileri işlemesini sağlayabilirsiniz. Bu olay barındırılan pencerenin ana pencere yordamına gönderilen her ileti için oluşturulur.

    - <xref:System.Windows.Interop.HwndHost.WndProc%2A>kullanarak işlem dışı olan Windows iletilerini işleyemez.

7. Yönetilmeyen `SendMessage` işlevini çağırmak için platform Invoke kullanarak barındırılan pencereyle iletişim kurun.

Bu adımları takip etmek, fare girişi ile birlikte çalışarak bir uygulama oluşturur. <xref:System.Windows.Interop.IKeyboardInputSink> arabirimini uygulayarak, barındırılan pencereniz için sekme desteği ekleyebilirsiniz.

Bu adımların her biri, konu başlığı altında kod aracılığıyla gösterilmiştir [: WPF 'Te Win32 denetimi barındırma](walkthrough-hosting-a-win32-control-in-wpf.md).

### <a name="hwnds-inside-wpf"></a>WPF Içinde HWNDs

<xref:System.Windows.Interop.HwndHost> özel bir denetim olarak düşünebilirsiniz. (Teknik olarak, <xref:System.Windows.Interop.HwndHost> türetilmiş bir sınıf <xref:System.Windows.Controls.Control> değil <xref:System.Windows.FrameworkElement> türetilmiş bir sınıftır, ancak birlikte çalışma amacıyla bir denetim olarak kabul edilebilir.) <xref:System.Windows.Interop.HwndHost> barındırılan içeriğin temel [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] yapısını soyutlayan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] geri kalanı barındırılan içeriği, girişin oluşturulması ve işlemesi gereken başka bir denetim benzeri nesne olacak şekilde değerlendirir. <xref:System.Windows.Interop.HwndHost> genellikle diğer tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>gibi davranır, ancak çıktı (çizim ve grafik) ve giriş (fare ve klavye) etrafında, temel alınan HWND NDS 'nin destekleyebilecekleri sınırlamalara göre bazı önemli farklılıklar vardır.

#### <a name="notable-differences-in-output-behavior"></a>Çıkış davranışındaki önemli farklılıklar

- <xref:System.Windows.Interop.HwndHost> temel sınıfı olan <xref:System.Windows.FrameworkElement>, Kullanıcı arabiriminde yapılan değişiklikleri gösteren çok sayıda özelliğe sahiptir. Bunlar, bu öğe içindeki öğelerin yerleşimini üst öğe olarak değiştiren <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>gibi özellikleri içerir. Ancak, bu özelliklerin çoğu, bu tür eşdeğerleri mevcut olabilseler bile olası [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] eşdeğerlerine eşlenmez. Bu özelliklerden çok fazla ve anlamları, eşlemelerin pratik olması için çok fazla işleme teknolojisine özgüdür. Bu nedenle, <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.FrameworkElement.FlowDirection%2A> gibi özelliklerin ayarlanması hiçbir etkiye sahip değildir.

- <xref:System.Windows.Interop.HwndHost>, dönüşümden döndürülemez, ölçeklendirilemez, çarpıtılmış veya başka bir şekilde etkilenmemelidir.

- <xref:System.Windows.Interop.HwndHost>, <xref:System.Windows.UIElement.Opacity%2A> özelliğini (Alpha karıştırma) desteklemiyor. <xref:System.Windows.Interop.HwndHost> içindeki içerik alfa bilgilerini içeren <xref:System.Drawing> işlemleri gerçekleştirirse, bu kendisi bir ihlal değildir, ancak bir bütün olarak <xref:System.Windows.Interop.HwndHost> yalnızca opaklığı destekler = 1,0 (100%).

- <xref:System.Windows.Interop.HwndHost>, aynı üst düzey penceredeki diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğelerinin üstünde görünür. Ancak, <xref:System.Windows.Controls.ToolTip> veya <xref:System.Windows.Controls.ContextMenu> oluşturulan bir menü ayrı bir üst düzey penceredir ve bu nedenle <xref:System.Windows.Interop.HwndHost>ile doğru şekilde davranır.

- <xref:System.Windows.Interop.HwndHost>, üst <xref:System.Windows.UIElement>kırpma bölgesine uymaz. Bu, bir <xref:System.Windows.Interop.HwndHost> sınıfını bir kayan bölge veya <xref:System.Windows.Controls.Canvas>içine koymaya çalışırsanız sorun olabilir.

#### <a name="notable-differences-in-input-behavior"></a>Giriş davranışında önemli farklılıklar

- Genel olarak, giriş cihazları <xref:System.Windows.Interop.HwndHost> barındırılan [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bölgesi kapsamında yer alıyorsa, giriş olayları doğrudan [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]' e gider.

- Fare <xref:System.Windows.Interop.HwndHost>üzerindeyken, uygulamanız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fare olaylarını almaz ve <xref:System.Windows.UIElement.IsMouseOver%2A> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliğinin değeri `false`olur.

- <xref:System.Windows.Interop.HwndHost> klavye odağına sahip olsa da, uygulamanız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klavye olaylarını almaz ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> özelliğinin değeri `false`olur.

- Odak <xref:System.Windows.Interop.HwndHost> içindeyken ve <xref:System.Windows.Interop.HwndHost>içindeki başka bir denetimde yapılan değişiklikler olduğunda, uygulamanız <xref:System.Windows.UIElement.GotFocus> veya <xref:System.Windows.UIElement.LostFocus>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olaylarını almaz.

- İlgili ekran kalemi özellikleri ve olayları benzerdir ve Stilus <xref:System.Windows.Interop.HwndHost>üzerindeyken bilgi bildirmez.

<a name="tabbing_mnemonics_accelerators"></a>

## <a name="tabbing-mnemonics-and-accelerators"></a>Sekme, anımsatıcı ve Hızlandırıcılar

<xref:System.Windows.Interop.IKeyboardInputSink> ve <xref:System.Windows.Interop.IKeyboardInputSite> arabirimleri, karışık [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamalar için sorunsuz bir klavye deneyimi oluşturmanıza olanak tanır:

- [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşenleri arasında sekme

- Odak bir Win32 bileşeni içindeyse ve bir WPF bileşeni içindeyse her ikisi de çalışan anımsatıcıları ve Hızlandırıcılar.

<xref:System.Windows.Interop.HwndHost> ve <xref:System.Windows.Interop.HwndSource> sınıflarının her ikisi de <xref:System.Windows.Interop.IKeyboardInputSink>uygulamalarını sağlar, ancak daha gelişmiş senaryolar için istediğiniz tüm giriş iletilerini işleyemeyebilir. İstediğiniz klavye davranışını almak için uygun yöntemleri geçersiz kılın.

Arabirimler yalnızca [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bölgeleri arasındaki geçişte ne olacağı için destek sağlar. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bölgesinde sekme davranışı, varsa sekme için uygulanan [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] mantığı tarafından tamamen denetlenir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.HwndHost>
- <xref:System.Windows.Interop.HwndSource>
- <xref:System.Windows.Interop>
- [İzlenecek yol: WPF'te Win32 Denetimi Barındırma](walkthrough-hosting-a-win32-control-in-wpf.md)
- [İzlenecek yol: Win32'de WPF Barındırma](walkthrough-hosting-wpf-content-in-win32.md)
