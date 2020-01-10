---
title: 'Nasıl yapılır: Win32 Konak Kapsayıcısı Kullanan Tıklama Testi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
ms.openlocfilehash: b71783f2d061c9139de4449d8e0106eb00345894
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740180"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a>Nasıl yapılır: Win32 Konak Kapsayıcısı Kullanan Tıklama Testi
Görsel nesneler için bir konak pencere kapsayıcısı sunarak, bir Win32 penceresi içinde görsel nesneler oluşturabilirsiniz. İçerilen görsel nesnelere olay işleme sağlamak için, ana bilgisayar pencere kapsayıcısının ileti filtresi döngüsüne geçirilen iletileri işleyin. Visual Objects 'i bir Win32 penceresinde barındırmak hakkında daha fazla bilgi için bkz. [öğretici: bir Win32 uygulamasında görsel nesneler barındırma](tutorial-hosting-visual-objects-in-a-win32-application.md) .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, görsel nesneler için konak kapsayıcısı olarak kullanılan bir Win32 penceresi için fare olay işleyicilerini ayarlamayı gösterir.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 Aşağıdaki örnekte, belirli fare olaylarını yakalamaya yönelik yanıt olarak bir isabet testinin nasıl ayarlanacağı gösterilmektedir.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <xref:System.Windows.Interop.HwndSource> nesnesi bir Win32 penceresi içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] içerik sunar. <xref:System.Windows.Interop.HwndSource> nesnesinin <xref:System.Windows.Interop.HwndSource.RootVisual%2A> özelliğinin değeri, görsel ağaç hiyerarşisindeki en üstteki düğümü temsil eder.  
  
 Bir Win32 konak kapsayıcısı kullanan isabet sınama nesnelerinde tüm örnek için bkz. Win32 birlikte [çalışabilirlik örneği Ile Isabet testi](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.HwndSource>
- [Görsel Katmanda Tıklama Testi](hit-testing-in-the-visual-layer.md)
- [Eğitmen: Win32 Uygulamasında Görsel Nesneler Barındırma](tutorial-hosting-visual-objects-in-a-win32-application.md)
