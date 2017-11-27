---
title: "İzlenecek yol: Win32'de WPF Barındırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords: hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fce70ab1571602fb046d3ccde9e7c014834ae6a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>İzlenecek yol: Win32'de WPF Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]uygulamaları oluşturmak için zengin bir ortam sağlar. Önemli ölçüde yatırımınız varsa [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kodu, onu olabilir eklemek için daha etkili [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özgün kodunuzu yeniden yazma işlemi yerine, uygulamanızın işlevselliği. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]barındırma için basit bir mekanizma sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi.  
  
 Bu öğreticinin örnek uygulamasının nasıl yazılacağını açıklar [Win32 penceresi örneği içerisinde WPF içeriği barındırma](http://go.microsoft.com/fwlink/?LinkID=160004), o ana [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi. Herhangi bir ana bilgisayar için bu örnek genişletebilirsiniz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi. Yönetilen ve yönetilmeyen kod karıştırma içerdiğinden, uygulama yazılmış [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)].  
  
 
  
<a name="requirements"></a>   
## <a name="requirements"></a>Gereksinimler  
 Bu öğretici temel olarak bilindiğini her ikisi de varsayar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programlama. Temel bir giriş için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programlama, bkz: [Başlarken](../../../../docs/framework/wpf/getting-started/index.md). Giriş için [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programlama herhangi konu üzerine çok sayıdaki kitaplardan özellikle başvurmalısınız *Windows programlama* Charles Petzold'un.  
  
 Bu öğretici eşlik örnek uygulanan çünkü [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)], Bu öğretici kullanımını bilindiğini varsayar [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] programa [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] yönetilen kod programlama anlaşılması artı. Aşina [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] yararlı ancak temel değildir.  
  
> [!NOTE]
>  Bu öğretici ilişkili örnekten kod örnekleri içerir. Ancak, okunabilmesi için tam örnek kodu içermez. Tam örnek kod için bkz: [barındırma WPF içeriği Win32 penceresi örneği](http://go.microsoft.com/fwlink/?LinkID=160004).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Temel yordamı  
 Bu bölüm için kullandığınız temel yordamı açıklar konak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi. Kalan bölümler her adımı ayrıntılarını açıklar.  
  
 Barındırma için anahtarı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi <xref:System.Windows.Interop.HwndSource> sınıfı. Bu sınıf sarmalar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] birleştirilir izin veren penceresinde, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] alt pencere olarak. Aşağıdaki yaklaşımlardan birleştirir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tek bir uygulamada.  
  
1.  Uygulama, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönetilen sınıf olarak içerik.  
  
2.  Uygulama bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulama [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]. Varolan bir uygulama ile başlangıç ve yönetilmeyen ise [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] kodu, genellikle etkinleştirebilirsiniz, yönetilen kod eklemek için proje ayarlarınızı değiştirerek çağırmak `/clr` derleyici bayrağı.  
  
3.  İş parçacığı modelini tek iş parçacıklı için (STA) ayarlayın.  
  
4.  İşleme [WM_CREATE](http://msdn.microsoft.com/library/ms632619.aspx)bildirim pencere yordamı ve aşağıdakileri yapın:  
  
    1.  Yeni bir <xref:System.Windows.Interop.HwndSource> üst pencere olarak nesnesiyle kendi `parent` parametresi.  
  
    2.  Bir örneğini oluşturun, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik sınıfı.  
  
    3.  Bir başvuru atamak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesnesine <xref:System.Windows.Interop.HwndSource.RootVisual%2A> özelliği <xref:System.Windows.Interop.HwndSource>.  
  
    4.  HWND içeriğini alın. <xref:System.Windows.Interop.HwndSource.Handle%2A> Özelliği <xref:System.Windows.Interop.HwndSource> nesne pencere işleyicisi (HWND) içerir. Uygulamanızın yönetilmeyen parçası kullanabileceğiniz bir HWND almak için cast `Handle.ToPointer()` HWND için.  
  
5.  Bir başvuru tutmak için statik bir alan içeren bir yönetilen sınıf uygulama, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Bu sınıf için bir başvuru almanıza yardımcı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kodu.  
  
6.  Ata [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] statik alanın içeriği.  
  
7.  ' Den bildirim almak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir veya daha fazla işleyici ekleyerek içerik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olaylar.  
  
8.  İletişim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerini ayarlamak ve benzeri için statik alanda depolanan başvuru kullanarak içerik.  
  
> [!NOTE]
>  Aynı zamanda [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] uygulamak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Ancak, bu derleme gerekecek ayrı ayrı olarak bir [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)] ve başvuran [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] gelen, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulama. Yordamın geri kalanı, yukarıda özetlenen benzer.  
  
<a name="implementing_the_application"></a>   
## <a name="implementing-the-host-application"></a>Konak uygulamanın uygulama  
 Bu bölümde açıklanmıştır ana bilgisayara nasıl [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] temel bir içerik [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulama. İçerik uygulanan [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] yönetilen sınıf olarak. Çoğunlukla, basittir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programlama. İçerik uygulama önemli yönlerini ele alınmıştır [WPF içeriği uygulama](#implementing_the_wpf_page).  
  
<a name="autoNestedSectionsOUTLINE1"></a>   
-   [Temel uygulama](#the_basic_application)  
  
-   [WPF içeriği barındırma](#hosting_the_wpf_page)  
  
-   [WPF içeriği için bir başvuru bulunduran](#holding_a_reference)  
  
-   [WPF içeriği ile iletişim](#communicating_with_the_page)  
  
<a name="the_basic_application"></a>   
### <a name="the-basic-application"></a>Temel uygulama  
 Ana bilgisayar uygulaması için başlangıç noktası oluşturmak için olan bir [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] şablonu.  
  
1.  Açık [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)]seçip **yeni proje** gelen **dosya** menüsü.  
  
2.  Seçin **Win32** listesinden [!INCLUDE[TLA2#tla_visualcpp](../../../../includes/tla2sharptla-visualcpp-md.md)] proje türleri. Varsayılan dilinizi değilse [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)], bu proje türleri altında bulabilirsiniz **diğer diller**.  
  
3.  Seçin bir **Win32 Proje** şablonu, proje için bir ad atayın ve tıklatın **Tamam** başlatmak için **Win32 Uygulama Sihirbazı'nı**.  
  
4.  Sihirbazın varsayılan ayarları kabul edin ve tıklatın **son** projeyi başlatın.  
  
 Temel bir şablon oluşturur [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulaması da dahil olmak üzere:  
  
-   Uygulama için bir giriş noktası.  
  
-   Bir ilişkili pencere yordamı (WndProc) içeren bir pencere.  
  
-   Bir menüsüyle **dosya** ve **yardımcı** başlıkları. **Dosya** menü sahip bir **çıkış** Uygulama kapandıktan öğesi. **Yardımcı** menü sahip bir **hakkında** basit bir iletişim kutusu başlatır öğesi.  
  
 Ana bilgisayara kod yazmaya başlamadan önce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik, temel şablon iki değişiklikler yapma gerekir.  
  
 İlk olarak yönetilen kod projesi derlemektir. Varsayılan olarak, projeyi yönetilmeyen kodu olarak derler. Ancak, çünkü [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulanan yönetilen kodda proje uygun şekilde derlenmesi gerekir.  
  
1.  Proje adına sağ tıklayın **Çözüm Gezgini** seçip **özellikleri** başlatmak için bağlam menüsünden **özellik sayfaları** iletişim kutusu.  
  
2.  Seçin **yapılandırma özellikleri** sol bölmede ağaç görünümünden.  
  
3.  Seçin **ortak dil çalışma zamanı** gelen destek **Proje Varsayılanları** sağ bölmede listesi.  
  
4.  Seçin **ortak dil çalışma zamanı desteği (/ clr)** aşağı açılan liste kutusundan.  
  
> [!NOTE]
>  Bu derleyici bayrağı, uygulamanızda yönetilen kod kullanmanıza olanak sağlar, ancak yönetilmeyen kodunuzu hala eskisi derlenir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]iş parçacığı modeli tek iş parçacıklı (STA) kullanır. İle düzgün çalışması için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik kodu ayarlamanız gerekir uygulamanın iş parçacığı modelini STA için giriş noktası için bir öznitelik uygulayarak.  
  
 [!code-cpp[Win32HostingWPFPage#WinMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]  
  
<a name="hosting_the_wpf_page"></a>   
### <a name="hosting-the-wpf-content"></a>WPF içeriği barındırma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçeriği bir basit adresi giriş uygulamasıdır. Birkaç oluşur <xref:System.Windows.Controls.TextBox> kullanıcı adını, adresini vb. yapılacak kontrol eder. Ayrıca vardır iki <xref:System.Windows.Controls.Button> denetimleri **Tamam** ve **iptal**. Kullanıcı tıkladığında **Tamam**, düğmenin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisi verileri toplar <xref:System.Windows.Controls.TextBox> denetimleri, karşılık gelen özellikleriyle atar ve özel bir olay başlatır `OnButtonClicked`. Kullanıcı tıkladığında **iptal**, işleyici yalnızca başlatır `OnButtonClicked`. İçin olay bağımsız değişkeni nesnesi `OnButtonClicked` hangi düğmenin tıklandığını gösteren bir Boole alanı içerir.  
  
 Ana bilgisayar koda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik için bir işleyici uygulandığına [WM_CREATE](http://msdn.microsoft.com/library/ms632619.aspx) ana penceresinde bildirim.  
  
 [!code-cpp[Win32HostingWPFPage#WMCreate](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]  
  
 `GetHwnd` Yöntemi boyutunu ve konumunu bilgi artı üst pencere tanıtıcının alır ve barındırılan pencere işleyicisini döndürür [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği.  
  
> [!NOTE]
>  Kullanarak bir `#using` için yönerge `System::Windows::Interop` ad alanı. Bunun yapılması oluşturur arasında bir ad çakışması <xref:System.Windows.Interop.MSG> bu ad alanındaki yapısı ve MSG yapısı içinde winuser.h bildirildi. Bunun yerine, bu ad alanı içeriğine erişmek için tam olarak nitelenmiş adlar kullanmanız gerekir.  
  
 [!code-cpp[Win32HostingWPFPage#GetHwnd](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]  
  
 Barındıramaz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] doğrudan uygulama pencerenizde içerik. Bunun yerine, önce oluşturduğunuz bir <xref:System.Windows.Interop.HwndSource> sarmalamak için nesne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Bu nesnenin temel olarak barındırmak için tasarlanmış bir penceredir bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Konak <xref:System.Windows.Interop.HwndSource> bir alt öğesi olarak oluşturarak üst pencere nesnesinde bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamanızı parçası olan penceresi. <xref:System.Windows.Interop.HwndSource> Oluşturucu parametreleri içeren oluşturduğunuzda CreateWindow'unkine geçip geçmeyeceğini çok aynı bilgileri bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] alt pencere.  
  
 Sonraki bir örneğini oluşturmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik nesnesi. Bu durumda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik ayrı bir sınıf olarak uygulanan `WPFPage`kullanarak [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]. Ayrıca uygulama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ile içerik [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Ancak, bunu yapmak için gereken bir ayrı projesi ayarlayın ve yapı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olarak içerik bir [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]. Bir başvuru ekleyebilir [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] proje ve bir örneğini oluşturmak için başvuru kullanım [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği.  
  
 Görüntü [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] alt pencerenizde başvuru atayarak içerik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik <xref:System.Windows.Interop.HwndSource.RootVisual%2A> özelliği <xref:System.Windows.Interop.HwndSource>.  
  
 Kodun sonraki satırında, bir olay işleyicisi ekler `WPFButtonClicked`, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik `OnButtonClicked` olay. Kullanıcı tıkladığında bu işleyici adlı **Tamam** veya **iptal** düğmesi. Bkz: [communicating_with_the_WPF içerik](#communicating_with_the_page) daha fazla irdelemesi için bu olay işleyicisi.  
  
 İle ilişkili bir pencere tanıtıcının (HWND) gösterilen kodun son satırı döndürür <xref:System.Windows.Interop.HwndSource> nesnesi. Bu işleyici gelen kullanabilirsiniz, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] örnek Bunu yapmak olsa da barındırılan penceresine iletileri göndermek için kod. <xref:System.Windows.Interop.HwndSource> Nesnesi bir ileti alır her zaman bir olay başlatır. İletileri işlemek üzere çağrı <xref:System.Windows.Interop.HwndSource.AddHook%2A> ileti işleyicisi ekleme ve bu işleyici iletileri işlemek için yöntem.  
  
<a name="holding_a_reference"></a>   
### <a name="holding-a-reference-to-the-wpf-content"></a>WPF içeriği için bir başvuru bulunduran  
 Birçok uygulama için iletişim isteyeceksiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] daha sonra içerik. Örneğin, değiştirmek isteyebilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik özellikleri veya belki de sahip <xref:System.Windows.Interop.HwndSource> nesne konak farklı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Bunu yapmak için bir başvuru gerekir <xref:System.Windows.Interop.HwndSource> nesne veya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. <xref:System.Windows.Interop.HwndSource> Nesne ve onun ilişkili [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik pencere tanıtıcının destroy kadar bellekte kalır. Ancak, değişken atadığınız <xref:System.Windows.Interop.HwndSource> penceresi yordamdan dönüş hemen nesne kapsam dışında gider. Bu sorun işlemek için her zamanki şekilde [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] uygulamalar, statik ya da genel değişkeni kullanmaktır. Ne yazık ki, bu değişkenleri türleri için yönetilen bir nesne atayamazsınız. İle ilişkili bir pencere tanıtıcının atayabilirsiniz <xref:System.Windows.Interop.HwndSource> doe nesnesine erişim sağlamak için değil ancak bu bir genel veya statik değişkene nesne.  
  
 Bu sorunu en basit çözümü erişmesi gereken tüm yönetilen nesnelerin başvuruları tutmak için statik alanları kümesini içeren bir yönetilen sınıf uygulamaktır. Örnek kullanır `WPFPageHost` bir başvuru tutmak için sınıf [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik yanı sıra, daha sonra kullanıcı tarafından değiştirilmiş ve özelliklerini bir sayının ilk değerleri. Bu başlığında tanımlanır.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageHost](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]  
  
 İkinci bölümü `GetHwnd` işlevi sırasında daha sonra kullanmak için bu alanlar için değerleri atar `myPage` hala kapsamında değil.  
  
<a name="communicating_with_the_page"></a>   
### <a name="communicating-with-the-wpf-content"></a>WPF içeriği ile iletişim  
 İle iletişim iki tür vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Uygulama bilgileri alır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik kullanıcı tıklattığında **Tamam** veya **iptal** düğmeler. Uygulama de sahip bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kullanıcının çeşitli değiştirmesine olanak tanıyan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik arka plan rengini veya varsayılan yazı tipi boyutu gibi özellikleri.  
  
 Yukarıda belirtildiği gibi kullanıcı tıkladığında ya da düğmesini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik başlatır bir `OnButtonClicked` olay. Uygulama bu bildirimleri almak için bu olay işleyici iliştirir. Varsa **Tamam** düğmesine tıklandığında, kullanıcı bilgilerini işleyici alır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik ve statik denetimleri kümesinde görüntüler.  
  
 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]  
  
 Özel olay bağımsız değişkeni nesnesinden işleyici alır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik `MyPageEventArgs`. Nesnenin `IsOK` özelliği ayarlanmış `true` varsa **Tamam** düğmesine tıklandığında, ve `false` varsa **iptal** düğmesine tıklanana.  
  
 Varsa **Tamam** düğmesine tıklandığında, işleyici için bir başvuru alır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kapsayıcı sınıfından içerik. Ardından tutulur kullanıcı bilgilerini toplar ilişkili [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik özellikleri ve kullandığı ana penceresinde bilgileri görüntülemek için statik denetimler. Çünkü [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik veri yönetilen bir dize biçiminde, tarafından kullanılmak üzere sıralanması gerekir bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] denetim. Varsa **iptal** düğmesine tıklandığında, işleyici statik denetimleri verileri temizler.  
  
 Uygulama [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] arka plan rengini değiştirmek kullanıcının izin radyo düğmeleri kümesi sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik ve birkaç yazı tipi ilgili özellikler. Aşağıdaki örnek uygulama penceresi yordamdan (WndProc) bir alıntı aynıdır ve kendi ileti, işleme arka plan rengini de dahil olmak üzere farklı iletilerde çeşitli özelliklerini ayarlar. Diğer benzer ve gösterilmez. Tam örnek ayrıntıları ve bağlam için bkz.  
  
 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]  
  
 Arka plan rengini ayarlamak için bir başvuru almak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği (`hostedPage`) gelen `WPFPageHost` ve uygun renk arka plan rengi özelliğini ayarlayın. Örnek üç renk seçeneklerini kullanır: açık yeşil ya da açık SOM, özgün rengi. Özgün arka plan rengi statik bir alana olarak depolanan `WPFPageHost` sınıfı. Diğer iki ayarlamak için yeni oluşturduğunuz <xref:System.Windows.Media.SolidColorBrush> nesne ve bir statik renkleri değerinden Oluşturucusu geçirin <xref:System.Windows.Media.Colors> nesnesi.  
  
<a name="implementing_the_wpf_page"></a>   
## <a name="implementing-the-wpf-page"></a>WPF sayfası uygulama  
 Ana bilgisayar ve kullanmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gerçek uygulama bilgisi olmadan içerik. Varsa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik, ayrı bir paketlenmiş [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], onu birinde oluşturulmuş [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] dili. Aşağıdadır kısa bir kılavuz [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] örnekte kullanılan uygulama. Bu bölüm aşağıdaki alt bölümleri içerir.  
  
<a name="autoNestedSectionsOUTLINE2"></a>   
-   [Düzen](#page_layout)  
  
-   [Konak penceresine veriyor](#returning_data_to_window)  
  
-   [WPF özelliklerini ayarlama](#set_page_properties)  
  
<a name="page_layout"></a>   
### <a name="layout"></a>Düzen  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Öğelerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik oluşur beş <xref:System.Windows.Controls.TextBox> denetimleri, ilişkili <xref:System.Windows.Controls.Label> denetimleri: ad, adres, şehir, durumu ve Zip. Ayrıca vardır iki <xref:System.Windows.Controls.Button> denetimleri **Tamam** ve **iptal et**  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçerik uygulandığına `WPFPage` sınıfı. Düzen ile işlenir bir <xref:System.Windows.Controls.Grid> Düzen öğesi. Sınıfının devraldığı <xref:System.Windows.Controls.Grid>, hangi etkili bir şekilde kılar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik kök öğesi.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçerik Oluşturucusu alır gereken genişlik ve yükseklik ve boyutları <xref:System.Windows.Controls.Grid> uygun şekilde. Bir dizi oluşturarak sonra temel düzeni tanımlar <xref:System.Windows.Controls.ColumnDefinition> ve <xref:System.Windows.Controls.RowDefinition> nesneleri ve bunlara ekleme <xref:System.Windows.Controls.Grid> nesne temel <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> ve <xref:System.Windows.Controls.Grid.RowDefinitions%2A> koleksiyonlar, sırasıyla. Bu, beş satır ve yedi sütun oluşan bir kılavuz hücreleri içeriği tarafından belirlenen boyutlarla tanımlar.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]  
  
 Ardından, Oluşturucusu ekler [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğelerine <xref:System.Windows.Controls.Grid>. Başlık metni ilk öğedir bir <xref:System.Windows.Controls.Label> ızgaranın ilk satırda ortalanmış denetim.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]  
  
 Sonraki satıra adı içeren <xref:System.Windows.Controls.Label> denetim ve onun ilişkili <xref:System.Windows.Controls.TextBox> denetim. Aynı kodu her etiket/textbox çifti için kullanıldığından, özel yöntemleri bir çiftinden yerleştirilir ve tüm beş etiket/textbox çiftleri için kullanılan. Yöntemleri uygun oluşturmak denetlemek ve arama <xref:System.Windows.Controls.Grid> statik sınıf <xref:System.Windows.Controls.Grid.SetColumn%2A> ve <xref:System.Windows.Controls.Grid.SetRow%2A> yöntemleri denetimleri uygun hücreye yerleştirin. Denetim oluşturulduktan sonra örnek çağırır <xref:System.Windows.Controls.UIElementCollection.Add%2A> yöntemi <xref:System.Windows.Controls.Panel.Children%2A> özelliği <xref:System.Windows.Controls.Grid> kılavuza denetim eklemek için. Kalan etiket/textbox çiftleri eklemek üzere kod benzer. Örnek kod Ayrıntılar için bkz.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]  
  
 İki yöntemden birini uygulaması aşağıdaki gibidir:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]  
  
 Son olarak, örnek ekler **Tamam** ve **iptal** düğmeler ve bir olay işleyicisi ekler kendi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olaylar.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]  
  
<a name="returning_data_to_window"></a>   
### <a name="returning-the-data-to-the-host-window"></a>Konak penceresine veriyor  
 Her iki düğmesine tıklandığında, kendi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı oluşturulur. Konak penceresi yalnızca bu olaylara işleyicileri ekleyin ve doğrudan veri al <xref:System.Windows.Controls.TextBox> kontrol eder. Örnek biraz daha az doğrudan bir yaklaşım kullanır. Bu işleme <xref:System.Windows.Controls.Primitives.ButtonBase.Click> içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik ve özel bir olay başlatır `OnButtonClicked`bildirmek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği. Böylece [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] konak bildiren önce bazı parametre doğrulaması yapmak içerik. Metinden işleyici alır <xref:System.Windows.Controls.TextBox> denetler ve bilgilerin alınacağı konak alabilir genel özelliklerine atar.  
  
 Olay bildirimi WPFPage.h:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]  
  
 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> WPFPage.cpp, olay işleyicisi:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]  
  
<a name="set_page_properties"></a>   
### <a name="setting-the-wpf-properties"></a>WPF özelliklerini ayarlama  
 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Ana bilgisayarın kullanıcının birkaç değiştirmesine izin verir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik özellikleri. Gelen [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] yan, olmasından özelliklerini değiştirme basitçe kurabilirsiniz. Uygulamasında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri yazı tipleri tüm denetimler için tek bir genel özellik olduğundan içerik sınıfı biraz daha karmaşıktır. Bunun yerine, her denetim için uygun özelliği özellikleri set erişimcileri değiştirilir. Aşağıdaki örnek kodunu gösterir `DefaultFontFamily` özelliği. Özelliği bir özel yöntemini çağırır bu sırayla kümeleri <xref:System.Windows.Controls.Control.FontFamily%2A> çeşitli denetimlerin özelliklerini.  
  
 WPFPage.h:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]  
  
 WPFPage.cpp:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Interop.HwndSource>  
 [WPF ve Win32 birlikte çalışma](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
