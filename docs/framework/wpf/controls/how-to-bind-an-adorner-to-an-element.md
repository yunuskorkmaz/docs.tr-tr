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
ms.openlocfilehash: e8c7eb929042bfe1455bfc9bf459fc466de5c397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923490"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>Nasıl yapılır: Öğeye bir Donatıcı Bağlama
Bu örnekte, bir donatıcının programlı olarak belirtilen <xref:System.Windows.UIElement>bir şekilde nasıl bağlanacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Bir donatıcıyı belirli <xref:System.Windows.UIElement>bir nesneye bağlamak için şu adımları izleyin:  
  
1. ' Nin donatılacak bir <xref:System.Windows.Documents.AdornerLayer> nesne <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> <xref:System.Windows.UIElement> almak için yönteminiçağırın.`static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>görsel ağacı, belirtilen **UIElement**'den başlayıp, bulduğu ilk donatıcı katmanını geri döndürür. (Bir donatıcı katmanı bulunmazsa, yöntem null döndürür.)  
  
2. Donatıcıyı hedef **UIElement**'e bağlamak için yönteminiçağırın.<xref:System.Windows.Documents.AdornerLayer.Add%2A>  
  
 Aşağıdaki örnek, bir SimpleCircleAdorner 'ı (yukarıda gösterilen) adlandırılmış bir <xref:System.Windows.Controls.TextBox> *myTextBox*öğesine bağlar.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
> Bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] donatıcıyı başka bir öğeye bağlamak için kullanılması şu anda desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Donatıcılara Genel Bakış](adorners-overview.md)
