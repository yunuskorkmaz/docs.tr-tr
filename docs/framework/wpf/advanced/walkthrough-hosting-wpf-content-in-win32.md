---
title: 'İzlenecek yol: WPF İçeriğini Win32 içinde Barındırma'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 9ab046c6f7c070ade9d3e474309b33afbf78370e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629642"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>İzlenecek yol: WPF İçeriğini Win32 içinde Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]uygulamalar oluşturmak için zengin bir ortam sağlar. Ancak, kod içinde [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] önemli bir yatırımınız olduğunda, özgün kodunuzu yeniden yazmak yerine uygulamanıza işlevsellik eklemek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] daha etkili olabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pencerede içerik barındırmak için basit bir mekanizma sağlar.  
  
 Bu öğreticide, bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pencerede içerik barındıran [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [bir Win32 pencere örneğinde WPF içeriği barındıran](https://go.microsoft.com/fwlink/?LinkID=160004)örnek bir uygulamanın nasıl yazılacağı açıklanmaktadır. Bu örneği, herhangi bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pencereyi barındırmak için genişletebilirsiniz. Yönetilen ve yönetilmeyen kodu karıştırmayı içerdiğinden, uygulama/Clide C++yazılır.  

<a name="requirements"></a>   
## <a name="requirements"></a>Gereksinimler  
 Bu öğreticide, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hem hem de programlama ile ilgili temel bir benzerlik varsayılmaktadır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Programlamaya temel bir giriş için [bkz. Başlarken](../getting-started/index.md). [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Programlamaya giriş için, özellikle Charles Petzold tarafından yapılan belirli bir *programlama* penceresinde, konudaki çok sayıda kitaplardan birine başvurmanız gerekir.  
  
 Bu öğreticiye eşlik eden örnek, C++/CLI ' da uygulandığından, bu öğreticide, Windows API 'sinin programlanması ve yönetilen kod programlamasını anlamak için kullanımı hakkında C++ bilgiler verilir. /CLI ile C++benzerlik yararlı ancak gerekli değildir.  
  
> [!NOTE]
>  Bu öğretici, ilişkili örnekten bir dizi kod örneği içerir. Ancak okunabilirlik için, örnek kodu tamamen içermez. Tüm örnek kod için bkz. [bir Win32 pencere ÖRNEĞINDE WPF Içeriğini barındırma](https://go.microsoft.com/fwlink/?LinkID=160004).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Temel yordam  
 Bu bölümde, içeriği bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pencerede barındırmak için kullandığınız temel yordam özetlenmektedir. Kalan bölümlerde her adımın ayrıntıları açıklanmaktadır.  
  
 İçeriği bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pencerede barındırmak için anahtar <xref:System.Windows.Interop.HwndSource> sınıfı olur. Bu sınıf, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pencerede sarmalanmış ve bu da bir alt pencere olarak uygulamanıza [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dahil olmasını sağlar. Aşağıdaki yaklaşım, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesini tek bir uygulamada birleştirir.  
  
1. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçeriğinizi yönetilen bir sınıf olarak uygulayın.  
  
2. /Cliile C++bir Windows uygulaması uygulayın. Var olan bir uygulama ve yönetilmeyen C++ kod ile başlıyorsanız, genellikle proje ayarlarınızı `/clr` derleyici bayrağını içerecek şekilde değiştirerek yönetilen kodu çağırmak için bunu etkinleştirebilirsiniz.  
  
3. İş parçacığı modelini tek iş parçacıklı Apartment (STA) olarak ayarlayın.  
  
4. [WM_CREATE](/windows/desktop/winmsg/wm-create)bildirimini pencere yordamınıza işleyin ve şunları yapın:  
  
    1. Üst pencereyle `parent` parametresi <xref:System.Windows.Interop.HwndSource> olarak yeni bir nesne oluşturun.  
  
    2. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçerik sınıfınızın bir örneğini oluşturun.  
  
    3. <xref:System.Windows.Interop.HwndSource.RootVisual%2A> Özelliğine içeriknesnesine[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir başvuru atayın. <xref:System.Windows.Interop.HwndSource>  
  
    4. İçerik için HWND 'yi alın. <xref:System.Windows.Interop.HwndSource> Nesnesinin özelliği, pencere tanıtıcısını (hwnd) içerir. <xref:System.Windows.Interop.HwndSource.Handle%2A> Uygulamanızın yönetilmeyen bölümünde kullanabileceğiniz bir hwnd almak için bir HWND 'ye atayın `Handle.ToPointer()` .  
  
5. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçeriğiniz için bir başvuru tutmak üzere statik alan içeren bir yönetilen sınıf uygulayın. Bu sınıf, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodunuzun içeriğine yönelik bir başvuru almanızı sağlar.  
  
6. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçeriği statik alana atayın.  
  
7. Bir veya daha fazla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olaya bir işleyici ekleyerek içerikten bildirim alın.  
  
8. Özellikleri ayarlamak için statik alanda depoladığınız başvuruyu kullanarak içerikleiletişimkurunvebuşekildedevamedin.[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
> [!NOTE]
>  İçeriğinizi uygulamak için de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]kullanabilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bununla birlikte, bir dinamik bağlantı kitaplığı (dll) olarak ayrı olarak derlemek ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamanızdan dll 'ye başvurmanız gerekir. Yordamın geri kalanı yukarıda ana hatlarıyla benzerdir.

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>Konak uygulamasını uygulama
 Bu bölümde, basit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bir uygulamada içeriğin nasıl barındırılacağını açıklanmaktadır. İçerik, bir yönetilen sınıf olarak C++/CLI ' da uygulanır. Çoğu bölümde, basit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir programlama olur. İçerik uygulamasının temel yönleri [WPF Içeriğini uygulama](#implementing_the_wpf_page)bölümünde ele alınmıştır.

<a name="autoNestedSectionsOUTLINE1"></a>
- [Temel uygulama](#the_basic_application)

- [WPF Içeriğini barındırma](#hosting_the_wpf_page)

- [WPF Içeriğine başvuru tutma](#holding_a_reference)

- [WPF Içeriğiyle iletişim kurma](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>Temel uygulama
 Ana bilgisayar uygulaması için başlangıç noktası, bir Visual Studio 2005 şablonu oluşturmaktır.

1. Visual Studio 2005 ' i açın ve **Dosya** menüsünden **Yeni proje** ' yi seçin.

2. [!INCLUDE[TLA2#tla_visualcpp](../../../../includes/tla2sharptla-visualcpp-md.md)] Proje türleri listesinden **Win32** öğesini seçin. Varsayılan diliniz yoksa C++, bu proje türlerini **diğer diller**altında bulacaksınız.

3. Bir **Win32 Proje** şablonu seçin, projeye bir ad atayın ve **Win32 uygulama sihirbazını**başlatmak için **Tamam** ' a tıklayın.

4. Sihirbazın varsayılan ayarlarını kabul edin ve projeyi başlatmak için **son** ' a tıklayın.

 Şablon, aşağıdakiler dahil olmak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] üzere temel bir uygulama oluşturur:

- Uygulama için bir giriş noktası.

- İlişkili bir pencere yordamıyla (WndProc) bir pencere.

- **Dosya** ve **Yardım** başlıkları içeren bir menü. **Dosya** menüsünde, uygulamayı kapatan bir **Çıkış** öğesi vardır. **Yardım** menüsünde basit bir iletişim kutusu başlatan **hakkında** bir öğe bulunur.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçeriği barındırmak için kod yazmaya başlamadan önce, temel şablonda iki değişiklik yapmanız gerekir.

 Birincisi, projeyi yönetilen kod olarak derlemek olur. Varsayılan olarak, proje yönetilmeyen kod olarak derlenir. Ancak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönetilen kodda uygulandığından, projenin buna göre derlenmesi gerekir.

1. **Çözüm Gezgini** ' de proje adına sağ tıklayın ve bağlam menüsünden **Özellikler** ' i seçerek **Özellik sayfaları** iletişim kutusunu başlatın.

2. Sol bölmedeki ağaç görünümünden **yapılandırma özellikleri** ' ni seçin.

3. Sağ bölmedeki **Proje Varsayılanları** listesinden **ortak dil çalışma zamanı** desteği ' ni seçin.

4. Açılan liste kutusundan **ortak dil çalışma zamanı desteği (/CLR)** öğesini seçin.

> [!NOTE]
>  Bu derleyici bayrağı uygulamanızda yönetilen kod kullanmanıza izin verir, ancak yönetilmeyen kodunuz daha önce olduğu gibi derlenmeye devam eder.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tek iş parçacıklı Apartment (STA) iş parçacığı modelini kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçerik kodu ile düzgün bir şekilde çalışabilmek için, giriş noktasına bir öznitelik uygulayarak uygulamanın iş parçacığı modelini STA olarak ayarlamanız gerekir.

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>WPF Içeriğini barındırma
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçerik, basit bir adres girişi uygulamasıdır. Kullanıcı adı, adres <xref:System.Windows.Controls.TextBox> vb. almak için çeşitli denetimlerden oluşur. Ayrıca, **Tamam** ve <xref:System.Windows.Controls.Button> **iptal**' de iki denetim vardır. Kullanıcı **Tamam**' ı tıklattığında, düğmenin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisi <xref:System.Windows.Controls.TextBox> denetimlerden verileri toplar, bunları karşılık gelen özelliklere atar ve özel bir olay `OnButtonClicked`oluşturur. Kullanıcı **iptal**' i tıklattığında işleyici yalnızca yükseltilir `OnButtonClicked`. İçin `OnButtonClicked` olay bağımsız değişkeni nesnesi, hangi düğmenin tıklandığını gösteren bir Boole alanı içerir.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçeriği barındıracak kod, ana bilgisayar penceresinde [WM_CREATE](/windows/desktop/winmsg/wm-create) bildirimi için bir işleyicide uygulanır.

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 Yöntemi `GetHwnd` , boyut ve konum bilgilerini ve üst pencere tanıtıcısını alır ve barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğin pencere tanıtıcısını döndürür.

> [!NOTE]
>  Ad`System::Windows::Interop` alanı için bir `#using` yönerge kullanamazsınız. Bunun yapılması, <xref:System.Windows.Interop.MSG> bu ad alanındaki yapı ve Winuser. h içinde belirtilen MSG yapısı arasında bir ad çakışması oluşturur. Bunun yerine, bu ad alanının içeriğine erişmek için tam nitelikli adlar kullanmanız gerekir.

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçeriği doğrudan uygulama pencerenizde barındıryükleyemezsiniz. Bunun yerine, önce <xref:System.Windows.Interop.HwndSource> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği kaydırmak için bir nesne oluşturun. Bu nesne temelde bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği barındırmak için tasarlanan bir penceredir. Uygulamayı, uygulamanızın <xref:System.Windows.Interop.HwndSource> bir parçası olan bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pencerenin alt öğesi olarak oluşturarak ana pencerede barındırabilirsiniz. Oluşturucu <xref:System.Windows.Interop.HwndSource> parametreleri, bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] alt pencere oluştururken CreateWindow 'a geçirdiğiniz bilgilerin çoğunu içerir.

 Bir sonraki adımda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesnesinin bir örneğini oluşturun. Bu durumda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , içerik,/clikullanılarak `WPFPage` C++ayrı bir sınıf olarak uygulanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ayrıca[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]içeriğini de uygulayabilirsiniz. Ancak bunu yapmak için ayrı bir proje ayarlamanız ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği bir dll olarak oluşturmanız gerekir. Projenize bu DLL 'ye bir başvuru ekleyebilir ve bu başvuruyu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik örneği oluşturmak için kullanabilirsiniz.

 İçeriğine bir başvuru [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] atayarak<xref:System.Windows.Interop.HwndSource.RootVisual%2A> ,<xref:System.Windows.Interop.HwndSource>içeriği alt pencerenizde görüntüleyin.

 Sonraki kod satırı, `WPFButtonClicked` [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik `OnButtonClicked` olayına bir olay işleyicisi ekler. Bu işleyici Kullanıcı **Tamam** veya **iptal** düğmesine tıkladığında çağrılır. Bu olay işleyicisi hakkında daha fazla bilgi için bkz. [communicating_with_the_WPF Content](#communicating_with_the_page) .

 Gösterilen kodun son satırı, <xref:System.Windows.Interop.HwndSource> nesnesiyle ilişkili pencere tanıtıcısını (hwnd) döndürür. Bu tanıtıcıyı kodınızdan [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] , barındırılan pencereye ileti göndermek için kullanabilirsiniz, ancak örnek bunu yapmaz. <xref:System.Windows.Interop.HwndSource> Nesnesi bir iletiyi her aldığında bir olay oluşturur. İletileri işlemek için, bir ileti işleyicisi <xref:System.Windows.Interop.HwndSource.AddHook%2A> iliştirmek ve sonra bu işleyicide iletileri işlemek üzere yöntemini çağırın.

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>WPF Içeriğine başvuru tutma
 Birçok uygulama için, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerikle daha sonra iletişim kurmak isteyeceksiniz. Örneğin, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik özelliklerini değiştirmek veya belki de <xref:System.Windows.Interop.HwndSource> nesne farklı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik barındırmak isteyebilirsiniz. Bunu yapmak için, <xref:System.Windows.Interop.HwndSource> nesne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veya içeriğe bir başvuru gerekir. Nesne ve ilişkili [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği, pencere tanıtıcısını yok edinceye kadar bellekte kalır. <xref:System.Windows.Interop.HwndSource> Ancak, <xref:System.Windows.Interop.HwndSource> nesnesine atadığınız değişken, pencere yordamından döndükten hemen sonra kapsam dışına çıkar. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Uygulamalarda bu sorunu işlemenin normal yöntemi, statik veya genel bir değişken kullanmaktır. Ne yazık ki, bu tür değişkenlere yönetilen bir nesne atayamazsınız. <xref:System.Windows.Interop.HwndSource> Nesneyle ilişkili pencere tanıtıcısını genel veya statik bir değişkene atayabilir, ancak bu, söz konusu tikan nesnenin kendisi için erişim sağlamaz.

 Bu soruna en basit çözüm, erişmeniz gereken herhangi bir yönetilen nesne için başvuruları tutmak üzere statik alanlar kümesi içeren bir yönetilen sınıf uygulamaktır. Örnek, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik başvurusunu `WPFPageHost` tutmak için sınıfını ve daha sonra Kullanıcı tarafından değiştirilebilecek bir dizi özelliğin başlangıç değerlerini kullanır. Bu, üst bilgide tanımlanmıştır.

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 `GetHwnd` İşlevin ikinci bölümü, daha sonra kullanılmak üzere bu alanlara değerler atar, ancak `myPage` hala kapsamdadır.

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>WPF Içeriğiyle iletişim kurma
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçerikle iki tür iletişim vardır. Kullanıcı **Tamam** veya **iptal** düğmelerine tıkladığında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama içerikten bilgi alır. Uygulamanın arka plan rengi veya [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] varsayılan yazı tipi boyutu gibi çeşitli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik özelliklerini değiştirmesine izin veren bir de vardır.

 Yukarıda belirtildiği gibi, Kullanıcı herhangi bir düğmeye [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tıkladığında içerik bir `OnButtonClicked` olay oluşturur. Uygulama bu bildirimleri almak için bu olaya bir işleyici ekler. **Tamam** düğmesine tıklandığı işleyici, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerikten Kullanıcı bilgilerini alır ve Statik denetimler kümesi içinde görüntüler.

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 İşleyici, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `MyPageEventArgs`içerikten özel bir olay bağımsız değişkeni nesnesi alır. Nesnenin `IsOK` özelliği **Tamam** düğmesine tıklandıysa `true` ve `false` **iptal** düğmesi tıklandıysa olarak ayarlanır.

 **Tamam** düğmesine tıklandığı işleyici kapsayıcı sınıfından [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğe bir başvuru alır. Daha sonra, ilişkili [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik özellikleri tarafından tutulan Kullanıcı bilgilerini toplar ve ana pencerede bilgileri göstermek için statik denetimleri kullanır. İçerik verileri yönetilen bir dize biçiminde olduğundan, bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] denetim tarafından kullanılmak üzere sıralanmalıdır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] **İptal** düğmesine tıklandığında, işleyici verileri statik denetimlerden temizler.

 Uygulama [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , kullanıcının [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğin arka plan rengini ve yazı tipiyle ilgili birkaç özelliği değiştirmesine izin veren radyo düğmeleri kümesi sağlar. Aşağıdaki örnek, uygulamanın pencere yordamından (WndProc) ve arka plan rengi dahil farklı iletilerde çeşitli özellikleri ayarlayan ileti işlemenin bir alıntısıdır. Diğerleri benzerdir ve gösterilmemiştir. Ayrıntılar ve bağlam için tüm örneğe bakın.

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 Arka plan rengini ayarlamak için, ( [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `hostedPage`) `WPFPageHost` içeriğine bir başvuru alın ve arka plan rengi özelliğini uygun renge ayarlayın. Örnek üç renk seçeneği kullanır: orijinal renk, açık yeşil veya hafif Salmon. Özgün arka plan rengi, `WPFPageHost` sınıfında statik bir alan olarak depolanır. Diğerini ayarlamak için yeni <xref:System.Windows.Media.SolidColorBrush> bir nesne oluşturur ve oluşturucuyu <xref:System.Windows.Media.Colors> nesnesinden statik renkler değeri geçirin.

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>WPF sayfasını uygulama
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçeriği gerçek uygulamayla ilgili herhangi bir bilgi olmadan barındırabilirsiniz ve kullanabilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçerik ayrı bir dll 'de paketlenmişse, herhangi bir ortak dil çalışma zamanı (CLR) dilinde oluşturulmuş olabilir. Örnekte kullanılan C++/CLI uygulamasına ilişkin kısa bir anlatım aşağıda verilmiştir. Bu bölüm aşağıdaki alt bölümleri içerir.

<a name="autoNestedSectionsOUTLINE2"></a>
- [Düzen](#page_layout)

- [Veriler konak penceresine döndürülüyor](#returning_data_to_window)

- [WPF özelliklerini ayarlama](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>Düzen
 İçerikteki öğeler, ilişkili<xref:System.Windows.Controls.Label> denetimlerle birlikte beş <xref:System.Windows.Controls.TextBox> denetimden oluşur: [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ad, adres, şehir, eyalet ve posta. Ayrıca, **Tamam** ve <xref:System.Windows.Controls.Button> **iptal et** olmak üzere iki denetim vardır

 İçerik, `WPFPage` sınıfında uygulanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Düzen bir <xref:System.Windows.Controls.Grid> düzen öğesiyle işlenir. Sınıfı öğesinden <xref:System.Windows.Controls.Grid>devralır, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bu, içerik kök öğesi etkin bir şekilde oluşturur.

 İçerik Oluşturucu gerekli genişliği ve yüksekliği alır ve <xref:System.Windows.Controls.Grid> uygun şekilde boyutları. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Daha sonra temel düzeni tanımlar <xref:System.Windows.Controls.ColumnDefinition> ve <xref:System.Windows.Controls.RowDefinition> nesneler kümesi oluşturup nesneleri sırasıyla <xref:System.Windows.Controls.Grid> nesne tabanına <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> ve <xref:System.Windows.Controls.Grid.RowDefinitions%2A> koleksiyonlara ekler. Bu, hücrelerin içeriğine göre belirlenen boyutları içeren beş satırlık ve yedi sütundan oluşan bir kılavuz tanımlar.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 Sonra, Oluşturucu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğelerini <xref:System.Windows.Controls.Grid>öğesine ekler. İlk öğe, kılavuzun ilk satırına ortalanmış bir <xref:System.Windows.Controls.Label> denetim olan başlık metindir.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 Sonraki satır, ad <xref:System.Windows.Controls.Label> denetimini ve ilişkili <xref:System.Windows.Controls.TextBox> denetimini içerir. Her etiket/metin kutusu çifti için aynı kod kullanıldığından, bir dizi özel yönteme yerleştirilir ve beş etiket/metin kutusu çifti için kullanılır. Yöntemler uygun denetimi oluşturur ve denetimleri uygun hücreye yerleştirmek için <xref:System.Windows.Controls.Grid> static <xref:System.Windows.Controls.Grid.SetColumn%2A> ve <xref:System.Windows.Controls.Grid.SetRow%2A> Methods sınıfını çağırır. Denetim oluşturulduktan sonra örnek, denetimi kılavuza eklemek <xref:System.Windows.Controls.UIElementCollection.Add%2A> <xref:System.Windows.Controls.Grid> için öğesinin <xref:System.Windows.Controls.Panel.Children%2A> özelliği üzerinde yöntemini çağırır. Kalan etiketi/TextBox çiftlerini eklemek için kod benzerdir. Ayrıntılar için örnek koda bakın.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 İki yöntemin uygulanması aşağıdaki gibidir:

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 Son olarak, örnek, **Tamam** ve **iptal** düğmelerini ekler ve <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olaylarına bir olay işleyicisi ekler.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>Veriler konak penceresine döndürülüyor
 Düğmeye tıklandığında, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı tetiklenir. Ana bilgisayar penceresi yalnızca bu olaylara işleyicileri iliştirebilir ve doğrudan <xref:System.Windows.Controls.TextBox> denetimlerden verileri alabilir. Örnek biraz daha az bir doğrudan yaklaşım kullanır. İçeriği içinde işler <xref:System.Windows.Controls.Primitives.ButtonBase.Click> ve sonra [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğe bildirimde bulunan özel bir olay `OnButtonClicked`oluşturur. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğin konağa bildirmeden önce bazı parametre doğrulaması yapmasına olanak sağlar. İşleyici, <xref:System.Windows.Controls.TextBox> denetimlerden metni alır ve ana bilgisayarın bilgileri alabileceği ortak özelliklere atar.

 , WPFPage. h içindeki olay bildirimi:

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 WPFPage. cpp içindeki olayişleyicisi:<xref:System.Windows.Controls.Primitives.ButtonBase.Click>

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>WPF özelliklerini ayarlama
 Ana bilgisayar, kullanıcının çeşitli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik özelliklerini değiştirmesine izin verir. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Taraftan, özelliklerin değiştirilmesinin bir önemi vardır. Tüm denetimlerin yazı tiplerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetleyen tek bir genel özellik olmadığından, içerik sınıfındaki uygulama biraz daha karmaşıktır. Bunun yerine, her denetim için uygun özellik, Properties ' set erişimcileri içinde değiştirilir. Aşağıdaki örnek, `DefaultFontFamily` özelliği için kodu gösterir. Özelliği ayarlamak, çeşitli denetimlerin <xref:System.Windows.Controls.Control.FontFamily%2A> özelliklerini ayarlayan özel bir yöntemi çağırır.

 WPFPage. h öğesinden:

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 WPFPage. cpp öğesinden:

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.HwndSource>
- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
