---
title: 'Öğretici: Win32 Uygulamasında Görsel Nesneler Barındırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual objects in Win32 code [WPF]
- Win32 code [WPF], visual objects in
- hosting [WPF], visual objects in Win32 code
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
ms.openlocfilehash: c8baefbf01467a65626a77f300f34a145d5c7281
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962869"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Öğretici: Win32 Uygulamasında Görsel Nesneler Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]uygulamalar oluşturmak için zengin bir ortam sağlar. Ancak, kod içinde [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] önemli bir yatırımınız olduğunda kodunuzu yeniden yazmak yerine uygulamanıza işlevsellik eklemek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] daha etkili olabilir. Bir uygulamada eşzamanlı olarak [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kullanılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafik alt sistemleri için destek sağlamak üzere, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesneleri bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pencerede barındırmak için bir mekanizma sağlar.  
  
 Bu öğreticide, bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pencerede görsel nesneleri barındıran [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [Win32 birlikte çalışma örneği ile](https://go.microsoft.com/fwlink/?LinkID=159995)bir örnek uygulamanın nasıl yazılacağı açıklanır.  

<a name="requirements"></a>   
## <a name="requirements"></a>Gereksinimler  
 Bu öğreticide, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hem hem de programlama ile ilgili temel bir benzerlik varsayılmaktadır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Programlamaya temel bir giriş için bkz [. İzlenecek yol: İlk WPF Masaüstü](../getting-started/walkthrough-my-first-wpf-desktop-application.md)Uygulamam. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Programlamaya giriş için, özellikle Charles Petzold tarafından yapılan belirli bir *programlama* penceresinde konu üzerinde bulunan çok sayıda kitaplardan birine bakın.  
  
> [!NOTE]
> Bu öğretici, ilişkili örnekten bir dizi kod örneği içerir. Ancak okunabilirlik için, örnek kodu tamamen içermez. Tüm örnek kod için bkz. [Win32 birlikte çalışabilirlik örneği Ile Isabet testi](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>Konak Win32 penceresi oluşturma  
 <xref:System.Windows.Interop.HwndSource> Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] penceredeki[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] nesneleri barındırmak için anahtar sınıfındır. Bu sınıf, bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceredeki nesneleri sarmalanmış ve bu nesnelerin bir alt pencere [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] olarak içine eklenmesine izin verir.  
  
 Aşağıdaki örnek, nesneleri görsel nesneler için <xref:System.Windows.Interop.HwndSource> [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kapsayıcı pencere olarak oluşturmaya yönelik kodu gösterir. Pencerenin pencere stilini, konumunu ve diğer parametrelerini [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ayarlamak için <xref:System.Windows.Interop.HwndSourceParameters> nesnesini kullanın.  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> Özelliğin değeri WS_EX_TRANSPARENT olarak ayarlanamaz. Bu, konak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresinin saydam olamayacağı anlamına gelir. Bu nedenle, ana bilgisayar [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresinin arka plan rengi üst penceresiyle aynı arka plan rengine ayarlanır.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Konak Win32 penceresine görsel nesneler ekleme  
 Görsel nesneler için bir konak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kapsayıcı penceresi oluşturduktan sonra, buna görsel nesneler ekleyebilirsiniz. Animasyonlar gibi görsel nesnelerin tüm dönüştürmelerinin, ana bilgisayar [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresinin sınırlayıcı dikdörtgeninin sınırlarının ötesine genişlememesini sağlamak isteyeceksiniz.  
  
 Aşağıdaki örnek, <xref:System.Windows.Interop.HwndSource> nesnesini oluşturmak ve buna görsel nesneler eklemek için kodu gösterir.  
  
> [!NOTE]
> Nesnesinin özelliği, ana bilgisayar [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresine eklenen ilk görsel nesneye ayarlanır. <xref:System.Windows.Interop.HwndSource.RootVisual%2A> <xref:System.Windows.Interop.HwndSource> Kök görsel nesnesi, görsel nesne ağacının en üstteki düğümünü tanımlar. Konak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresine eklenen sonraki tüm görsel nesneler, alt nesneler olarak eklenir.  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Win32 Ileti filtresi uygulama  
 Görsel nesneler [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] için ana bilgisayar penceresi, uygulama kuyruğundan pencereye gönderilen iletileri işlemek için bir pencere ileti filtresi yordamı gerektirir. Pencere yordamı, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] sistemden iletileri alır. Bunlar giriş iletileri veya pencere yönetimi iletileri olabilir. İsteğe bağlı olarak, pencere yordamınıza bir iletiyi işleyebilir veya varsayılan işleme için iletiyi sisteme geçirebilirsiniz.  
  
 Görsel nesneler için üst öğe olarak tanımladığınız nesnenin,sağladığınızpencereiletisifiltreyordamınabaşvurmasıgerekir.<xref:System.Windows.Interop.HwndSource> <xref:System.Windows.Interop.HwndSource> Nesneyi oluşturduğunuzda, <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> özelliği pencere yordamına başvuracak şekilde ayarlayın.  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 Aşağıdaki örnek, sol ve sağ fare düğmesi iletilerini işlemeye yönelik kodu gösterir. Fare isabet konumunun koordinat değeri `lParam` parametrenin değerinde bulunur.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Win32 Iletilerini işleme  
 Aşağıdaki örnekteki kod, bir isabet testinin konak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresinde bulunan görsel nesneler hiyerarşisine karşı nasıl gerçekleştirileceğini gösterir. Bir noktanın, bir görsel nesnenin geometrisi içinde olup olmadığını, kök görsel nesnesini ve isabet sınaması için <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> koordinat değerini belirtmek üzere yöntemini kullanarak tanımlayabilirsiniz. Bu durumda, kök görsel nesnesi <xref:System.Windows.Interop.HwndSource.RootVisual%2A> <xref:System.Windows.Interop.HwndSource> nesnenin özelliğinin değeridir.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Visual Objects 'e yönelik isabet testi hakkında daha fazla bilgi için bkz. [görsel katmandaki Isabet testi](hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.HwndSource>
- [Win32 birlikte çalışabilirlik örneğiyle isabet testi örneği](https://go.microsoft.com/fwlink/?LinkID=159995)
- [Görsel Katmanda Tıklama Testi](hit-testing-in-the-visual-layer.md)
