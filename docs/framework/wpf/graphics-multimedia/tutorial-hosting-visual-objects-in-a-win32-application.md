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
ms.openlocfilehash: d04357e0770bbf8eebe8f40a86a19ddc9baae3ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187421"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Eğitmen: Win32 Uygulamasında Görsel Nesneler Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]uygulamaları oluşturmak için zengin bir ortam sağlar. Ancak, Win32 koduna önemli bir yatırımınız olduğunda, kodunuzu yeniden yazmak yerine uygulamanız için işlevsellik eklemek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] daha etkili olabilir. Win32 ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulamada aynı anda kullanılan grafik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] alt sistemleri için destek sağlamak için, win32 penceresinde nesneleri barındırma için bir mekanizma sağlar.  
  
 Bu öğretici, win32 penceresinde görsel nesneleri barındıran [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [Win32 Interoperation Sample ile Hit Testi,](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)örnek bir uygulama yazmak için nasıl açıklar.  

<a name="requirements"></a>
## <a name="requirements"></a>Gereksinimler  
 Bu öğretici hem de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Win32 programlama ile temel bir aşinalık varsayar. Programlamaya temel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir giriş için [Walkthrough: İlk WPF masaüstü uygulamama](../getting-started/walkthrough-my-first-wpf-desktop-application.md)bakın. Win32 programlamabir giriş için, charles Petzold tarafından programlama *Windows* özellikle konuyla ilgili çok sayıda kitap herhangi bakın.  
  
> [!NOTE]
> Bu öğretici, ilişkili örnekten bir dizi kod örneği içerir. Ancak, okunabilirlik için, tam örnek kodu içermez. Tam örnek kod için [Win32 İşlem Numunesi ile Vur Testi'ne](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)bakın.  
  
<a name="creating_the_host_win32_window"></a>
## <a name="creating-the-host-win32-window"></a>Ana Bilgisayar Win32 Penceresini Oluşturma  
 Win32 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] penceresinde nesneleri barındırmanın <xref:System.Windows.Interop.HwndSource> anahtarı sınıftır. Bu sınıf, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesneleri Win32 penceresinde sarar ve alt penceresiolarak [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] nesnelerin sizin alt pencerenize dahil edilmesine izin verir.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Interop.HwndSource> nesneyi görsel nesneler için Win32 kapsayıcı penceresi olarak oluşturma kodu gösterilmektedir. Win32 penceresi için pencere stilini, konumunu ve diğer <xref:System.Windows.Interop.HwndSourceParameters> parametreleri ayarlamak için nesneyi kullanın.  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> Özelliğin <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> değeri WS_EX_TRANSPARENT olarak ayarlanamaz. Bu, ana bilgisayar Win32 penceresinin saydam olamayacağı anlamına gelir. Bu nedenle, ana bilgisayar Win32 penceresinin arka plan rengi üst penceresiyle aynı arka plan renginde ayarlanır.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Ana Bilgisayar Win32 Penceresine Görsel Nesneler Ekleme  
 Görsel nesneler için bir ana bilgisayar Win32 kapsayıcı penceresi oluşturduktan sonra, ona görsel nesneler ekleyebilirsiniz. Animasyonlar gibi görsel nesnelerin herhangi bir dönüşümünün ana bilgisayar Win32 penceresinin sınırlayıcı dikdörtgeninin sınırlarının ötesine geçmemesini sağlamak isteyeceksiniz.  
  
 Aşağıdaki örnek, <xref:System.Windows.Interop.HwndSource> nesneyi oluşturmak ve nesneye görsel nesneler eklemek için kodu gösterir.  
  
> [!NOTE]
> Nesnenin <xref:System.Windows.Interop.HwndSource.RootVisual%2A> <xref:System.Windows.Interop.HwndSource> özelliği, ana bilgisayar Win32 penceresine eklenen ilk görsel nesneye ayarlanır. Kök görsel nesne, görsel nesne ağacının en üstteki düğümünü tanımlar. Ana bilgisayar Win32 penceresine eklenen sonraki görsel nesneler alt nesneler olarak eklenir.  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>
## <a name="implementing-the-win32-message-filter"></a>Win32 İleti Filtresini Uygulama  
 Görsel nesneler için ana bilgisayar Win32 penceresi, uygulama kuyruğundan pencereye gönderilen iletileri işlemek için bir pencere iletifiltresi yordamı gerektirir. Pencere yordamı Win32 sisteminden iletileri alır. Bunlar giriş iletileri veya pencere yönetimi iletileri olabilir. Pencere yordamınızda isteğe bağlı olarak bir iletiyi işleyebilir veya varsayılan işlem için iletiyi sisteme iletebilirsiniz.  
  
 Görsel <xref:System.Windows.Interop.HwndSource> nesnelerin üst öğesi olarak tanımladığınız nesne, sağladığınız pencere iletifiltresi yordamına başvurmalıdır. Nesneyi <xref:System.Windows.Interop.HwndSource> oluşturduğunuzda, <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> özelliği pencere yordamına başvurmak üzere ayarlayın.  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 Aşağıdaki örnekte, iletileri yukarı sol ve sağ fare düğmesini işlemek için kod gösterilmektedir. Fare isabet konumunun koordinat değeri `lParam` parametrenin değerinde bulunur.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>
## <a name="processing-the-win32-messages"></a>Win32 İletilerini Işleme  
 Aşağıdaki örnekteki kod, ana bilgisayar Win32 penceresinde bulunan görsel nesnelerin hiyerarşisi karşı bir isabet testi nasıl gerçekleştirilin gösterir. Kök görsel nesneyi ve karşı test vurmak için koordinat <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> değerini belirtmek için yöntemi kullanarak, bir nokta görsel nesnenin geometrisi içinde olup olmadığını belirleyebilirsiniz. Bu durumda, kök görsel nesne <xref:System.Windows.Interop.HwndSource.RootVisual%2A> <xref:System.Windows.Interop.HwndSource> nesnenin özelliğinin değeridir.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Görsel nesnelere karşı isabet testi hakkında daha fazla bilgi için [Bkz. Görsel Katmanda Hit Testi.](hit-testing-in-the-visual-layer.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.HwndSource>
- [Win32 İnterİşleme Örneği ile Vur Testi](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)
- [Görsel Katmanda Tıklama Testi](hit-testing-in-the-visual-layer.md)
