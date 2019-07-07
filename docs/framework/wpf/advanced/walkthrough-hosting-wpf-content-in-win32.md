---
title: 'İzlenecek yol: WPF İçeriğini Win32 içinde Barındırma'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 9042548c52a7a82f75b4287323097655ffec48bf
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610428"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>İzlenecek yol: WPF İçeriğini Win32 içinde Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamaları oluşturmak için zengin bir ortam sağlar. Önemli ölçüde yatırımınız varsa [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kodu olabilir eklemek daha etkili [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özgün kodunuzu yeniden yazma yerine uygulamanızın işlevselliği. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] barındırma için basit bir mekanizma sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi.  
  
 Bu öğretici örnek bir uygulama yazmak açıklar [WPF içeriğini Win32 penceresinde örnek barındırma](https://go.microsoft.com/fwlink/?LinkID=160004), bu Konaklar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi. Bu örnek herhangi barındırmak için genişletebileceğiniz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi. Yönetilen ve yönetilmeyen kod ile karıştırma gerektirdiğinden, uygulamanın yazıldığı [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)].  

<a name="requirements"></a>   
## <a name="requirements"></a>Gereksinimler  
 Bu öğretici hem de temel bir bilindiğini varsayar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programlama. Temel bir giriş için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programlama, bkz: [Başlarken](../getting-started/index.md). Giriş konulu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programlama, herhangi bir konu çok sayıda kitaplar özellikle başvurmalısınız *Windows programlama* Charles Petzold ile.  
  
 Bu öğreticide eşlik eden örnek uygulandığından [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)], Bu öğretici kullanımını bilindiğini varsayar [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] programa [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]API'nin yanı sıra bir anlayış yönetilen kod programlama. Konusunda [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] yararlı ancak temel değildir.  
  
> [!NOTE]
>  Bu öğreticide ilişkili örnekteki kod örnekleri içerir. Ancak, okunabilirlik için tam örnek kod içermez. Tam örnek kod için bkz: [barındıran WPF içeriğini Win32 penceresinde örnek](https://go.microsoft.com/fwlink/?LinkID=160004).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Temel yordamı  
 Bu bölüm için kullandığınız temel yordamı açıklar konak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi. Kalan bölümler, her bir adımın ayrıntılarını açıklar.  
  
 Barındırma için anahtar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi <xref:System.Windows.Interop.HwndSource> sınıfı. Bu sınıf sarmalar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] içine alınacağı veren penceresinde, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] bir alt pencere olarak. Aşağıdaki yaklaşımı birleştirir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tek bir uygulamada.  
  
1. Uygulama, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik olarak yönetilen bir sınıf.  
  
2. Uygulama bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ile uygulama [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]. Var olan bir uygulama ile başlayan ve yönetilmeyen varsa [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] kod, genellikle etkinleştirebilirsiniz yönetilen kod eklemek için proje ayarlarınızı değiştirerek çağıracak şekilde `/clr` derleyici bayrağı.  
  
3. Tek iş parçacıklı grup (STA) için iş parçacığı modeli ayarlayın.  
  
4. Tanıtıcı [WM_CREATE](/windows/desktop/winmsg/wm-create)bildirim pencere yordamını ve aşağıdakileri yapın:  
  
    1. Yeni bir <xref:System.Windows.Interop.HwndSource> nesnesi olarak ana penceresi ile onun `parent` parametresi.  
  
    2. Öğesinin bir örneğini oluşturur, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik sınıfı.  
  
    3. Bir başvuru atama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesnesine <xref:System.Windows.Interop.HwndSource.RootVisual%2A> özelliği <xref:System.Windows.Interop.HwndSource>.  
  
    4. HWND içeriğini alın. <xref:System.Windows.Interop.HwndSource.Handle%2A> Özelliği <xref:System.Windows.Interop.HwndSource> nesne pencere tanıtıcısı (HWND) içerir. Uygulamanızın yönetilmeyen parçası kullanabileceğiniz bir HWND almak için cast `Handle.ToPointer()` HWND için.  
  
5. Bir başvuru tutmak için bir statik alan içeren bir yönetilen sınıf uygulamak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Bu sınıf, bir başvuru almak sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kod.  
  
6. Ata [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik statik alan.  
  
7. Bildirimleri almak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] birini veya birkaçını bir işleyici ekleyerek içerik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olayları.  
  
8. İletişim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerini ayarlayın vb. için statik alanında depolanan başvuru kullanarak içerik.  
  
> [!NOTE]
>  Ayrıca [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] uygulamak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Ancak, bu derleme gerekecek ayrı ayrı olarak bir [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)] ve başvuran [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] gelen, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulama. Yordamın geri kalanını yukarıda özetlenen benzer.

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>Konak uygulamanın uygulama
 Bu bölümde açıklanmaktadır barındırmak için nasıl [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] temel içeriği [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulama. İçerik uygulanan [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] olarak yönetilen bir sınıf. Çoğunlukla, oldukça basittir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programlama. İçerik uygulama önemli noktaları ele alınmıştır [WPF içeriği uygulama](#implementing_the_wpf_page).

<a name="autoNestedSectionsOUTLINE1"></a>
- [Temel uygulama](#the_basic_application)

- [WPF içeriği barındırma](#hosting_the_wpf_page)

- [WPF içeriği için bir başvuru tutan](#holding_a_reference)

- [WPF içeriği ile iletişim kurma](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>Temel uygulama
 Visual Studio 2005 şablonu oluşturmak için ana bilgisayar uygulaması için başlangıç noktası oluştu.

1. Visual Studio 2005 açın ve seçin **yeni proje** gelen **dosya** menüsü.

2. Seçin **Win32** listesinden [!INCLUDE[TLA2#tla_visualcpp](../../../../includes/tla2sharptla-visualcpp-md.md)] proje türleri. Varsayılan dilinizi değilse [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)], bu proje türleri altında bulabilirsiniz **diğer diller**.

3. Seçin bir **Win32 projesi** şablonu, projeye bir ad atayın ve tıklayın **Tamam** başlatmak için **Win32 Uygulama Sihirbazı**.

4. Sihirbazın varsayılan ayarları kabul edin ve tıklayın **son** projeyi başlatın.

 Temel bir şablon oluşturur [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulaması da dahil olmak üzere:

- Uygulama için bir giriş noktası.

- Bir ilişkili pencere yordamını (WndProc) içeren bir pencere.

- Sahip bir menüyü **dosya** ve **yardımcı** başlıkları. **Dosya** menü sahip bir **çıkış** uygulamayı kapatana maddesi. **Yardımcı** menü sahip bir **hakkında** basit bir iletişim kutusunu başlatan öğesi.

 Konak için kod yazmaya başlamadan önce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik, iki temel şablon değişiklikler gerekir.

 İlk olarak yönetilen kod projesi derlemektir. Varsayılan olarak, yönetilmeyen kod olarak projeyi derler. Ancak, çünkü [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulanan yönetilen kodda proje buna uygun olarak derlenmelidir.

1. İçinde proje adınıza sağ **Çözüm Gezgini** seçip **özellikleri** başlatmak için bağlam menüsünden **özellik sayfaları** iletişim kutusu.

2. Seçin **yapılandırma özellikleri** sol bölmesinde ağaç görünümünden.

3. Seçin **ortak dil çalışma zamanı** gelen destek **Proje Varsayılanları** sağ bölmede listesi.

4. Seçin **ortak dil çalışma zamanı desteği (/ clr)** aşağı açılan liste kutusundan.

> [!NOTE]
>  Bu derleyici bayrağı uygulamanızda yönetilen kod kullanmanıza olanak tanır, ancak, yönetilmeyen kod hala önceki gibi derlenir.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iş parçacığı modeli tek iş parçacıklı grup (STA) kullanır. İle düzgün çalışması için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik kodu ayarlamanız gerekir uygulamanın iş parçacığı modeli STA için giriş noktası bir özniteliği uygulayarak.

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>WPF içeriği barındırma
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçerik basit adresi giriş uygulamasıdır. Birkaç oluşur <xref:System.Windows.Controls.TextBox> kullanıcı adı, adresi ve benzeri yapılacak denetimler. Ayrıca vardır iki <xref:System.Windows.Controls.Button> denetimleri **Tamam** ve **iptal**. Kullanıcı tıkladığında **Tamam**, düğmenin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisi verileri toplayan <xref:System.Windows.Controls.TextBox> denetimleri, karşılık gelen özellikleriyle atar ve özel bir olay başlatır `OnButtonClicked`. Kullanıcı tıkladığında **iptal**, işleyicinin yalnızca başlatır `OnButtonClicked`. Olay bağımsız değişken nesnesi için `OnButtonClicked` hangi düğmesine tıklandığını belirtir bir Boole alanı içerir.

 Kod barındırmak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik için bir işleyici içinde gerçekleştirilir [WM_CREATE](/windows/desktop/winmsg/wm-create) ana penceresinde bildirim.

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 `GetHwnd` Yöntemi boyut ve konum bilgileri artı üst pencere tanıtıcısı alır ve döndürür barındırılan pencere tanıtıcısı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği.

> [!NOTE]
>  Kullanamazsınız bir `#using` yönergesi `System::Windows::Interop` ad alanı. Bunun yapılması, bir ad çakışması arasında oluşturur <xref:System.Windows.Interop.MSG> bu ad alanındaki yapısı ve MSG yapısı winuser.h içinde bildirilmiş. Bunun yerine, bu ad alanı içeriğine erişmek için tam adlarını kullanmanız gerekir.

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 Barındıramaz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] doğrudan uygulama penceresi içeriği. Bunun yerine, ilk oluşturmak bir <xref:System.Windows.Interop.HwndSource> kaydırılacak nesne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Bu nesne temelde barındırmak için tasarlanmış bir penceresi olan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Barındırabileceğiniz <xref:System.Windows.Interop.HwndSource> nesne alt öğesi olarak oluşturarak ana penceresinde bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamanızın bir parçası olan bir pencere. <xref:System.Windows.Interop.HwndSource> Oluşturucu parametresi oluşturduğunuzda için CreateWindow geçip geçmeyeceğini çok aynı olan bilgileri içeren bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] alt penceresi.

 Ardından bir örneğini oluşturun [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesne. Bu durumda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği ayrı bir sınıf uygulanan `WPFPage`kullanarak [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]. Ayrıca uygulayabileceğine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ile içerik [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Ancak, bunu yapmak için gereken ayrı bir projesi kurun ve yapı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik olarak bir [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]. Bir başvuru ekleyebilirsiniz [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] projesi ve bir örneğini oluşturmak için başvuru kullanım [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği.

 Görüntü [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik alt pencerenizde başvuru atayarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik <xref:System.Windows.Interop.HwndSource.RootVisual%2A> özelliği <xref:System.Windows.Interop.HwndSource>.

 Sonraki kod satırına bir olay işleyicisi ekler `WPFButtonClicked`, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği `OnButtonClicked` olay. Bu işleyici, kullanıcı tıkladığında çağrılır **Tamam** veya **iptal** düğmesi. Bkz: [communicating_with_the_WPF içeriği](#communicating_with_the_page) daha irdelemesi ve bu olay işleyicisi.

 Son satır gösterilen kod ile ilişkili pencere tanıtıcısı (HWND) döndürür <xref:System.Windows.Interop.HwndSource> nesne. Bu tanıtıcıdan kullanabilirsiniz, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] örneği Bunu yapmak olsa da barındırılan penceresine ileti göndermek için kod. <xref:System.Windows.Interop.HwndSource> Nesnesi bir ileti aldığı zaman her bir olay başlatır. İletileri işlemek üzere çağrı <xref:System.Windows.Interop.HwndSource.AddHook%2A> ileti işleyicisi ekleyin ve ardından bu işleyici iletileri işlemek için yöntemi.

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>WPF içeriği için bir başvuru tutan
 Birçok uygulama için iletişim isteyeceksiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] daha sonra içerik. Örneğin, değiştirmek isteyebileceğiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik özellikleri veya belki de sahip <xref:System.Windows.Interop.HwndSource> nesne konak farklı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Bunu yapmak için başvuru gerekir. <xref:System.Windows.Interop.HwndSource> nesne veya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. <xref:System.Windows.Interop.HwndSource> Nesne ve onun ilişkili [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik pencere tanıtıcısı yok kadar bellekte kalır. Ancak, değişken atadığınız <xref:System.Windows.Interop.HwndSource> penceresi yordamdan dönmez nesne kapsam dışına gider. Bu sorun her zamanki şekilde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamaları, bir statik veya genel değişkeni kullanmaktır. Ne yazık ki bu türde değişkenlere yönetilen bir nesneye atanamaz. İle ilişkili pencere tanıtıcısı atayabilirsiniz <xref:System.Windows.Interop.HwndSource> doe nesnesine erişim sağlamak için değil, ancak bir genel veya statik değişken için nesne.

 Bu sorunu en basit çözüme statik alanları erişmesi gereken herhangi bir yönetilen nesne başvurularını tutmak için bir dizi içeren bir yönetilen sınıf uygulamaktır. Örnek kullanır `WPFPageHost` başvuru için sınıf [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik yanı sıra, Başlangıç değerlerini bir dizi özelliklerini daha sonra kullanıcı tarafından değiştirilebilir. Bu üstbilgisinde tanımlanır.

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 İkinci bölümü `GetHwnd` işlevi sırasında daha sonra kullanmak için bu alanları için değerler atar `myPage` hala kapsamdadır.

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>WPF içeriği ile iletişim kurma
 İki tür ile iletişim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Uygulama bilgileri alır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik kullanıcı tıkladığında **Tamam** veya **iptal** düğmeleri. Uygulama ayrıca sahip bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] çeşitli değiştirmesine izin verir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik arka plan rengi veya varsayılan yazı tipi boyutu gibi özellikleri.

 Yukarıda belirtildiği gibi kullanıcı tıkladığında herhangi bir düğmeyi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik harekete geçirirse bir `OnButtonClicked` olay. Uygulama, bu bildirimleri almak için bu olaya bir işleyici ekler. Varsa **Tamam** düğmeye tıkladı, kullanıcı bilgileri işleyicisini alır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik ve statik denetim kümesi içinde görüntüler.

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 Bir özel olay bağımsız değişkeni nesnesinden işleyici alır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik `MyPageEventArgs`. Nesnenin `IsOK` özelliği `true` varsa **Tamam** düğmeye tıkladı, ve `false` varsa **iptal** düğmeye tıkladı.

 Varsa **Tamam** düğmeye tıkladı, işleyici için bir başvuru alır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kapsayıcı sınıfının içeriği. Ardından tutulan kullanıcı bilgilerini toplayan ilişkili [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik özellikleri ve üst pencere hakkında bilgileri görüntülemek için statik denetim kullanır. Çünkü [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik verilerinin yönetilen bir dize biçiminde, tarafından kullanılmak üzere başvuruya erişiminizde bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] denetimi. Varsa **iptal** düğmeye tıkladı, işleyici statik denetim verileri temizler.

 Uygulama [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] arka plan rengini değiştirmek kullanıcının olanak tanıyan radyo düğmeleri takımına [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik ve birden çok yazı tipi ilgili özellikler. Aşağıdaki örnek, uygulamanın pencere yordamını (WndProc) kitabından ve kendi ileti, işleme farklı iletileri, arka plan rengini de dahil olmak üzere çeşitli özelliklerini ayarlar. Diğer benzer ve gösterilmez. Tam örnek ayrıntıları ve bağlam için bkz.

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 Arka plan rengini ayarlamak için bir başvuru almak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği (`hostedPage`) öğesinden `WPFPageHost` ve uygun rengi ile arka plan rengi özelliğini ayarlayın. Örnek üç renk seçeneklerini kullanır: açık yeşil ya da Açık Somon, özgün rengi. Statik alan olarak depolanan özgün arka plan rengi `WPFPageHost` sınıfı. Diğer iki ayarlamak için yeni oluşturduğunuz <xref:System.Windows.Media.SolidColorBrush> nesnesi ve bir statik renkleri değerinden Oluşturucu geçirin <xref:System.Windows.Media.Colors> nesne.

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>WPF sayfası uygulama
 Barındırma ve kullanma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gerçek uygulama bilgileri olmadan içerik. Varsa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği, ayrı bir paketlenmiş [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], onu birinde oluşturulmuş [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] dili. Kısa bir kılavuz aşağıdadır [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] örnekte kullanılan uygulama. Bu bölüm aşağıdaki alt bölümleri içerir.

<a name="autoNestedSectionsOUTLINE2"></a>
- [Düzen](#page_layout)

- [Ana pencereyi veriyor](#returning_data_to_window)

- [WPF özelliklerini ayarlama](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>Düzen
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Öğelerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği oluşması beş <xref:System.Windows.Controls.TextBox> denetimleri, ilişkili <xref:System.Windows.Controls.Label> denetimler: Ad, adres, şehir, durum ve Zip. Ayrıca vardır iki <xref:System.Windows.Controls.Button> denetimleri **Tamam** ve **iptal et**

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçeriği içinde uygulanan `WPFPage` sınıfı. Düzen ile işlenir bir <xref:System.Windows.Controls.Grid> Düzen öğesi. Sınıfının devraldığı <xref:System.Windows.Controls.Grid>, hangi etkin hale [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik kök öğesi.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçerik oluşturucu gerekli alan genişliğini ve yüksekliğini ve boyutları <xref:System.Windows.Controls.Grid> uygun şekilde. Bir dizi oluşturarak ardından temel düzenini tanımlar <xref:System.Windows.Controls.ColumnDefinition> ve <xref:System.Windows.Controls.RowDefinition> nesneleri ve bunlara ekleme <xref:System.Windows.Controls.Grid> temel nesne <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> ve <xref:System.Windows.Controls.Grid.RowDefinitions%2A> koleksiyonları, sırasıyla. Bu hücre içeriğini tarafından belirlenen boyutlarla beş satırdan ve yedi sütundan oluşan bir kılavuz tanımlar.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 Ardından, oluşturucu ekler [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğelerine <xref:System.Windows.Controls.Grid>. Başlık metni olan ilk öğedir bir <xref:System.Windows.Controls.Label> ızgaranın ilk satırda ortalanır denetimi.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 Sonraki satırda adında <xref:System.Windows.Controls.Label> denetimi ve onun ilişkili <xref:System.Windows.Controls.TextBox> denetimi. Aynı kod her etiket/textbox çifti için kullanıldığından, özel yöntemler bir çift yerleştirilir ve beş etiket/textbox çiftleri için kullanılan. Yöntemleri uygun oluşturma denetimi ve arama <xref:System.Windows.Controls.Grid> sınıfı statik <xref:System.Windows.Controls.Grid.SetColumn%2A> ve <xref:System.Windows.Controls.Grid.SetRow%2A> yöntemleri uygun hücresinde denetimlerini yerleştirin. Denetimin oluşturulduktan sonra örnek çağırır <xref:System.Windows.Controls.UIElementCollection.Add%2A> metodunda <xref:System.Windows.Controls.Panel.Children%2A> özelliği <xref:System.Windows.Controls.Grid> kılavuza denetimi eklemek için. Kalan etiket/textbox çifti eklemek için kod benzer. Ayrıntılar için örnek koda bakın.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 İki yöntemden biriyle uygulaması aşağıdaki gibidir:

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 Son olarak, örnek ekler **Tamam** ve **iptal** düğme ve bir olay işleyici ekler, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayları.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>Ana pencereyi veriyor
 Her iki düğmesine tıklandığında, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı oluşturulur. Ana pencerenin yalnızca bu olayları işleyicileri eklemek ve verileri doğrudan <xref:System.Windows.Controls.TextBox> kontrol eder. Örnek, biraz daha az doğrudan bir yaklaşım kullanır. Bu işleme <xref:System.Windows.Controls.Primitives.ButtonBase.Click> içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik ve ardından özel bir olay başlatır `OnButtonClicked`bildirmek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Böylece [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] konak bildiren önce bazı parametre doğrulaması yapmak içerik. Metinden işleyicisini alır <xref:System.Windows.Controls.TextBox> denetler ve kendisinden konak alabilir, genel özelliklerine bilgileri atar.

 Olay bildirimi WPFPage.h:

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Olay işleyicisinde WPFPage.cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>WPF özelliklerini ayarlama
 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Konak birkaç değiştirmesine izin verir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik özellikleri. Gelen [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] tarafını özelliklerini değiştirme tek gereken bunların olduğu. Uygulamasında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri yazı tipleri tüm denetimler için hiçbir tek bir genel özellikse olduğundan içerik sınıfı biraz daha karmaşıktır. Bunun yerine, her denetim için uygun özelliği özelliklerin set erişimcisine değiştirilir. Aşağıdaki örnek kodu gösterilir `DefaultFontFamily` özelliği. Özelliği bir özel yöntemini çağırır, sırayla kümeleri <xref:System.Windows.Controls.Control.FontFamily%2A> çeşitli denetimler için özellikleri.

 WPFPage.h:

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 WPFPage.cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.HwndSource>
- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
