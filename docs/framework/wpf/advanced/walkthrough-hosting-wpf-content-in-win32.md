---
title: "İzlenecek yol: Win32'de WPF Barındırma"
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 5bc6e6d805d74bcf01044a16d94d6b3fc0ccf881
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846847"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>İzlenecek yol: Win32'de WPF Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], uygulamalar oluşturmak için zengin bir ortam sağlar. Ancak [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kodda önemli bir yatırımınız varsa, özgün kodunuzu yeniden yazmak yerine uygulamanıza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işlevselliği eklemek daha etkili olabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği barındırmak için kolay bir mekanizma sağlar.  
  
 Bu öğreticide, bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği barındıran [bir Win32 pencere ÖRNEĞINDE WPF Içeriği barındıran](https://go.microsoft.com/fwlink/?LinkID=160004)örnek bir uygulamanın nasıl yazılacağı açıklanmaktadır. Bu örneği, herhangi bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresini barındırmak için genişletebilirsiniz. Yönetilen ve yönetilmeyen kodu karıştırmayı içerdiğinden, uygulama/Clide C++yazılır.  

<a name="requirements"></a>   
## <a name="requirements"></a>Gereksinimler  
 Bu öğreticide [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programlamaya yönelik temel bir benzerlik vardır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programlamaya temel bir giriş için [bkz. Başlarken](../getting-started/index.md). [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programlamaya giriş için, özellikle Charles Petzold tarafından yapılan belirli bir *programlama* penceresinde, konudaki çok sayıda kitaplardan birine başvurmanız gerekir.  
  
 Bu öğreticiye eşlik eden örnek, C++/CLI ' da uygulandığından, bu öğreticide, Windows API 'sinin programlanması ve yönetilen kod programlamasını anlamak için kullanımı hakkında C++ bilgiler verilir. /CLI ile C++benzerlik yararlı ancak gerekli değildir.  
  
> [!NOTE]
> Bu öğretici, ilişkili örnekten bir dizi kod örneği içerir. Ancak okunabilirlik için, örnek kodu tamamen içermez. Tüm örnek kod için bkz. [bir Win32 pencere ÖRNEĞINDE WPF Içeriğini barındırma](https://go.microsoft.com/fwlink/?LinkID=160004).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Temel yordam  
 Bu bölümde, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğini [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bir pencerede barındırmak için kullandığınız temel yordam özetlenmektedir. Kalan bölümlerde her adımın ayrıntıları açıklanmaktadır.  
  
 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bir pencere üzerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik barındırmak için anahtar <xref:System.Windows.Interop.HwndSource> sınıftır. Bu sınıf, bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğini sarmalanmış ve bunun bir alt pencere olarak [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] eklenmesine izin verir. Aşağıdaki yaklaşım [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tek bir uygulamada birleştirir.  
  
1. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğinizi yönetilen bir sınıf olarak uygulayın.  
  
2. /Cliile C++bir Windows uygulaması uygulayın. Var olan bir uygulama ve yönetilmeyen C++ kod ile başlıyorsanız, genellikle proje ayarlarınızı`/clr`derleyici bayrağını içerecek şekilde değiştirerek yönetilen kodu çağırmak için bunu etkinleştirebilirsiniz.  
  
3. İş parçacığı modelini tek iş parçacıklı Apartment (STA) olarak ayarlayın.  
  
4. [WM_CREATE](/windows/desktop/winmsg/wm-create)bildirimini pencere yordamınıza işleyin ve şunları yapın:  
  
    1. Üst pencereyle `parent` parametresi olarak yeni bir <xref:System.Windows.Interop.HwndSource> nesnesi oluşturun.  
  
    2. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik sınıfınızın bir örneğini oluşturun.  
  
    3. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Content nesnesine bir başvuruyu <xref:System.Windows.Interop.HwndSource><xref:System.Windows.Interop.HwndSource.RootVisual%2A> özelliğine atayın.  
  
    4. İçerik için HWND 'yi alın. <xref:System.Windows.Interop.HwndSource> nesnesinin <xref:System.Windows.Interop.HwndSource.Handle%2A> özelliği pencere tanıtıcısını (HWND) içerir. Uygulamanızın yönetilmeyen bölümünde kullanabileceğiniz bir HWND almak için `Handle.ToPointer()` HWND 'ye atayın.  
  
5. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğiniz için bir başvuru tutmak üzere statik alan içeren bir yönetilen sınıf uygulayın. Bu sınıf, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodunuzda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğine yönelik bir başvuru almanızı sağlar.  
  
6. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğini statik alana atayın.  
  
7. Bir veya daha fazla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olayına işleyici ekleyerek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğinden bildirim alın.  
  
8. Özellikleri ayarlamak için statik alanda depoladığınız başvuruyu kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğiyle iletişim kurun ve bu şekilde devam edin.  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğinizi uygulamak için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] de kullanabilirsiniz. Ancak, bu dosyayı dinamik bağlantı kitaplığı (DLL) olarak ayrı olarak derleyip [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamanızdan DLL 'ye başvurmanız gerekecektir. Yordamın geri kalanı yukarıda ana hatlarıyla benzerdir.

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>Konak uygulamasını uygulama
 Bu bölümde, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğin temel bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamasında nasıl barındırılacağını açıklanmaktadır. İçerik, bir yönetilen sınıf olarak C++/CLI ' da uygulanır. Çoğu bölümde, programlama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] basittir. İçerik uygulamasının temel yönleri [WPF Içeriğini uygulama](#implementing_the_wpf_page)bölümünde ele alınmıştır.

- [Temel uygulama](#the_basic_application)

- [WPF Içeriğini barındırma](#hosting_the_wpf_page)

- [WPF Içeriğine başvuru tutma](#holding_a_reference)

- [WPF Içeriğiyle iletişim kurma](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>Temel uygulama
 Ana bilgisayar uygulaması için başlangıç noktası, bir Visual Studio 2005 şablonu oluşturmaktır.

1. Visual Studio 2005 ' i açın ve **Dosya** menüsünden **Yeni proje** ' yi seçin.

2. Görsel C++ proje türleri listesinden Win32 öğesini seçin. Varsayılan diliniz yoksa C++, bu proje türlerini **diğer diller**altında bulacaksınız.

3. Bir **Win32 Proje** şablonu seçin, projeye bir ad atayın ve **Win32 uygulama sihirbazını**başlatmak için **Tamam** ' a tıklayın.

4. Sihirbazın varsayılan ayarlarını kabul edin ve projeyi başlatmak için **son** ' a tıklayın.

 Şablon, aşağıdakiler dahil olmak üzere temel bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulaması oluşturur:

- Uygulama için bir giriş noktası.

- İlişkili bir pencere yordamıyla (WndProc) bir pencere.

- **Dosya** ve **Yardım** başlıkları içeren bir menü. **Dosya** menüsünde, uygulamayı kapatan bir **Çıkış** öğesi vardır. **Yardım** menüsünde basit bir iletişim kutusu başlatan **hakkında** bir öğe bulunur.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğini barındırmak için kod yazmaya başlamadan önce, temel şablonda iki değişiklik yapmanız gerekir.

 Birincisi, projeyi yönetilen kod olarak derlemek olur. Varsayılan olarak, proje yönetilmeyen kod olarak derlenir. Ancak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönetilen kodda uygulandığından, projenin buna göre derlenmesi gerekir.

1. **Çözüm Gezgini** ' de proje adına sağ tıklayın ve bağlam menüsünden **Özellikler** ' i seçerek **Özellik sayfaları** iletişim kutusunu başlatın.

2. Sol bölmedeki ağaç görünümünden **yapılandırma özellikleri** ' ni seçin.

3. Sağ bölmedeki **Proje Varsayılanları** listesinden **ortak dil çalışma zamanı** desteği ' ni seçin.

4. Açılan liste kutusundan **ortak dil çalışma zamanı desteği (/CLR)** öğesini seçin.

> [!NOTE]
> Bu derleyici bayrağı uygulamanızda yönetilen kod kullanmanıza izin verir, ancak yönetilmeyen kodunuz daha önce olduğu gibi derlenmeye devam eder.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tek iş parçacıklı Apartment (STA) iş parçacığı modelini kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik kodu ile düzgün şekilde çalışabilmek için, giriş noktasına bir öznitelik uygulayarak uygulamanın iş parçacığı modelini STA olarak ayarlamanız gerekir.

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>WPF Içeriğini barındırma
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik basit bir adres girişi uygulamasıdır. Kullanıcı adı, adres vb. almak için birkaç <xref:System.Windows.Controls.TextBox> denetimden oluşur. Ayrıca iki <xref:System.Windows.Controls.Button> denetimi vardır, **Tamam** ve **iptal et**. Kullanıcı **Tamam**' ı tıklattığında, düğmenin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisi verileri <xref:System.Windows.Controls.TextBox> denetimlerinden toplar, bunu ilgili özelliklere atar ve bir özel olay `OnButtonClicked`oluşturur. Kullanıcı **iptal**' i tıklattığında, işleyici `OnButtonClicked`yükseltilir. `OnButtonClicked` için olay bağımsız değişkeni nesnesi, hangi düğmenin tıklandığını gösteren bir Boole alanı içerir.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğini barındıracak kod, ana bilgisayar penceresinde [WM_CREATE](/windows/desktop/winmsg/wm-create) bildirimi için bir işleyicide uygulanır.

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 `GetHwnd` yöntemi, boyut ve konum bilgilerini ve üst pencere tanıtıcısını alır ve barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğinin pencere tanıtıcısını döndürür.

> [!NOTE]
> `System::Windows::Interop` ad alanı için `#using` yönergesi kullanamazsınız. Bunun yapılması, bu ad alanındaki <xref:System.Windows.Interop.MSG> yapısı ve Winuser. h içinde belirtilen MSG yapısı arasında bir ad çakışması oluşturur. Bunun yerine, bu ad alanının içeriğine erişmek için tam nitelikli adlar kullanmanız gerekir.

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğini doğrudan uygulama pencerenizde barındıryükleyemezsiniz. Bunun yerine, önce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğini kaydırmak için bir <xref:System.Windows.Interop.HwndSource> nesnesi oluşturursunuz. Bu nesne, temel olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir içerik barındırmak için tasarlanan bir penceredir. <xref:System.Windows.Interop.HwndSource> nesnesini, uygulamanızın bir parçası olan bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresinin alt öğesi olarak oluşturarak ana pencerede barındırabilirsiniz. <xref:System.Windows.Interop.HwndSource> Oluşturucu parametreleri, bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] alt pencere oluştururken CreateWindow 'a geçirdiğiniz bilgilerin çoğunu içerir.

 Daha sonra [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesnesinin bir örneğini oluşturun. Bu durumda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği, `WPFPage`/Clikullanarak C++ayrı bir sınıf olarak uygulanır. Ayrıca, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)][!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğini de uygulayabilirsiniz. Ancak bunu yapmak için, ayrı bir proje ayarlamanız ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğini DLL olarak oluşturmanız gerekir. Projenize bu DLL 'ye bir başvuru ekleyebilir ve bu başvuruyu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğin bir örneğini oluşturmak için kullanabilirsiniz.

 <xref:System.Windows.Interop.HwndSource><xref:System.Windows.Interop.HwndSource.RootVisual%2A> özelliğine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğine bir başvuru atayarak alt pencerenizde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği görüntülenir.

 Sonraki kod satırı, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik `OnButtonClicked` olayına bir olay işleyicisi `WPFButtonClicked`ekler. Bu işleyici Kullanıcı **Tamam** veya **iptal** düğmesine tıkladığında çağrılır. Bu olay işleyicisi hakkında daha fazla bilgi için bkz. [communicating_with_the_WPF Content](#communicating_with_the_page) .

 Gösterilen kodun son satırı, <xref:System.Windows.Interop.HwndSource> nesnesiyle ilişkili pencere tanıtıcısını (HWND) döndürür. Bu tanıtıcıyı, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodınızdan, örnek bunu yapmaz ancak barındırılan pencereye ileti göndermek için kullanabilirsiniz. <xref:System.Windows.Interop.HwndSource> nesnesi her ileti aldığında bir olay oluşturur. İletileri işlemek için, bir ileti işleyicisi iliştirmek ve sonra bu işleyicide iletileri işlemek üzere <xref:System.Windows.Interop.HwndSource.AddHook%2A> yöntemini çağırın.

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>WPF Içeriğine başvuru tutma
 Birçok uygulama için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğiyle daha sonra iletişim kurmak isteyeceksiniz. Örneğin, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik özelliklerini değiştirmek veya belki de <xref:System.Windows.Interop.HwndSource> nesnesi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği farklı bir şekilde barındırmak isteyebilirsiniz. Bunu yapmak için <xref:System.Windows.Interop.HwndSource> nesnesine veya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğine yönelik bir başvuruya ihtiyacınız vardır. <xref:System.Windows.Interop.HwndSource> nesnesi ve onunla ilişkili [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği pencere tanıtıcısını yok edinceye kadar bellekte kalır. Ancak, <xref:System.Windows.Interop.HwndSource> nesnesine atadığınız değişken, pencere yordamından döndükten hemen sonra kapsam dışına çıkar. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamalarda bu sorunu işlemenin normal yöntemi, statik veya genel bir değişken kullanmaktır. Ne yazık ki, bu tür değişkenlere yönetilen bir nesne atayamazsınız. <xref:System.Windows.Interop.HwndSource> nesnesi ile ilişkili pencere tanıtıcısını genel veya statik bir değişkene atayabilirsiniz, ancak bu, söz konusu tikan nesnenin kendisi için erişim sağlamaz.

 Bu soruna en basit çözüm, erişmeniz gereken herhangi bir yönetilen nesne için başvuruları tutmak üzere statik alanlar kümesi içeren bir yönetilen sınıf uygulamaktır. Örnek, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğine bir başvuru tutmak için `WPFPageHost` sınıfını ve daha sonra Kullanıcı tarafından değiştirilebilecek bir dizi özelliğin başlangıç değerlerini kullanır. Bu, üst bilgide tanımlanmıştır.

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 `GetHwnd` işlevinin ikinci bölümü, `myPage` hala kapsam içinde olduğu sürece daha sonra kullanılmak üzere bu alanlara değerler atar.

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>WPF Içeriğiyle iletişim kurma
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğine sahip iki tür iletişim vardır. Uygulama, Kullanıcı **Tamam** veya **iptal** düğmesine tıkladığında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerikten bilgileri alır. Uygulamanın arka plan rengi veya varsayılan yazı tipi boyutu gibi çeşitli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik özelliklerini değiştirmesine izin veren bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de vardır.

 Yukarıda belirtildiği gibi, Kullanıcı her iki düğmeye tıkladığında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik `OnButtonClicked` bir olay oluşturur. Uygulama bu bildirimleri almak için bu olaya bir işleyici ekler. **Tamam** düğmesine tıklandığı işleyici, kullanıcı bilgilerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğinden alır ve Statik denetimler kümesi içinde görüntüler.

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 İşleyici, `MyPageEventArgs`[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerikten özel bir olay bağımsız değişkeni nesnesi alır. Nesnenin `IsOK` özelliği **Tamam** düğmesine Tıklandıysa ve **iptal** düğmesine tıklandıysa `false` `true` olarak ayarlanır.

 **Tamam** düğmesine tıklandığı işleyici, kapsayıcı sınıfından [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğine bir başvuru alır. Daha sonra, ilişkili [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik özellikleri tarafından tutulan Kullanıcı bilgilerini toplar ve ana pencerede bilgileri göstermek için statik denetimleri kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik verileri yönetilen bir dize biçiminde olduğundan, bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] denetimi tarafından kullanılmak üzere sıralanmalıdır. **İptal** düğmesine tıklandığında, işleyici verileri statik denetimlerden temizler.

 Uygulama [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], kullanıcının [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğin arka plan rengini ve yazı tipiyle ilgili birkaç özelliği değiştirmesine izin veren radyo düğmeleri kümesi sağlar. Aşağıdaki örnek, uygulamanın pencere yordamından (WndProc) ve arka plan rengi dahil farklı iletilerde çeşitli özellikleri ayarlayan ileti işlemenin bir alıntısıdır. Diğerleri benzerdir ve gösterilmemiştir. Ayrıntılar ve bağlam için tüm örneğe bakın.

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 Arka plan rengini ayarlamak için `WPFPageHost` [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğine (`hostedPage`) bir başvuru alın ve arka plan rengi özelliğini uygun renge ayarlayın. Örnek üç renk seçeneği kullanır: orijinal renk, açık yeşil veya hafif Salmon. Özgün arka plan rengi, `WPFPageHost` sınıfında statik bir alan olarak depolanır. Diğerini ayarlamak için yeni bir <xref:System.Windows.Media.SolidColorBrush> nesnesi oluşturur ve oluşturucuyu <xref:System.Windows.Media.Colors> nesnesinden statik renkler değeri geçirin.

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>WPF sayfasını uygulama
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğini, gerçek uygulamayla ilgili herhangi bir bilgi olmadan barındırabilirsiniz ve kullanabilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik ayrı bir DLL 'de paketlenmişse, herhangi bir ortak dil çalışma zamanı (CLR) dilinde oluşturulmuş olabilir. Örnekte kullanılan C++/CLI uygulamasına ilişkin kısa bir anlatım aşağıda verilmiştir. Bu bölüm aşağıdaki alt bölümleri içerir.

- [Düzen](#page_layout)

- [Veriler konak penceresine döndürülüyor](#returning_data_to_window)

- [WPF özelliklerini ayarlama](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>Düzen
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğindeki [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeleri, ilişkili <xref:System.Windows.Controls.Label> denetimleriyle birlikte beş <xref:System.Windows.Controls.TextBox> denetimden oluşur: ad, adres, şehir, eyalet ve zip. Ayrıca iki <xref:System.Windows.Controls.Button> denetimi mevcuttur, **Tamam** ve **iptal et**

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik `WPFPage` sınıfında uygulanır. Düzen bir <xref:System.Windows.Controls.Grid> düzeni öğesiyle işlenir. Sınıfı <xref:System.Windows.Controls.Grid>devralır, bu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik kök öğesi etkin hale getirir.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik Oluşturucu gereken genişlik ve yüksekliği alır ve <xref:System.Windows.Controls.Grid> uygun şekilde boyutlandırır. Daha sonra, <xref:System.Windows.Controls.ColumnDefinition> ve <xref:System.Windows.Controls.RowDefinition> nesneleri kümesi oluşturup bunları sırasıyla <xref:System.Windows.Controls.Grid> nesne taban <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> ve <xref:System.Windows.Controls.Grid.RowDefinitions%2A> koleksiyonlara ekleyerek temel düzeni tanımlar. Bu, hücrelerin içeriğine göre belirlenen boyutları içeren beş satırlık ve yedi sütundan oluşan bir kılavuz tanımlar.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 Sonra, Oluşturucu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğelerini <xref:System.Windows.Controls.Grid>ekler. İlk öğe, kılavuzun ilk satırına ortalanmış <xref:System.Windows.Controls.Label> bir denetim olan başlık metindir.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 Sonraki satır, ad <xref:System.Windows.Controls.Label> denetimini ve ilişkili <xref:System.Windows.Controls.TextBox> denetimini içerir. Her etiket/metin kutusu çifti için aynı kod kullanıldığından, bir dizi özel yönteme yerleştirilir ve beş etiket/metin kutusu çifti için kullanılır. Yöntemler uygun denetimi oluşturur ve <xref:System.Windows.Controls.Grid> sınıfı statik <xref:System.Windows.Controls.Grid.SetColumn%2A> ve <xref:System.Windows.Controls.Grid.SetRow%2A> yöntemlerini çağırıp denetimleri uygun hücreye yerleştirir. Denetim oluşturulduktan sonra örnek, denetimi kılavuza eklemek için <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Panel.Children%2A> özelliğindeki <xref:System.Windows.Controls.UIElementCollection.Add%2A> yöntemini çağırır. Kalan etiketi/TextBox çiftlerini eklemek için kod benzerdir. Ayrıntılar için örnek koda bakın.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 İki yöntemin uygulanması aşağıdaki gibidir:

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 Son olarak, örnek, **Tamam** ve **iptal** düğmelerini ekler ve <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olaylarına bir olay işleyicisi ekler.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>Veriler konak penceresine döndürülüyor
 Her iki düğmeye tıklandığında <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı tetiklenir. Konak penceresi yalnızca işleyicileri bu olaylara ekleyebilir ve doğrudan <xref:System.Windows.Controls.TextBox> denetimlerinden verileri alabilir. Örnek biraz daha az bir doğrudan yaklaşım kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik içindeki <xref:System.Windows.Controls.Primitives.ButtonBase.Click> işler ve sonra [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğine bildirimde bulunan özel bir olay `OnButtonClicked`oluşturur. Bu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğinin konağa bildirmeden önce bazı parametre doğrulaması yapmasına olanak sağlar. İşleyici, <xref:System.Windows.Controls.TextBox> denetimlerinden metni alır ve bunu konağın bilgileri alabileceği ortak özelliklere atar.

 , WPFPage. h içindeki olay bildirimi:

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 WPFPage. cpp içinde <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisi:

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>WPF özelliklerini ayarlama
 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ana bilgisayarı, kullanıcının çeşitli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik özelliklerini değiştirmesine olanak tanır. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] taraftan, özellikleri değiştirmenin bir önemi vardır. Tüm denetimlerin yazı tiplerini denetleyen tek bir genel özellik olmadığından, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik sınıfındaki uygulama biraz daha karmaşıktır. Bunun yerine, her denetim için uygun özellik, Properties ' set erişimcileri içinde değiştirilir. Aşağıdaki örnek `DefaultFontFamily` özelliği için kodu gösterir. Özelliği ayarlamak, çeşitli denetimlerin <xref:System.Windows.Controls.Control.FontFamily%2A> özelliklerini ayarlayan özel bir yöntemi çağırır.

 WPFPage. h öğesinden:

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 WPFPage. cpp öğesinden:

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.HwndSource>
- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
