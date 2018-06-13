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
ms.openlocfilehash: cc78dfd22b0ad2726ce8870a4e03f539ec691d85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565356"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Eğitmen: Win32 Uygulamasında Görsel Nesneler Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamaları oluşturmak için zengin bir ortam sağlar. Önemli ölçüde yatırımınız varsa [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kodu, onu olabilir eklemek için daha etkili [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanıza işlevsellik yerine kodunuzu yeniden yazma. Desteği sağlamak için [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aynı anda bir uygulamada kullanılan grafik alt sistemlerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesneleri barındırmak için bir mekanizma sağlar bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi.  
  
 Bu öğreticinin örnek uygulamasının nasıl yazılacağını açıklar [isabet testi Win32 birlikte çalışabilirlik örneği ile](http://go.microsoft.com/fwlink/?LinkID=159995), o ana [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual nesnelerini bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi.  
  

  
<a name="requirements"></a>   
## <a name="requirements"></a>Gereksinimler  
 Bu öğretici temel olarak bilindiğini her ikisi de varsayar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programlama. Temel bir giriş için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programlama, bkz: [gözden geçirme: ilk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md). Giriş için [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programlama, çok sayıda kitaplardan herhangi birine konuyla ilgili özellikle bkz *Windows programlama* Charles Petzold'un.  
  
> [!NOTE]
>  Bu öğretici ilişkili örnekten kod örnekleri içerir. Ancak, okunabilmesi için tam örnek kodu içermez. Tam örnek kod için bkz: [isabet testi Win32 birlikte çalışabilirlik örneği ile](http://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>Win32 konak penceresi oluşturma  
 Barındırma için anahtarı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesnelerini bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi <xref:System.Windows.Interop.HwndSource> sınıfı. Bu sınıf sarmalar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesnelerini bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] birleştirilir vermeden penceresinde, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] alt pencere olarak.  
  
 Aşağıdaki örnek oluşturma kodunu gösterir <xref:System.Windows.Interop.HwndSource> olarak nesne [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] görsel nesneler için kapsayıcı pencere. Pencere stili, konumu ve diğer parametreleri ayarlamak için [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi, kullanım <xref:System.Windows.Interop.HwndSourceParameters> nesnesi.  
  
 [!code-csharp[VisualsHitTesting#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
>  Değerini <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> için WS_EX_TRANSPARENT özelliği ayarlanamaz. Ana bilgisayar buna [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi saydam olamaz. Bu nedenle, konak arka plan rengini [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi aynı arka plan rengi kendi üst penceresi olarak ayarlanır.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Win32 konak penceresine görsel nesneler ekleme  
 Bir konak oluşturduktan sonra [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kapsayıcı pencere görsel nesneler için görsel nesneler için ekleyebilirsiniz. Görsel nesnelerinin animasyonları gibi herhangi bir dönüştürme konak sınırları genişletmek değil olmak isteyeceksiniz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresini çevreleyen dikdörtgenin.  
  
 Aşağıdaki örnek oluşturma kodunu gösterir <xref:System.Windows.Interop.HwndSource> nesne ve görsel nesneler ekleme.  
  
> [!NOTE]
>  <xref:System.Windows.Interop.HwndSource.RootVisual%2A> Özelliği <xref:System.Windows.Interop.HwndSource> nesne konağa eklenen ilk görsel nesne kümesine [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi. Kök görsel nesne görsel nesne ağacının en üstteki düğümü tanımlar. Ana bilgisayara eklenen sonraki tüm görsel nesneler [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi, alt nesneler olarak eklenir.  
  
 [!code-csharp[VisualsHitTesting#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Win32 İleti Filtresi Uygulama  
 Ana bilgisayar [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresinde görsel nesneler için pencereyi uygulama sırasından gönderilen iletileri işlemek için pencere İleti Filtresi yordamına gerektirir. Pencere yordamı gelen iletileri alan [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] sistem. Bunlar giriş iletileri veya pencere yönetim iletileri olabilir. İsteğe bağlı olarak, bir ileti penceresinde yordamda işlemek veya varsayılan işleme için sisteme ileti geçirin.  
  
 <xref:System.Windows.Interop.HwndSource> Görsel nesneler için üst sağladığınız pencere İleti Filtresi yordamına başvurmalıdır olarak tanımladığınız nesnesi. Oluştururken <xref:System.Windows.Interop.HwndSource> nesne, ayarlamak <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> pencere yordamına başvurmak için özellik.  
  
 [!code-csharp[VisualsHitTesting#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 Aşağıdaki örnek, sol ve sağ fare düğmesini iletilerini işlemek için kod gösterir. Fare koordinat değeri isabet konumu değerinde bulunan `lParam` parametresi.  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Win32 iletileri işleme  
 Aşağıdaki örnek kodda ana bilgisayarda yer alan visual nesneleri hiyerarşisini karşı isabet testi nasıl gerçekleştirileceğini gösterir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi. Kullanarak bir noktası görsel bir nesne geometrisi içinde olup olmadığını tespit edebilirsiniz <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi kök görsel nesne ve isabet sınaması için koordinat değerini belirtin. Bu durumda, kök görsel nesne değeri <xref:System.Windows.Interop.HwndSource.RootVisual%2A> özelliği <xref:System.Windows.Interop.HwndSource> nesnesi.  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Görsel nesnelere karşı isabet testi ile ilgili daha fazla bilgi için bkz: [isabet testi görsel katmandaki](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Interop.HwndSource>  
 [İsabet testi Win32 birlikte çalışabilirlik örneği ile](http://go.microsoft.com/fwlink/?LinkID=159995)  
 [Görsel Katmanda Tıklama Testi](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
