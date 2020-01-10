---
title: 'Eğitmen: Win32 Uygulamasında Görsel Nesneler Barındırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual objects in Win32 code [WPF]
- Win32 code [WPF], visual objects in
- hosting [WPF], visual objects in Win32 code
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
ms.openlocfilehash: 621684e14f9d1b599c4ef60e3731f0f58f31aacd
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740167"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Eğitmen: Win32 Uygulamasında Görsel Nesneler Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], uygulamalar oluşturmak için zengin bir ortam sağlar. Ancak, Win32 kodunda önemli bir yatırımınız varsa kodunuzu yeniden yazmak yerine uygulamanıza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işlevselliği eklemek daha etkili olabilir. Bir uygulamada eşzamanlı olarak kullanılan Win32 ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafik alt sistemleri için destek sağlamak üzere [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], nesneleri Win32 penceresinde barındırmak için bir mekanizma sağlar.  
  
 Bu öğreticide, bir Win32 penceresinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görsel nesneleri barındıran [Win32 birlikte çalışma örneği ile](https://go.microsoft.com/fwlink/?LinkID=159995)bir örnek uygulamanın nasıl yazılacağı açıklanmaktadır.  

<a name="requirements"></a>   
## <a name="requirements"></a>Gereksinimler  
 Bu öğreticide hem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hem de Win32 programlamaya yönelik temel bir benzerlik vardır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programlamaya temel bir giriş için bkz. [Izlenecek yol: Ilk WPF Masaüstü](../getting-started/walkthrough-my-first-wpf-desktop-application.md)Uygulamam. Win32 programlamaya giriş için, özellikle Charles Petzold tarafından yapılan belirli *programlama pencereleri* bölümünde yer alan çok sayıda kitaplardan birine bakın.  
  
> [!NOTE]
> Bu öğretici, ilişkili örnekten bir dizi kod örneği içerir. Ancak okunabilirlik için, örnek kodu tamamen içermez. Tüm örnek kod için bkz. [Win32 birlikte çalışabilirlik örneği Ile Isabet testi](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>Konak Win32 penceresi oluşturma  
 Win32 penceresinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesneleri barındırmak için anahtar <xref:System.Windows.Interop.HwndSource> sınıftır. Bu sınıf, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesnelerini bir Win32 penceresinde sarmalar ve bunların bir alt pencere olarak [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] eklenmesine izin verir.  
  
 Aşağıdaki örnek, <xref:System.Windows.Interop.HwndSource> nesnesini görsel nesneler için Win32 kapsayıcı penceresi olarak oluşturmaya yönelik kodu gösterir. Win32 penceresinin pencere stilini, konumunu ve diğer parametrelerini ayarlamak için <xref:System.Windows.Interop.HwndSourceParameters> nesnesini kullanın.  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> özelliğinin değeri WS_EX_TRANSPARENT olarak ayarlanamaz. Bu, konak Win32 penceresinin saydam olamayacağı anlamına gelir. Bu nedenle, ana bilgisayar Win32 penceresinin arka plan rengi, üst penceresiyle aynı arka plan rengine ayarlanır.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Konak Win32 penceresine görsel nesneler ekleme  
 Görsel nesneler için bir konak Win32 kapsayıcı penceresi oluşturduktan sonra buna görsel nesneler ekleyebilirsiniz. Animasyonlar gibi görsel nesnelerin tüm dönüştürmelerinin konak Win32 penceresinin sınırlayıcı dikdörtgeninin sınırlarının ötesine genişlememesini sağlamak isteyeceksiniz.  
  
 Aşağıdaki örnek, <xref:System.Windows.Interop.HwndSource> nesnesini oluşturmak ve buna görsel nesneler eklemek için kodu gösterir.  
  
> [!NOTE]
> <xref:System.Windows.Interop.HwndSource> nesnesinin <xref:System.Windows.Interop.HwndSource.RootVisual%2A> özelliği, konak Win32 penceresine eklenen ilk görsel nesneye ayarlanır. Kök görsel nesnesi, görsel nesne ağacının en üstteki düğümünü tanımlar. Konak Win32 penceresine eklenen sonraki tüm görsel nesneler, alt nesneler olarak eklenir.  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Win32 Ileti filtresi uygulama  
 Görsel nesneler için Win32 ana bilgisayar penceresi, uygulama kuyruğundan pencereye gönderilen iletileri işlemek için bir pencere ileti filtresi yordamı gerektirir. Pencere yordamı, Win32 sisteminden iletileri alır. Bunlar giriş iletileri veya pencere yönetimi iletileri olabilir. İsteğe bağlı olarak, pencere yordamınıza bir iletiyi işleyebilir veya varsayılan işleme için iletiyi sisteme geçirebilirsiniz.  
  
 Görsel nesneler için üst öğe olarak tanımladığınız <xref:System.Windows.Interop.HwndSource> nesnesi, sağladığınız pencere ileti filtresi yordamına başvurmalıdır. <xref:System.Windows.Interop.HwndSource> nesnesini oluştururken, <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> özelliğini pencere yordamına başvuracak şekilde ayarlayın.  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 Aşağıdaki örnek, sol ve sağ fare düğmesi iletilerini işlemeye yönelik kodu gösterir. Fare isabet konumunun koordinat değeri `lParam` parametresi değerinde bulunur.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Win32 Iletilerini işleme  
 Aşağıdaki örnekteki kod, bir isabet testinin konak Win32 penceresinde bulunan görsel nesneler hiyerarşisine karşı nasıl gerçekleştirileceğini gösterir. Bir noktanın, bir görsel nesnenin geometrisi içinde olup olmadığını, kök görsel nesnesini belirtmek için <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemini kullanarak ve isabet sınaması için koordinat değerini kullanarak tanımlayabilirsiniz. Bu durumda, kök görsel nesnesi, <xref:System.Windows.Interop.HwndSource> nesnesinin <xref:System.Windows.Interop.HwndSource.RootVisual%2A> özelliğinin değeridir.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Visual Objects 'e yönelik isabet testi hakkında daha fazla bilgi için bkz. [görsel katmandaki Isabet testi](hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.HwndSource>
- [Win32 birlikte çalışabilirlik örneğiyle isabet testi örneği](https://go.microsoft.com/fwlink/?LinkID=159995)
- [Görsel Katmanda Tıklama Testi](hit-testing-in-the-visual-layer.md)
