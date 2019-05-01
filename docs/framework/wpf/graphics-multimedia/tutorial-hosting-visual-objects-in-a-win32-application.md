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
ms.openlocfilehash: b260f96246f0d9e5447b74a05e1396bfef176197
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053086"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Öğretici: Win32 Uygulamasında Görsel Nesneler Barındırma
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamaları oluşturmak için zengin bir ortam sağlar. Önemli ölçüde yatırımınız varsa [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kodu olabilir eklemek daha etkili [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanıza işlevsellik yerine, kodu yeniden yazın. Destek sağlamak üzere [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafik alt sistemlerin aynı anda bir uygulamada kullanılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesneleri barındırmak için bir mekanizma sağlar bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi.  
  
 Bu öğretici örnek bir uygulama yazmak açıklar [Win32 birlikte çalışması örnek ile isabet sınaması](https://go.microsoft.com/fwlink/?LinkID=159995), bu Konaklar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesnelerini bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi.  

<a name="requirements"></a>   
## <a name="requirements"></a>Gereksinimler  
 Bu öğretici hem de temel bir bilindiğini varsayar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programlama. Temel bir giriş için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programlama, bkz: [izlenecek yol: İlk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md). Giriş konulu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programlama, çok sayıda kitaplardan herhangi birine konuyla ilgili özellikle bkz *Windows programlama* Charles Petzold ile.  
  
> [!NOTE]
>  Bu öğreticide ilişkili örnekteki kod örnekleri içerir. Ancak, okunabilirlik için tam örnek kod içermez. Tam örnek kod için bkz: [Win32 birlikte çalışması örnek ile isabet sınaması](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>Win32 konak penceresi oluşturma  
 Barındırma için anahtar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesneler bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi <xref:System.Windows.Interop.HwndSource> sınıfı. Bu sınıf sarmalar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesneler bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] bunları içine alınacağı izin verme penceresinde, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] bir alt pencere olarak.  
  
 Aşağıdaki örnek oluşturmak için kod gösterir <xref:System.Windows.Interop.HwndSource> nesnesinin [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] görsel nesneler için kapsayıcı penceresi. Pencere stili, konumu ve diğer parametreler için ayarlanacak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresinde kullanım <xref:System.Windows.Interop.HwndSourceParameters> nesne.  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
>  Değerini <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> WS_EX_TRANSPARENT için özelliği ayarlanamaz. Konak buna [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi saydam olamaz. Bu nedenle, arka plan rengi konağının [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi aynı arka plan rengine ilişkin ana pencerelere olarak ayarlanır.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Görsel nesneler için Win32 konak penceresi ekleme  
 Bir konak oluşturduktan sonra [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kapsayıcı penceresi görsel nesneler için görsel nesneler ekleyebilirsiniz. Herhangi bir dönüştürme gibi animasyon, görsel nesneler konak sınırlarının ötesine genişletmek değil olmak isteyeceksiniz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresini çevreleyen dikdörtgen.  
  
 Aşağıdaki örnek oluşturmak için kod gösterir <xref:System.Windows.Interop.HwndSource> nesne ve görsel nesneler ekleme.  
  
> [!NOTE]
>  <xref:System.Windows.Interop.HwndSource.RootVisual%2A> Özelliği <xref:System.Windows.Interop.HwndSource> nesne konağa eklenen ilk görsel nesne kümesine [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi. Kök görsel nesneyi görsel nesne ağacının en üst düğümü tanımlar. Ana bilgisayara eklenmiş sonraki tüm görsel nesneler [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi, alt nesne olarak eklenir.  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Win32 İleti Filtresi Uygulama  
 Konak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] görsel nesneler için pencere penceresine uygulama sıradan gönderilen iletileri işlemek için bir pencere ileti filtre yordamı gerektirir. Pencere yordamı iletiler alır [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] sistem. Bu, giriş iletileri veya pencere yönetimi iletileri olabilir. İsteğe bağlı olarak, bir ileti penceresinde yordamınız işlemek veya varsayılan işleme sistemine ileti geçirin.  
  
 <xref:System.Windows.Interop.HwndSource> Üst görsel nesneler için sağladığınız pencere ileti filtre yordamı başvurmalıdır olarak tanımladığınız nesne. Oluştururken <xref:System.Windows.Interop.HwndSource> nesne, ayarlama <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> pencere yordamını başvurmak için özellik.  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 Aşağıdaki örnek, sol ve sağ fare düğmesi iletilerini işlemek için kod gösterir. Fare koordinat değeri isabet konumu değerinde bulunan `lParam` parametresi.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Win32 iletilerini işleme  
 Aşağıdaki örnek kodda isabet sınaması ana bilgisayarda yer alan visual nesne hiyerarşisini karşı nasıl gerçekleştirildiğini gösterir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi. Bir noktayı kullanarak görsel bir nesnenin geometrisini içinde olup olmadığını belirleyebilir <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> kök görsel nesnesi ve isabet sınaması için koordinat değeri belirtmek için yöntemi. Bu durumda, kök görsel nesne değeri <xref:System.Windows.Interop.HwndSource.RootVisual%2A> özelliği <xref:System.Windows.Interop.HwndSource> nesne.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 İsabet sınaması karşı görsel nesneler üzerinde daha fazla bilgi için bkz. [isabet testi görsel katmandaki](hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.HwndSource>
- [İsabet testi ile Win32 birlikte çalışabilirlik örneği](https://go.microsoft.com/fwlink/?LinkID=159995)
- [Görsel Katmanda Tıklama Testi](hit-testing-in-the-visual-layer.md)
