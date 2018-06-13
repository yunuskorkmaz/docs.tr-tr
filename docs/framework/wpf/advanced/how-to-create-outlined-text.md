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
ms.openlocfilehash: c79f5c1c6812b1175119133664e39995af29bd4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544971"
---
# <a name="how-to-create-outlined-text"></a>Nasıl yapılır: Anahatları Belirlenmiş Metin Oluşturma
Çoğu durumda, metin dizelerini için eklediğiniz zaman, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulama, kullanmakta olduğunuz farklı karakter ya da karakterlerin koleksiyonu bakımından metin. Örneğin, doğrusal gradyan fırçası oluşturabilir ve uygulayan <xref:System.Windows.Controls.Control.Foreground%2A> özelliği bir <xref:System.Windows.Controls.TextBox> nesnesi. Görüntüleme veya düzenleme metin kutusu, doğrusal gradyan fırçası metin dizesindeki karakterlerin geçerli kümesini otomatik olarak uygulanır.  
  
 ![Doğrusal gradyan fırçası ile görüntülenen metin](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")  
Bir metin kutusuna uygulanan doğrusal gradyan fırçası örneği  
  
 Ancak, aynı zamanda metne dönüştürebilirsiniz <xref:System.Windows.Media.Geometry> nesneleri, sizin görsel olarak zengin metin diğer türleri oluşturmanıza izin verir. Örneğin, oluşturabilirsiniz bir <xref:System.Windows.Media.Geometry> nesne tabanlı bir metin dizesinin anahattına.  
  
 ![Doğrusal gradyan fırçası kullanarak metin anahattı](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
Metin anahat geometriye uygulanan doğrusal gradyan fırçası örneği  
  
 Ne zaman metin dönüştürülür için bir <xref:System.Windows.Media.Geometry> nesne olduğu artık karakterler koleksiyonu — metin dizesindeki karakterleri değiştiremezsiniz. Ancak, vuruş ve dolgu özelliklerini değiştirerek Dönüştürülen metin görünümünü etkileyebilir. Vuruşun Dönüştürülen metin anahattına gösterir; Dolgu alanının içini Dönüştürülen metin anahat ifade eder.  
  
 Aşağıdaki örneklerde vuruş ve dönüştürülen metin dolgusunu değiştirerek görsel efektler oluşturmanın birkaç yolu gösterilmektedir.  
  
 ![Doldurma ve vuruş yapmak için farklı renkler metinle](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
Farklı renk vuruş ve dolgu ayarlama örneği  
  
 ![Görüntü fırça uygulandığı metinle](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
Uygulandığı bir resim fırçası örneği  
  
 Sınırlama kutusu dikdörtgen veya dönüştürülen metni vurgulama değiştirmek mümkündür. Aşağıdaki örnek, vuruş ve dönüştürülen metin Vurgusu değiştirerek görsel efektler oluşturmanın bir şekilde gösterilmektedir.  
  
 ![Görüntü fırça uygulandığı metinle](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
Vuruş ve vurgulamaya uygulanan resim fırçası örneği  
  
## <a name="example"></a>Örnek  
 Metne dönüştürme anahtarını bir <xref:System.Windows.Media.Geometry> nesnesi kullanmaktır <xref:System.Windows.Media.FormattedText> nesnesi. Bu nesne oluşturduktan sonra kullanabileceğiniz <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> ve <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> metne dönüştürmek için yöntemleri <xref:System.Windows.Media.Geometry> nesneleri. İlk yöntem geometri biçimlendirilmiş metin döndürür; İkinci yöntem, geometri biçimlendirilmiş metin kutusu sınırlayıcı döndürür. Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir bir <xref:System.Windows.Media.FormattedText> nesne ve biçimlendirilmiş metin ve kendi sınırlama kutusu geometri alınamadı.  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 Alınan görüntülemek için <xref:System.Windows.Media.Geometry> nesneleri erişmek gereken <xref:System.Windows.Media.DrawingContext> Dönüştürülen metin görüntüleme nesnesi. Bu kod örneklerinde, kullanıcı tanımlı işlemeyi destekleyen bir sınıfından türetilen özel bir denetim nesnesi oluşturarak yapılır.  
  
 Görüntülenecek <xref:System.Windows.Media.Geometry> özel denetim nesneleri sağlamak için bir geçersiz kılma <xref:System.Windows.UIElement.OnRender%2A> yöntemi. Geçersiz kılınan yönteminizi kullanması gereken <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> çizmek için yöntemi <xref:System.Windows.Media.Geometry> nesneleri.  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Biçimlendirilmiş Metin Çizme](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
