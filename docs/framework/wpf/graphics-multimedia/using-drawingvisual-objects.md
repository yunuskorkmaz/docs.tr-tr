---
title: DrawingVisual Nesnelerini Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual layer [WPF], DrawingVisual objects
- DrawingVisual objects in visual layer [WPF]
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
ms.openlocfilehash: 9d67fbc0d9716c9df3935232c6c7e579b50d55bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148328"
---
# <a name="using-drawingvisual-objects"></a>DrawingVisual Nesnelerini Kullanma
Bu konu, görsel katmandaki <xref:System.Windows.Media.DrawingVisual> nesnelerin nasıl [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanılacağına genel bir bakış sağlar.  
  
<a name="drawingvisual_object"></a>
## <a name="drawingvisual-object"></a>ÇizimGörsel Nesne  
 Şekilleri, <xref:System.Windows.Media.DrawingVisual> görüntüleri veya metni işlemek için kullanılan hafif bir çizim sınıfıdır. Bu sınıf, performansını artıran düzen veya olay işleme sağlamadığından hafif olarak kabul edilir. Bu nedenle, çizimler arka planlar ve küçük resim için idealdir.  
  
<a name="drawingvisual_host_container"></a>
## <a name="drawingvisual-host-container"></a>ÇizimGörsel Host Konteyner  
 Nesneleri kullanmak <xref:System.Windows.Media.DrawingVisual> için, nesneler için bir ana bilgisayar kapsayıcıoluşturmanız gerekir. Ana bilgisayar kapsayıcı nesnesi, <xref:System.Windows.FrameworkElement> <xref:System.Windows.Media.DrawingVisual> sınıfın sahip olmadığı düzen ve olay işleme desteğini sağlayan sınıftan türemelidir. Ana amacı alt nesneleri içermek olduğundan, ana bilgisayar kapsayıcı nesnesi görünür özellikleri göstermez. Ancak, <xref:System.Windows.UIElement.Visibility%2A> ana kapsayıcının özelliği; <xref:System.Windows.Visibility.Visible> aksi takdirde, alt öğelerinin hiçbiri görünür olacaktır.  
  
 Görsel nesneler için bir ana kapsayıcı nesnesi oluşturduğunuzda, görsel <xref:System.Windows.Media.VisualCollection>nesne başvurularını bir . Ana <xref:System.Windows.Media.VisualCollection.Add%2A> bilgisayar kapsayıcısına görsel bir nesne eklemek için yöntemi kullanın. Aşağıdaki örnekte, bir ana kapsayıcı nesnesi oluşturulur ve üç <xref:System.Windows.Media.VisualCollection>görsel nesne onun .  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
> Önceki kod örneğinin ayıklandığı tam kod örneği için [bkz.](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual)  
  
<a name="creating_drawingvisual_objects"></a>
## <a name="creating-drawingvisual-objects"></a>Çizim Görsel Nesneler oluşturma  
 Bir <xref:System.Windows.Media.DrawingVisual> nesne oluşturduğunuzda, hiçbir çizim içeriği vardır. Nesnenin <xref:System.Windows.Media.DrawingContext> kini alıp içine çizerek metin, grafik veya resim içeriği ekleyebilirsiniz. A, <xref:System.Windows.Media.DrawingContext> nesnenin <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> <xref:System.Windows.Media.DrawingVisual> yöntemini çağırarak döndürülür.  
  
 Bir dikdörtgen çizmek <xref:System.Windows.Media.DrawingContext>için, nesnenin <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> yöntemini <xref:System.Windows.Media.DrawingContext> kullanın. Benzer yöntemler diğer içerik türlerini çizmek için de vardır. İçeriğin içine çizimi <xref:System.Windows.Media.DrawingContext>bittiğinde, <xref:System.Windows.Media.DrawingContext.Close%2A> içeriği kapatmak <xref:System.Windows.Media.DrawingContext> ve devam etmek için yöntemi arayın.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Media.DrawingVisual> bir nesne oluşturulur ve bir dikdörtgen onun <xref:System.Windows.Media.DrawingContext>içine çizilir.  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>
## <a name="creating-overrides-for-frameworkelement-members"></a>FrameworkElement Üyeleri için Geçersiz Kılmaoluşturma  
 Ana bilgisayar kapsayıcı nesnesi, görsel nesneler koleksiyonunu yönetmekten sorumludur. Bu, ana bilgisayar kapsayıcısı uygulaması üyesinin türemiş <xref:System.Windows.FrameworkElement> sınıf için geçersiz kılmasını gerektirir.  
  
 Aşağıdaki listede geçersiz kılmanız gereken iki üye açıklanmaktadır:  
  
- <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Alt öğelerin koleksiyonundan belirtilen indekste bir alt verir.  
  
- <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Bu öğe içindeki görsel alt öğelerin sayısını alır.  
  
 Aşağıdaki örnekte, iki <xref:System.Windows.FrameworkElement> üye için geçersiz kılmalar uygulanır.  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>
## <a name="providing-hit-testing-support"></a>Hit Test Desteği Sağlama  
 Ana bilgisayar kapsayıcı nesnesi, görünür özellikler görüntülemese bile <xref:System.Windows.UIElement.Visibility%2A> olay işleme sağlayabilir, ancak özelliği ' ne göre <xref:System.Windows.Visibility.Visible>ayarlanmalıdır. Bu, sol fare düğmesinin serbest bırakılması gibi fare olaylarını bindirmeye bilen ana bilgisayar kapsayıcısı için bir olay işleme yordamı oluşturmanıza olanak tanır. Olay işleme yordamı daha sonra <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi çağırarak isabet testi uygulayabilirsiniz. Yöntemin <xref:System.Windows.Media.HitTestResultCallback> parametresi, isabet testinin sonucunu belirlemek için kullanabileceğiniz kullanıcı tanımlı bir yordamanlamına gelir.  
  
 Aşağıdaki örnekte, ana bilgisayar kapsayıcı nesnesi ve altları için hit test desteği uygulanır.  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [WPF Grafik İşlemeye Genel Bakış](wpf-graphics-rendering-overview.md)
- [Görsel Katmanda Tıklama Testi](hit-testing-in-the-visual-layer.md)
