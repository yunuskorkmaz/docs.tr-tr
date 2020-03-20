---
title: 'Nasıl yapılır: Anahatları Belirlenmiş Metin Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
ms.openlocfilehash: d0ce46b9895589fd4635b567136204368a6431ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186867"
---
# <a name="how-to-create-outlined-text"></a>Nasıl yapılır: Anahatları Belirlenmiş Metin Oluşturma
Çoğu durumda, uygulamanızdaki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin dizelerine süsleme eklerken, metni ayrı karakterler veya glifler koleksiyonu açısından kullanırsınız. Örneğin, doğrusal bir degrade fırça sıcabilir <xref:System.Windows.Controls.Control.Foreground%2A> ve <xref:System.Windows.Controls.TextBox> bunu bir nesnenin özelliğine uygulayabilirsiniz. Metin kutusunu görüntülediğinizde veya yaptığınızda, doğrusal degrade fırçası metin dizesindeki geçerli karakter kümesine otomatik olarak uygulanır.  
  
 ![Doğrusal degrade fırçasıyla görüntülenen metin](./media/how-to-create-outlined-text/text-linear-gradient.jpg)
  
 Ancak, görsel açıdan zengin <xref:System.Windows.Media.Geometry> başka metin türleri oluşturmanıza olanak tanıyan metni nesnelere dönüştürebilirsiniz. Örneğin, bir metin <xref:System.Windows.Media.Geometry> dizesinin anahatlarını temel alan bir nesne oluşturabilirsiniz.  
  
 ![Doğrusal degrade fırçası kullanarak metin anahattı](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 Metin bir <xref:System.Windows.Media.Geometry> nesneye dönüştürüldüğünde, artık bir karakter topluluğu değildir—metin dizesindeki karakterleri değiştiremezsiniz. Ancak, kontur ve dolgu özelliklerini değiştirerek dönüştürülen metnin görünümünü etkileyebilirsiniz. Kontur, dönüştürülen metnin anahatlarını ifade eder; dolgu, dönüştürülen metnin anahat içindeki alanı ifade eder.  
  
 Aşağıdaki örnekler, dönüştürülen metnin konturunu ve dolgusunu değiştirerek görsel efekt oluşturmanın çeşitli yollarını göstermektedir.  
  
 ![Dolgu ve kontur için farklı renklere sahip metin](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![Kontura uygulanan görüntü fırçası ile metin](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 Dönüştürülen metnin sınırlayıcı kutusu dikdörtgenini veya vurgusunu değiştirmek de mümkündür. Aşağıdaki örnek, dönüştürülen metnin konturunu ve vurgusunu değiştirerek görsel efekt oluşturmanın bir yolunu göstermektedir.  
  
 ![Kontur ve vurgulamaya uygulanan görüntü fırçası ile metin](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a>Örnek  
 Metni bir <xref:System.Windows.Media.Geometry> nesneye dönüştürmenin anahtarı nesneyi <xref:System.Windows.Media.FormattedText> kullanmaktır. Bu nesneyi oluşturduktan sonra, <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> metni <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> nesnelere dönüştürmek <xref:System.Windows.Media.Geometry> için bu ve yöntemleri kullanabilirsiniz. İlk yöntem biçimlendirilmiş metnin geometrisini döndürür; ikinci yöntem biçimlendirilmiş metnin sınırlayıcı kutusunun geometrisini döndürür. Aşağıdaki kod örneği, bir <xref:System.Windows.Media.FormattedText> nesnenin nasıl oluşturulup biçimlendirilmiş metnin ve sınırlayıcı kutusunun geometrilerini nasıl alınca gösterilmektedir.  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 Alınan <xref:System.Windows.Media.Geometry> nesneleri görüntülemek için dönüştürülen metni görüntüleyen <xref:System.Windows.Media.DrawingContext> nesnenin erişimine erişmeniz gerekir. Bu kod örneklerinde, bu, kullanıcı tanımlı işleme destekleyen bir sınıftan türetilen bir özel denetim nesnesi oluşturarak yapılır.  
  
 Nesneleri <xref:System.Windows.Media.Geometry> özel denetimde görüntülemek için <xref:System.Windows.UIElement.OnRender%2A> yöntem için bir geçersiz kılma sağlayın. Geçersiz kılınan yöntem, <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> <xref:System.Windows.Media.Geometry> nesneleri çizmek için yöntemi kullanmalıdır.  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  Örnek özel kullanıcı denetim nesnesinin kaynağı için, Visual Basic [için C#](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) için OutlineTextControl.cs ve [OutlineTextControl.vb bölümüne](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb)bakın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirilmiş Metin Çizme](drawing-formatted-text.md)
