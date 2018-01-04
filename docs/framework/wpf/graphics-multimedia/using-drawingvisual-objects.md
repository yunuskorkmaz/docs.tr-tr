---
title: DrawingVisual Nesnelerini Kullanma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual layer [WPF], DrawingVisual objects
- DrawingVisual objects in visual layer [WPF]
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a33e56b69a357694a1d1a23d5cd3c887c88cea37
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-drawingvisual-objects"></a>DrawingVisual Nesnelerini Kullanma
Bu konu nasıl kullanılacağını bir bakış sunar <xref:System.Windows.Media.DrawingVisual> nesnelerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görsel katmanı.  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a>DrawingVisual nesnesi  
 <xref:System.Windows.Media.DrawingVisual> Olan şekil, görüntü veya metin işlemek için kullanılan sınıf çizim basit. Bu sınıf, kendi performansını artırır, düzen veya olay işleme sağlamadığından basit olarak değerlendirilir. Bu nedenle, çizimler arka planlar ve küçük resim için idealdir.  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a>DrawingVisual Konak Kapsayıcısı  
 Kullanmak için <xref:System.Windows.Media.DrawingVisual> nesneleri, bir konak kapsayıcı nesneleri oluşturmanız gerekir. Konak kapsayıcı nesnesi öğesinden türetilmelidir <xref:System.Windows.FrameworkElement> düzeni ve olay işleme desteği sağlayan sınıf <xref:System.Windows.Media.DrawingVisual> oturumda sınıfı. Ana amacı alt nesneleri içerecek şekilde olduğundan konak kapsayıcı nesnesi herhangi bir görünür özelliği görüntülemez. Ancak, <xref:System.Windows.UIElement.Visibility%2A> konak kapsayıcısının özelliği ayarlanmalıdır <xref:System.Windows.Visibility.Visible>; Aksi halde, alt öğelerin hiçbiri görünür olur.  
  
 Görsel nesneler için bir konak kapsayıcı nesnesi oluşturduğunuzda, görsel nesne başvurularını depolamak gereken bir <xref:System.Windows.Media.VisualCollection>. Kullanım <xref:System.Windows.Media.VisualCollection.Add%2A> konak kapsayıcısı için görsel bir nesne eklemek için yöntem. Aşağıdaki örnekte, bir konak kapsayıcı nesnesi oluşturulur ve üç görsel nesne eklenir, <xref:System.Windows.Media.VisualCollection>.  
  
 [!code-csharp[DrawingVisualSample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  Önceki kod örneğinde ayıklandığı tam kod örnek için bkz [Test kullanarak isabet sınaması örneği isabet](http://go.microsoft.com/fwlink/?LinkID=159994).  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a>DrawingVisual nesneleri oluşturma  
 Oluştururken bir <xref:System.Windows.Media.DrawingVisual> nesnesi çizim içerik yok. Nesnenin alarak metin, grafik veya görüntü içeriği ekleyebilirsiniz <xref:System.Windows.Media.DrawingContext> ve içine çizim. A <xref:System.Windows.Media.DrawingContext> çağrılarak döndürülür <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> yöntemi bir <xref:System.Windows.Media.DrawingVisual> nesnesi.  
  
 Bir dikdörtgen çizmek için <xref:System.Windows.Media.DrawingContext>, kullanın <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> yöntemi <xref:System.Windows.Media.DrawingContext> nesnesi. Diğer içerik türlerine çizim için benzer yöntemler mevcut. İşiniz bittiğinde içine içerik çizmeyi <xref:System.Windows.Media.DrawingContext>, çağrı <xref:System.Windows.Media.DrawingContext.Close%2A> kapatmak için yöntemi <xref:System.Windows.Media.DrawingContext> ve içeriği kalır.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.DrawingVisual> nesnesi oluşturulur ve bir dikdörtgen çizilir kendi <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[DrawingVisualSample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a>Geçersiz kılmaları FrameworkElement üyeler için oluşturma  
 Konak kapsayıcı nesnesi, kendi görsel nesneler koleksiyonunu yönetilmesinden sorumludur. Bu konak kapsayıcı üye türetilmiş için geçersiz kılmalarını uygulamasını gerektirir <xref:System.Windows.FrameworkElement> sınıfı.  
  
 Aşağıdaki listede iki üyeleri geçersiz kılmanız gerekir açıklanmaktadır:  
  
-   <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Belirtilen dizindeki bir alt koleksiyonda alt öğelerini döndürür.  
  
-   <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Bu öğe içindeki görsel alt öğe sayısını alır.  
  
 Aşağıdaki örnekte, iki için geçersiz kılar <xref:System.Windows.FrameworkElement> üyeleri uygulanır.  
  
 [!code-csharp[DrawingVisualSample#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a>İsabet testi desteği sağlama  
 Konak kapsayıcı nesnesi görünür bir özellik görüntülemez olsa bile olay işleme sağlayabilir; ancak, kendi <xref:System.Windows.UIElement.Visibility%2A> özelliği ayarlanmalıdır <xref:System.Windows.Visibility.Visible>. Bu işleme yordamı sol fare düğmesini sürümü gibi fare olayları yakalayabilir konak kapsayıcı için bir olay oluşturmanıza olanak sağlar. Olay işleme yordamı, ardından çağırarak isabet testi uygulayabilirsiniz <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi. Yöntemin <xref:System.Windows.Media.HitTestResultCallback> parametresi isabet testi sonuç eylemini belirlemek için kullanabileceğiniz kullanıcı tanımlı bir yordam gösterir.  
  
 Aşağıdaki örnekte, isabet sınama desteğini konak kapsayıcı nesnesi ve alt öğelerini için uygulanır.  
  
 [!code-csharp[DrawingVisualSample#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.DrawingVisual>  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>  
 [WPF Grafik İşlemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Görsel Katmanda Tıklama Testi](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
