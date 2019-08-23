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
ms.openlocfilehash: 4e6fc89b64f7b0acc1a0077708d567eb97e2868e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962839"
---
# <a name="using-drawingvisual-objects"></a>DrawingVisual Nesnelerini Kullanma
Bu konu, <xref:System.Windows.Media.DrawingVisual> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görsel katmandaki nesnelerin nasıl kullanılacağına ilişkin bir genel bakış sağlar.  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a>DrawingVisual nesnesi  
 , <xref:System.Windows.Media.DrawingVisual> Şekilleri, resimleri veya metinleri işlemek için kullanılan basit bir çizim sınıfıdır. Bu sınıf, performansı artıran düzen veya olay işleme sağlamadığından hafif olarak değerlendirilir. Bu nedenle, çizimler arka planlar ve küçük resim için idealdir.  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a>DrawingVisual ana bilgisayar kapsayıcısı  
 Nesneleri kullanmak <xref:System.Windows.Media.DrawingVisual> için, nesneler için bir konak kapsayıcısı oluşturmanız gerekir. Konak kapsayıcı nesnesi, <xref:System.Windows.FrameworkElement> <xref:System.Windows.Media.DrawingVisual> sınıfın eksik olduğu düzen ve olay işleme desteğini sağlayan sınıfından türetilmelidir. Ana amacı alt nesneler içermesi gerektiğinden, konak kapsayıcı nesnesi hiçbir görünür özelliği görüntülemez. Ancak, <xref:System.Windows.UIElement.Visibility%2A> konak kapsayıcısının özelliği olarak <xref:System.Windows.Visibility.Visible>ayarlanmalıdır; Aksi takdirde, alt öğelerinden hiçbiri görünür olmayacaktır.  
  
 Görsel nesneler için bir konak kapsayıcı nesnesi oluşturduğunuzda, görsel nesne başvurularını bir <xref:System.Windows.Media.VisualCollection>olarak depolamanız gerekir. Bir görsel nesneyi konak kapsayıcısına eklemek için yönteminikullanın.<xref:System.Windows.Media.VisualCollection.Add%2A> Aşağıdaki örnekte, bir konak kapsayıcı nesnesi oluşturulur ve içine üç görsel nesne eklenir <xref:System.Windows.Media.VisualCollection>.  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
> Yukarıdaki kod örneğinin ayıklandığı bütün kod örneği için bkz. [Drawinggörselleri kullanarak Isabet testi örneği](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a>DrawingVisual nesneleri oluşturma  
 Bir <xref:System.Windows.Media.DrawingVisual> nesne oluşturduğunuzda, Çizim içeriğine sahip değildir. Nesne öğesini alarak <xref:System.Windows.Media.DrawingContext> ve içine çizerek metin, grafik veya resim içeriği ekleyebilirsiniz. <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> Bir <xref:System.Windows.Media.DrawingContext> nesnesinin<xref:System.Windows.Media.DrawingVisual> yöntemi çağırarak döndürülür.  
  
 İçine <xref:System.Windows.Media.DrawingContext>bir dikdörtgen çizmek için <xref:System.Windows.Media.DrawingContext> nesnesinin <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> yöntemini kullanın. Diğer içerik türlerini çizmek için benzer yöntemler vardır. İçine <xref:System.Windows.Media.DrawingContext>içerik çizmeyi bitirdiğinizde, ' yi kapatıp <xref:System.Windows.Media.DrawingContext> içeriği kalıcı hale <xref:System.Windows.Media.DrawingContext.Close%2A> getirmek için yöntemini çağırın.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.DrawingVisual> nesne oluşturulur ve <xref:System.Windows.Media.DrawingContext>içine bir dikdörtgen çizilir.  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a>FrameworkElement üyeleri için geçersiz kılmalar oluşturma  
 Konak kapsayıcı nesnesi, kendi görsel nesne koleksiyonunu yönetmekten sorumludur. Bu, konak kapsayıcısının türetilmiş <xref:System.Windows.FrameworkElement> sınıf için üye geçersiz kılmalarını uygulamasını gerektirir.  
  
 Aşağıdaki listede, geçersiz kılmanız gereken iki üye açıklanmaktadır:  
  
- <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Alt öğeler koleksiyonundan belirtilen dizinde bir alt öğe döndürür.  
  
- <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Bu öğe içindeki görsel alt öğe öğelerinin sayısını alır.  
  
 Aşağıdaki örnekte, iki <xref:System.Windows.FrameworkElement> üye için geçersiz kılmalar uygulanır.  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a>Isabet testi desteği sağlama  
 Konak kapsayıcı nesnesi herhangi bir görünür özellik görüntülemeseler bile olay işleme sağlayabilir, <xref:System.Windows.UIElement.Visibility%2A> ancak özelliği olarak <xref:System.Windows.Visibility.Visible>ayarlanmalıdır. Bu, sol fare düğmesinin yayını gibi fare olaylarını yakalayabileceğiniz ana bilgisayar kapsayıcısı için bir olay işleme yordamı oluşturmanızı sağlar. Olay işleme yordamı daha sonra <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemini çağırarak isabet sınamasını uygulayabilir. Yöntemin <xref:System.Windows.Media.HitTestResultCallback> parametresi, bir isabet testinin sonuç eylemini belirlemede kullanabileceğiniz Kullanıcı tanımlı bir yordama başvurur.  
  
 Aşağıdaki örnekte, ana bilgisayar kapsayıcısı nesnesi ve alt öğeleri için isabet testi desteği uygulanır.  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [WPF Grafik İşlemeye Genel Bakış](wpf-graphics-rendering-overview.md)
- [Görsel Katmanda Tıklama Testi](hit-testing-in-the-visual-layer.md)
