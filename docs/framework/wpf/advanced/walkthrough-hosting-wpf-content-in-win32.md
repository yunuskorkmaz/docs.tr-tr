---
title: Win32'de Ev sahibi WPF içeriği
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 8a5d556abf49c9c1f49e7853e752ebc5248d1101
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186064"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>İzlenecek yol: Win32'de WPF Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]uygulamaları oluşturmak için zengin bir ortam sağlar. Ancak, Win32 koduna önemli bir yatırımınız olduğunda, özgün [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodunuzu yeniden yazmak yerine uygulamanız için işlevsellik eklemek daha etkili olabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Win32 penceresinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik barındırma için basit bir mekanizma sağlar.  
  
 Bu öğretici, win32 penceresinde içerik barındıran [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir [Win32 Pencere Örneğinde WPF İçeriği Barındırma,](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32HostingWPFPage)örnek bir uygulama, Hosting nasıl açıklanır. Bu örneği herhangi bir Win32 penceresini barındıracak şekilde genişletebilirsiniz. Yönetilen ve yönetilmeyen kodun karıştırılması içerdiğinden, uygulama C++/CLI dilinde yazılır.  

<a name="requirements"></a>
## <a name="requirements"></a>Gereksinimler  
 Bu öğretici hem de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Win32 programlama ile temel bir aşinalık varsayar. Programlamaya temel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir giriş için [başlarken](../getting-started/index.md)bakın. Win32 programlama bir giriş için, charles Petzold tarafından özellikle *Programlama Windows,* konuyla ilgili çok sayıda kitap herhangi bir referans gerekir.  
  
 Bu öğreticiye eşlik eden örnek C++/CLI'de uygulandığından, bu öğretici Windows API'sini programlamak için C++'ın kullanımı yla ve yönetilen kod programlama anlayışına aşinalığı varsayar. C++/CLI'ye aşinalık yararlıdır, ancak gerekli değildir.  
  
> [!NOTE]
> Bu öğretici, ilişkili örnekten bir dizi kod örneği içerir. Ancak, okunabilirlik için, tam örnek kodu içermez. Örnek kodun tamamı için [Win32 Pencere Örneğinde WPF İçeriği barındırma'ya](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32HostingWPFPage)bakın.  
  
<a name="basic_procedure"></a>
## <a name="the-basic-procedure"></a>Temel Prosedür  
 Bu bölümde, win32 penceresinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği barındırmak için kullandığınız temel yordam özetlanmaktadır. Kalan bölümlerher adımın ayrıntılarını açıklar.  
  
 Win32 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] penceresinde içerik barındırmanın <xref:System.Windows.Interop.HwndSource> anahtarı sınıftır. Bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıf, içeriği Win32 penceresinde sarar ve alt penceresiolarak [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] içeriğinize dahil edilmesine izin verir. Aşağıdaki yaklaşım Win32'yi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tek bir uygulamada birleştirir.  
  
1. İçeriğinizi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönetilen bir sınıf olarak uygulayın.  
  
2. C++/CLI içeren bir Windows uygulaması uygulayın. Varolan bir uygulama ve yönetilmeyen bir C++ koduyla başlıyorsanız, proje ayarlarınızı derleyici `/clr` bayrağını içerecek şekilde değiştirerek genellikle yönetilen kodu aramasını etkinleştirebilirsiniz.  
  
3. İş parçacığı modelini tek dişli daire (STA) olarak ayarlayın.  
  
4. Pencere yordamınızda [WM_CREATE](/windows/desktop/winmsg/wm-create)bildirimini işleyebilir ve aşağıdakileri yapın:  
  
    1. Parametresi <xref:System.Windows.Interop.HwndSource> olarak ana pencere ile yeni bir nesne oluşturun. `parent`  
  
    2. İçerik sınıfınızın [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir örneğini oluşturun.  
  
    3. İçerik nesnesine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Interop.HwndSource.RootVisual%2A> <xref:System.Windows.Interop.HwndSource>bir başvuru ata.  
  
    4. İçerik için HWND'yi alın. Nesnenin <xref:System.Windows.Interop.HwndSource.Handle%2A> <xref:System.Windows.Interop.HwndSource> özelliği pencere tutamacı (HWND) içerir. Uygulamanızın yönetilmeyen bölümünde kullanabileceğiniz bir HWND almak için, bir HWND döküm. `Handle.ToPointer()`  
  
5. İçeriğinize başvuruda bulunabilmek için statik alan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeren yönetilen bir sınıf uygulayın. Bu sınıf, Win32 kodunuzdan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğe bir başvuru almanızı sağlar.  
  
6. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçeriği statik alana atayın.  
  
7. Olaylardan birine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veya daha fazlasına bir işleyici ekleyerek içerikten bildirimler alın. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
8. Özellikleri ayarlamak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] için statik alanda depoladığınız başvuruyu kullanarak içerikle iletişim kurun.  
  
> [!NOTE]
> İçeriğinizi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] için de kullanabilirsiniz. Ancak, dinamik bağlantı kitaplığı (DLL) olarak ayrı ayrı derlemeniz ve Win32 uygulamanızdan DLL'ye başvurmanız gerekir. Yordamın geri kalanı yukarıda özetlenen benzer.

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>Ana Bilgisayar Uygulamasının Uygulanması
 Bu bölümde, temel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir Win32 uygulamasında içeriğin nasıl barındırılanması açıklanmaktadır. İçeriğin kendisi Yönetilen bir sınıf olarak C++/CLI'de uygulanır. Çoğunlukla, basit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programlama. [WPF İçeriğinin Uygulanmasında](#implementing_the_wpf_page)içerik uygulamasının temel yönleri tartışılmıştır.

- [Temel Uygulama](#the_basic_application)

- [WPF İçeriğinin Barındırılıca](#hosting_the_wpf_page)

- [WPF İçeriğine Başvuru Tutma](#holding_a_reference)

- [WPF İçeriği ile iletişim kurma](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>Temel Uygulama
 Ana bilgisayar uygulamasının başlangıç noktası Visual Studio 2005 şablonu oluşturmaktı.

1. Visual Studio 2005'i açın ve **Dosya** menüsünden **Yeni Proje'yi** seçin.

2. Visual C++ proje türleri listesinden **Win32'yi** seçin. Varsayılan diliniz C++değilse, bu proje türlerini **Diğer Diller**altında bulabilirsiniz.

3. **Win32 Project** şablonu seçin, projeye bir ad atayın ve **Win32 Uygulama Sihirbazı'nı**başlatmak için **Tamam'ı** tıklatın.

4. Sihirbazın varsayılan ayarlarını kabul edin ve projeyi başlatmak için **Bitir'i** tıklatın.

 Şablon, aşağıdakiler de dahil olmak üzere temel bir Win32 uygulaması oluşturur:

- Uygulama için bir giriş noktası.

- İlişkili bir pencere yordamı (WndProc) ile bir pencere.

- **Dosya** ve **Yardım** başlıklarını içeren bir menü. **Dosya** menüsünde uygulamayı kapatan bir **Çıkış** öğesi vardır. **Yardım** menüsünde basit bir iletişim kutusu başlatan Bir **Hakkında** öğesi vardır.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçeriği barındırmak için kod yazmaya başlamadan önce, temel şablonda iki değişiklik yapmanız gerekir.

 Bunlardan ilki, projeyi yönetilen kod olarak derlemektir. Varsayılan olarak, proje yönetilmeyen kod olarak derler. Ancak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönetilen kodda uygulandığından, projenin buna göre derlemesi gerekir.

1. **Çözüm Gezgini'nde** proje adını sağ tıklatın ve Özellik **Sayfaları** iletişim kutusunu başlatmak için bağlam menüsünden **Özellikler'i** seçin.

2. Sol bölmedeki ağaç görünümünden **Yapılandırma Özellikleri'ni** seçin.

3. Sağ bölmedeki **Proje Varsayılanları** listesinden **Ortak Dil Çalışma Zamanı** desteğini seçin.

4. Açılan liste kutusundan **Ortak Dil Çalışma Süresi Desteği'ni (/clr)** seçin.

> [!NOTE]
> Bu derleyici bayrağı, uygulamanızda yönetilen kodu kullanmanıza olanak tanır, ancak yönetilmeyen kodunuz eskisi gibi derlenecektir.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tek dişli daire (STA) iş parçacığı modelini kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçerik koduyla düzgün çalışabilmek için, giriş noktasına bir öznitelik uygulayarak uygulamanın iş parçacığı modelini STA olarak ayarlamanız gerekir.

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>WPF İçeriğinin Barındırılıca
 İçerik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] basit bir adres giriş uygulamasıdır. Kullanıcı adını, <xref:System.Windows.Controls.TextBox> adresi ve benzeri bilgileri almak için çeşitli denetimlerden oluşur. Ayrıca iki <xref:System.Windows.Controls.Button> denetim, **Tamam** ve **İptal**vardır. Kullanıcı **Tamam'ı**tıklattığında, düğmenin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisi <xref:System.Windows.Controls.TextBox> denetimlerden verileri toplar, karşılık gelen özelliklere atar `OnButtonClicked`ve özel bir olay yükseltir. Kullanıcı **İptal'i**tıklattığında işleyici `OnButtonClicked`yalnızca yükseltir. Olay bağımsız değişken `OnButtonClicked` nesnesi, hangi düğmenin tıklatıldığını gösteren bir Boolean alanı içerir.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçeriği barındıracak kod, ana bilgisayar penceresindeki [bildirimin WM_CREATE](/windows/desktop/winmsg/wm-create) için bir işleyici olarak uygulanır.

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 Yöntem `GetHwnd` boyut ve konum bilgilerinin yanı sıra üst pencere tutamacını alır ve barındırılan içeriğin pencere tutamacını döndürür. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

> [!NOTE]
> Ad alanı `#using` için bir yönerge kullanamazsınız. `System::Windows::Interop` Bunu yapmak, bu ad <xref:System.Windows.Interop.MSG> alanındaki yapı ile winuser.h'de beyan edilen MSG yapısı arasında bir ad çarpışması oluşturur. Bunun yerine, bu ad alanının içeriğine erişmek için tam nitelikli adlar kullanmanız gerekir.

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçeriği doğrudan uygulama pencerenizde barındıramazsınız. Bunun yerine, önce <xref:System.Windows.Interop.HwndSource> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği sarmak için bir nesne oluşturursunuz. Bu nesne temelde bir içeriği barındırmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] için tasarlanmış bir penceredir. <xref:System.Windows.Interop.HwndSource> Uygulamanızın bir parçası olan win32 penceresinin alt öğesi olarak oluşturarak nesneyi üst pencerede barındırArsınız. Oluşturucu parametreleri, <xref:System.Windows.Interop.HwndSource> Win32 alt penceresi oluşturduğunuzda CreateWindow'a geçeceğiniz bilgilerin çoğunu içerir.

 Daha sonra içerik nesnesinin bir örneğini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oluşturursunuz. Bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] durumda, içerik c++/CLI kullanılarak `WPFPage`ayrı bir sınıf olarak uygulanır. Ayrıca [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Ancak, bunu yapmak için ayrı bir proje kurmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve bir DLL olarak içerik oluşturmak gerekir. Projenize söz söz etüt dll'ye bir başvuru ekleyebilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve bu başvuruyu içeriğin bir örneğini oluşturmak için kullanabilirsiniz.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçeriğin özelliğine bir başvuru [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Interop.HwndSource.RootVisual%2A> atayarak içeriği alt pencerenizde <xref:System.Windows.Interop.HwndSource>görüntülersiniz.

 Bir sonraki kod satırı, `WPFButtonClicked`içerik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `OnButtonClicked` olayına bir olay işleyicisi bağlar. Kullanıcı **Tamam** veya **İptal** düğmesini tıklattığında bu işleyici çağrılır. Bu olay işleyicisinin daha fazla tartışılması için [communicating_with_the_WPF içeriğe](#communicating_with_the_page) bakın.

 Gösterilen kodun son satırı, nesneyle ilişkili pencere tutamacını <xref:System.Windows.Interop.HwndSource> (HWND) döndürür. Örnek bunu yapmasa da, barındırılan pencereye ileti göndermek için Win32 kodunuzdan bu tutamacı kullanabilirsiniz. Nesne, <xref:System.Windows.Interop.HwndSource> her ileti aldığında bir olayı yükseltir. İletileri işlemek için, <xref:System.Windows.Interop.HwndSource.AddHook%2A> ileti işleyicisi eklemek için yöntemi arayın ve sonra bu işleyicideki iletileri işle.

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>WPF İçeriğine Başvuru Tutma
 Birçok uygulama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] için, içerikle daha sonra iletişim kurmak isteyeceksiniz. Örneğin, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik özelliklerini değiştirmek veya nesnenin <xref:System.Windows.Interop.HwndSource> farklı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik barındırmasını isteyebilirsiniz. Bunu yapmak için <xref:System.Windows.Interop.HwndSource> nesneye veya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğe bir başvuru yapmanız gerekir. Pencere <xref:System.Windows.Interop.HwndSource> tutamacını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yok edene kadar nesne ve ilişkili içeriği bellekte kalır. Ancak, <xref:System.Windows.Interop.HwndSource> nesneye atadığınız değişken, pencere yordamından döner dönmez kapsam dışına çıkar. Win32 uygulamaları ile bu sorunu ele almak için alışılmış yolu statik veya genel değişken kullanmaktır. Ne yazık ki, yönetilen bir nesneyi bu tür değişkenlere atayamazsınız. Nesneyle <xref:System.Windows.Interop.HwndSource> ilişkili pencere tutamacını genel veya statik bir değişkene atayabilirsiniz, ancak bu doe nesnenin kendisine erişim sağlamaz.

 Bu sorunun en basit çözümü, erişmeniz gereken yönetilen nesnelere başvuru tutmak için statik alanlar kümesi içeren yönetilen bir sınıf uygulamaktır. Örnek, `WPFPageHost` [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğe bir başvuru yutmak için sınıfı ve daha sonra kullanıcı tarafından değiştirilebilen bazı özelliklerinin başlangıç değerlerini kullanır. Bu üstbilgide tanımlanır.

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 İşlevin `GetHwnd` ikinci bölümü, kapsam devam ederken `myPage` daha sonra kullanmak üzere bu alanlara değerler atar.

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>WPF İçeriği ile iletişim kurma
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçerikle iki tür iletişim vardır. Kullanıcı **Ok** veya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] **İptal** düğmelerini tıklattığında uygulama içerikten bilgi alır. Uygulama ayrıca, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kullanıcının arka plan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rengi veya varsayılan yazı tipi boyutu gibi çeşitli içerik özelliklerini değiştirmesine olanak tanıyan bir uygulama da vardır.

 Yukarıda belirtildiği gibi, kullanıcı ya düğmeyi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tıklattığında `OnButtonClicked` içerik bir olay ortaya çıkarır. Uygulama, bu bildirimleri almak için bu olaya bir işleyici bağlar. **Tamam** düğmesi tıklanırsa, işleyici [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanıcı bilgilerini içerikten alır ve statik denetimler kümesinde görüntüler.

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 İşleyici, içerikten özel bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay `MyPageEventArgs`bağımsız değişken nesnesi alır. **Tamam** düğmesi `IsOK` tıklandığında ve `true` `false` **İptal** düğmesi tıklandığında nesnenin özelliği ayarlanır.

 **Tamam** düğmesi tıklatıldıysa, işleyici kapsayıcı sınıfından [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğe bir başvuru alır. Daha sonra ilişkili [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik özellikleri tarafından tutulan kullanıcı bilgilerini toplar ve üst penceredeki bilgileri görüntülemek için statik denetimleri kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçerik verileri yönetilen bir dize biçiminde olduğundan, Win32 denetimi tarafından kullanılmak üzere marshaled gerekir. **İptal** düğmesi tıklatılırsa, işleyici statik denetimlerden verileri temizler.

 Uygulama, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kullanıcının [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğin arka plan rengini değiştirmesine olanak tanıyan bir radyo düğmesi kümesi ve yazı tipiyle ilgili birkaç özellik sağlar. Aşağıdaki örnek, uygulamanın pencere yordamından (WndProc) ve arka plan rengi de dahil olmak üzere farklı iletilerde çeşitli özellikler belirleyen ileti işlemesinden bir alıntıdır. Diğerleri benzer ve gösterilmez. Ayrıntılar ve bağlam için tam örneğe bakın.

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 Arka plan rengini ayarlamak için, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğe`hostedPage`() bir başvuru alın `WPFPageHost` ve arka plan rengi özelliğini uygun renge ayarlayın. Örnek üç renk seçeneği kullanır: orijinal renk, açık yeşil veya açık somon. Özgün arka plan rengi `WPFPageHost` sınıfta statik bir alan olarak depolanır. Diğer ikisini ayarlamak için, yeni <xref:System.Windows.Media.SolidColorBrush> bir nesne oluşturun ve oluşturucuya <xref:System.Windows.Media.Colors> nesneden statik bir renk değeri geçirin.

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>WPF Sayfasının Uygulanması
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçeriği gerçek uygulama hakkında hiçbir bilgi sahibi olmadan barındırabilir ve kullanabilirsiniz. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçerik ayrı bir DLL'de paketlenmiş olsaydı, herhangi bir ortak dil çalışma zamanı (CLR) dilinde oluşturulmuş olabilir. Aşağıda, örnekte kullanılan C++/CLI uygulamasının kısa bir bölümü geçilir. Bu bölüm aşağıdaki alt bölümleri içerir.

- [Düzen](#page_layout)

- [Verileri Ana Bilgisayar Penceresine Döndürme](#returning_data_to_window)

- [WPF Özelliklerini Ayarlama](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>Düzen
 İçerikteki [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeler, ilişkili <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Label> denetimleri içeren beş denetimden oluşur: Ad, Adres, Şehir, Eyalet ve Zip. Ayrıca iki <xref:System.Windows.Controls.Button> denetim vardır, **Tamam** ve **İptal**

 İçerik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `WPFPage` sınıfta uygulanır. Düzen bir <xref:System.Windows.Controls.Grid> düzen öğesi ile işlenir. Sınıf, etkili <xref:System.Windows.Controls.Grid> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içerik kök öğesi yapar devralır.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] İçerik oluşturucu gerekli genişliği ve yüksekliği alır <xref:System.Windows.Controls.Grid> ve buna göre boyutlar. Daha sonra, sırasıyla nesne tabanına <xref:System.Windows.Controls.ColumnDefinition> <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> ve <xref:System.Windows.Controls.Grid.RowDefinitions%2A> koleksiyonlara bir <xref:System.Windows.Controls.Grid> dizi ve <xref:System.Windows.Controls.RowDefinition> nesne oluşturarak temel düzeni tanımlar. Bu, hücrelerin içeriği tarafından belirlenen boyutları ile beş satır ve yedi sütunlu bir ızgara tanımlar.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 Daha sonra, oluşturucu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeleri <xref:System.Windows.Controls.Grid>ekler. İlk öğe, ızgaranın ilk satırında ortalanan bir <xref:System.Windows.Controls.Label> denetim olan başlık metnidir.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 Sonraki satır Ad <xref:System.Windows.Controls.Label> denetimini <xref:System.Windows.Controls.TextBox> ve ilişkili denetimini içerir. Aynı kod her etiket/textbox çifti için kullanıldığından, bir çift özel yönteme yerleştirilir ve beş etiket/textbox çifti için de kullanılır. Yöntemler uygun denetimi oluşturur ve <xref:System.Windows.Controls.Grid> sınıfı <xref:System.Windows.Controls.Grid.SetColumn%2A> statik <xref:System.Windows.Controls.Grid.SetRow%2A> olarak çağırır ve denetimleri uygun hücreye yerleştirmek için yöntemler çağırır. Denetim oluşturulduktan sonra, örnek, <xref:System.Windows.Controls.UIElementCollection.Add%2A> denetimi <xref:System.Windows.Controls.Panel.Children%2A> <xref:System.Windows.Controls.Grid> ızgaraya eklemek için özelliğindeki yöntemi çağırır. Kalan etiket/textbox çiftleri eklemek için kod benzer. Ayrıntılar için örnek koduna bakın.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 Bu iki yöntemin uygulanması aşağıdaki gibidir:

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 Son olarak, örnek **Tamam** ve **İptal** düğmelerini ekler ve <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olaylarına bir olay işleyicisi ekler.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>Verileri Ana Bilgisayar Penceresine Döndürme
 Her iki düğme tıklatıldığında, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı yükseltilir. Ana bilgisayar penceresi yalnızca bu olaylara işleyiciler ekleyebilir <xref:System.Windows.Controls.TextBox> ve verileri doğrudan denetimlerden alabilir. Örnek biraz daha az doğrudan bir yaklaşım kullanır. İçeriğin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> içini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işler ve içeriği bildirmek `OnButtonClicked` [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] için özel bir olay yükseltir. Bu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriğin ana bilgisayara bildirmeden önce bazı parametre doğrulaması yapmasına olanak tanır. İşleyici, metni <xref:System.Windows.Controls.TextBox> denetimlerden alır ve ana bilgisayar ın bilgileri alabileceği ortak özelliklere atar.

 WPFPage.h'deki olay bildirimi:

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Olay işleyicisi, WPFPage.cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>WPF Özelliklerini Ayarlama
 Win32 ana bilgisayarı, kullanıcının [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çeşitli içerik özelliklerini değiştirmesine olanak tanır. Win32 tarafında, sadece özellikleri değişen bir konudur. Tüm denetimler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] için yazı tiplerini denetleyen tek bir genel özellik olmadığından, içerik sınıfındaki uygulama biraz daha karmaşıktır. Bunun yerine, her denetim için uygun özellik özellikleri 'ayarlanmış erişimci değiştirilir. Aşağıdaki örnek, `DefaultFontFamily` özelliğin kodunu gösterir. Özelliği ayarlamak, çeşitli denetimlerin <xref:System.Windows.Controls.Control.FontFamily%2A> özelliklerini ayarlayan özel bir yöntem çağırır.

 Kaynak:

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 Kaynak: WPFPage.cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.HwndSource>
- [WPF ve Win32 Birlikte Çalışması](wpf-and-win32-interoperation.md)
