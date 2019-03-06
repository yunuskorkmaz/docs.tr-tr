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
ms.openlocfilehash: 409981e9c751144d26151210977a45b5e1eccf0a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368157"
---
# <a name="how-to-create-outlined-text"></a>Nasıl yapılır: Anahatları Belirlenmiş Metin Oluşturma
Çoğu durumda, metin dizelerini için eklediğiniz zaman, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulama, kullanmakta olduğunuz farklı karakter veya karakterler koleksiyonu açısından metin. Örneğin, doğrusal gradyan fırçası oluşturmak ve uygulamak <xref:System.Windows.Controls.Control.Foreground%2A> özelliği bir <xref:System.Windows.Controls.TextBox> nesne. Görüntüleme veya düzenleme metin kutusu, doğrusal gradyan fırçası geçerli bir metin dizesindeki bir karakter kümesini otomatik olarak uygulanır.  
  
 ![Doğrusal gradyan fırçası ile bir metin](./media/outlinedtext01.jpg "OutlinedText01")  
Doğrusal gradyan fırçası uygulanan bir metin kutusu örneği  
  
 Ancak, aynı zamanda metne dönüştürebilirsiniz <xref:System.Windows.Media.Geometry> diğer türde bir görsel olarak zengin metin oluşturmanızı sağlayan nesneler. Örneğin, aşağıdakileri oluşturabilirsiniz bir <xref:System.Windows.Media.Geometry> nesne tabanlı bir metin dizesinin çerçevesinde.  
  
 ![Doğrusal gradyan fırçası kullanma metin anahat](./media/outlinedtext02.jpg "OutlinedText02")  
Örnek metin ana hat geometrisi için uygulanan doğrusal gradyan fırça  
  
 Ne zaman metin dönüştürülür bir <xref:System.Windows.Media.Geometry> nesnesi, artık bir derlemesidir karakter — metin dizesindeki karakterlerin değiştiremezsiniz. Ancak, çizme ve İşaretleme dolgu özelliklerini değiştirerek Dönüştürülen metin görünümünü etkileyebilir. Fırça darbesi Dönüştürülen metin anahattına gösterir. Dolgu Dönüştürülen metin özetini içindeki alan ifade eder.  
  
 Aşağıdaki örnekler, görsel efektler vuruş ve dönüştürülen metin dolgu değiştirerek oluşturmanın birkaç yolu gösterilmektedir.  
  
 ![Metin doldurup için farklı renklerde](./media/outlinedtext03.jpg "OutlinedText03")  
Fırça darbesi ve dolgu farklı renkleri ayarlama örneği  
  
 ![Resim fırçası uygulandığı metinle](./media/outlinedtext04.jpg "OutlinedText04")  
Bir resim fırçası uygulandığı örneği  
  
 Sınırlayıcı kutusunun dikdörtgen veya vurgulama, dönüştürülen metin değiştirmek mümkündür. Aşağıdaki örnek, dönüştürülen metin vurgulama ve vuruş değiştirerek görsel efektler oluşturmanın bir yolu gösterir.  
  
 ![Resim fırçası uygulandığı metinle](./media/outlinedtext05.jpg "OutlinedText05")  
Fırça darbesi ve vurgulamaya uygulanan bir resim fırçası örneği  
  
## <a name="example"></a>Örnek  
 Metin dönüştürmenin anahtarı bir <xref:System.Windows.Media.Geometry> kullanılacak nesnedir <xref:System.Windows.Media.FormattedText> nesne. Bu nesne oluşturulduktan sonra kullanabileceğiniz <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> ve <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> metne dönüştürme yöntemleri <xref:System.Windows.Media.Geometry> nesneleri. İlk yöntem, geometri biçimlendirilmiş metin döndürür; İkinci yöntem, biçimlendirilmiş metnin geometrisini sınırlayıcı kutusunun döndürür. Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Media.FormattedText> nesne ve biçimlendirilmiş metnin ve sınırlayıcı kutusunun geometriler alınacak.  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 Alınan görüntülemek için <xref:System.Windows.Media.Geometry> nesnelerini erişmek için gereksinim duyduğunuz <xref:System.Windows.Media.DrawingContext> Dönüştürülen metin görüntüleme nesnesi. Bu kod örnekleri, bu kullanıcı tanımlı işlemeyi destekleyen bir sınıftan türetilmiş bir özel denetim nesnesi oluşturarak yapılır.  
  
 Görüntülenecek <xref:System.Windows.Media.Geometry> özel denetimindeki nesnelere sağlamak için bir geçersiz kılma <xref:System.Windows.UIElement.OnRender%2A> yöntemi. Geçersiz kılınan yönteminizi kullanması gereken <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> çizmek için yöntemi <xref:System.Windows.Media.Geometry> nesneleri.  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  Örnek özel kullanıcı denetimi nesnesinin kaynağını görmek [için OutlineTextControl.cs C# ](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) ve [Visual Basic için OutlineTextControl.vb](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb). 
  
## <a name="see-also"></a>Ayrıca bkz.
- [Biçimlendirilmiş Metin Çizme](drawing-formatted-text.md)
