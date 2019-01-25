---
title: 'Nasıl yapılır: Öğeye bir Donatıcı Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: 91dd047e65af8791f8e558a9a3b622ef05e2cb77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606328"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>Nasıl yapılır: Öğeye bir Donatıcı Bağlama
Bu örnekte, program aracılığıyla belirtilen bir öğeye bir donatıcı bağlama işlemi gösterilmektedir <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Örnek  
 Belirli bir öğeye bir donatıcı bağlama için <xref:System.Windows.UIElement>, şu adımları izleyin:  
  
1.  Çağrı `static` yöntemi <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> almak için bir <xref:System.Windows.Documents.AdornerLayer> nesnesi <xref:System.Windows.UIElement> donatılmış için. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> Belirtilen adreste başlayan görsel ağaç'kurmak gezer **UIElement**ve bulduğu ilk donatıcı katmanı döndürür. (Hiçbir donatıcı katman bulunursa, yöntem null değeri döndürür.)  
  
2.  Çağrı <xref:System.Windows.Documents.AdornerLayer.Add%2A> donatıcıyı hedefe bağlamak için yöntemi **UIElement**.  
  
 Aşağıdaki örnekte (yukarıda gösterilen) SimpleCircleAdorner bağlayan bir <xref:System.Windows.Controls.TextBox> adlı *myTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  Kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] başka bir öğeye bir donatıcı bağlamak için şu anda desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Donatıcılara Genel Bakış](../../../../docs/framework/wpf/controls/adorners-overview.md)
