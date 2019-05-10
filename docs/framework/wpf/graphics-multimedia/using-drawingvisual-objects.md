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
ms.openlocfilehash: a0ce66e8956c8d7f1da1152f193f651ed1a54e3b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623561"
---
# <a name="using-drawingvisual-objects"></a>DrawingVisual Nesnelerini Kullanma
Bu konu nasıl kullanılacağına ilişkin bir genel bakış sağlar <xref:System.Windows.Media.DrawingVisual> nesneler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görsel katman.  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a>DrawingVisual nesnesi  
 <xref:System.Windows.Media.DrawingVisual> Olan şekil, görüntü veya metin işlemek için kullanılan sınıf çizim basit. Bu sınıf, performansını artırır, düzen veya olay işleme sağlamadığı basit olarak değerlendirilir. Bu nedenle, çizimleri, arka plan ve küçük resim için idealdir.  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a>DrawingVisual Konak Kapsayıcısı  
 Kullanmak için <xref:System.Windows.Media.DrawingVisual> nesneler, nesneler için bir konak kapsayıcısı oluşturmanız gerekir. Konak kapsayıcı nesnesi öğesinden türetilmelidir <xref:System.Windows.FrameworkElement> düzeni ve olay işleme desteği sağlar sınıfını <xref:System.Windows.Media.DrawingVisual> oturumda sınıfı. Ana amacı alt nesneleri içerecek şekilde olduğundan, konak kapsayıcı nesnesi herhangi bir görünür özelliği görüntülemez. Ancak, <xref:System.Windows.UIElement.Visibility%2A> konak kapsayıcısı özelliği ayarlanmalıdır <xref:System.Windows.Visibility.Visible>; Aksi takdirde, alt öğelerinden hiçbiri görünür olur.  
  
 Görsel nesneler için bir konak kapsayıcı nesnesi oluşturduğunuzda, görsel nesne başvurularını depolamak gereken bir <xref:System.Windows.Media.VisualCollection>. Kullanım <xref:System.Windows.Media.VisualCollection.Add%2A> konak kapsayıcıya görsel bir nesne eklemek için yöntemi. Aşağıdaki örnekte, bir konak kapsayıcı nesnesi oluşturulur ve üç görsel nesneler eklenir, <xref:System.Windows.Media.VisualCollection>.  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  Kendisinden önceki kod örneğinde çıkarılan tam kod örneği için bkz [isabet sınaması örneği kullanarak Test isabet](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a>DrawingVisual nesneleri oluşturma  
 Oluştururken bir <xref:System.Windows.Media.DrawingVisual> nesnesi çizim içerik yok. Nesnenin alarak metin, grafik veya görüntü içeriğini ekleyebilirsiniz <xref:System.Windows.Media.DrawingContext> ve içine çizim. A <xref:System.Windows.Media.DrawingContext> çağırarak döndürülen <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> yöntemi bir <xref:System.Windows.Media.DrawingVisual> nesne.  
  
 Bir dikdörtgen çizmek için <xref:System.Windows.Media.DrawingContext>, kullanın <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> yöntemi <xref:System.Windows.Media.DrawingContext> nesne. Diğer içerik türlerine çizmek için benzer yöntemler vardır. İşiniz bittiğinde çizim içeriğinize <xref:System.Windows.Media.DrawingContext>, çağrı <xref:System.Windows.Media.DrawingContext.Close%2A> kapatmak için yöntemi <xref:System.Windows.Media.DrawingContext> ve içeriği.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.DrawingVisual> nesnesi oluşturulur ve bir dikdörtgen çizilir kendi <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a>FrameworkElement üyeleri için geçersiz kılmaları oluşturma  
 Konak kapsayıcı nesnesi, görsel nesneler koleksiyonunu yönetmekten sorumludur. Bu konak kapsayıcısı için türetilen üye geçersiz kılmaları uygulamak gerektirir <xref:System.Windows.FrameworkElement> sınıfı.  
  
 Aşağıdaki listede iki üyeleri geçersiz kılmanız gerekir açıklanmaktadır:  
  
- <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Belirtilen dizindeki bir alt alt öğelerinin koleksiyonunu döndürür.  
  
- <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Bu öğe içindeki görsel alt öğe sayısını alır.  
  
 Aşağıdaki örnekte, iki için geçersiz kılmalar <xref:System.Windows.FrameworkElement> üyeleri uygulanır.  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a>İsabet testi desteği sağlama  
 Görünür bir özellik görüntülemez bile olay işleme konak kapsayıcı nesnesi sağlayabilir; ancak, kendi <xref:System.Windows.UIElement.Visibility%2A> özelliği ayarlanmalıdır <xref:System.Windows.Visibility.Visible>. Bu işleme yordamı farenin sol düğmesine sürümü gibi fare olayları yakalayabilir konak kapsayıcısı için bir olay oluşturmanıza olanak sağlar. İsabet sınaması çağırarak olay işleme yordamı uygulayabilirsiniz <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi. Yöntemin <xref:System.Windows.Media.HitTestResultCallback> parametresi bir isabet sınaması sonuç eylemini belirlemek için kullanabileceğiniz kullanıcı tanımlı bir yordam gösterir.  
  
 Aşağıdaki örnekte, isabet sınaması destek konak kapsayıcı nesnesi ve alt öğeleri için uygulanır.  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [WPF Grafik İşlemeye Genel Bakış](wpf-graphics-rendering-overview.md)
- [Görsel Katmanda Tıklama Testi](hit-testing-in-the-visual-layer.md)
