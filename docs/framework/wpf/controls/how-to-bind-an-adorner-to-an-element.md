---
title: "Nasıl yapılır: Öğeye bir Donatıcı Bağlama"
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
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2b1da3216ce6d3507c304ff957728d33ba1b9bd9
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>Nasıl yapılır: Öğeye bir Donatıcı Bağlama
Bu örnek bir donatıcıyı programlı olarak belirtilen bir bağlamak nasıl gösterir <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Örnek  
 Belirli bir donatıcı bağlamak için <xref:System.Windows.UIElement>, şu adımları izleyin:  
  
1.  Çağrı `static` yöntemi <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> almak için bir <xref:System.Windows.Documents.AdornerLayer> için nesne <xref:System.Windows.UIElement> donatılacak. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>Belirtilen başlangıç görsel ağaç anlatılmaktadır **UIElement**ve bulduğu ilk donatıcı katmanı döndürür. (Hiçbir donatıcı katman bulunamazsa, yöntem null değeri döndürür.)  
  
2.  Çağrı <xref:System.Windows.Documents.AdornerLayer.Add%2A> donatıcıyı hedef bağlamak için yöntemi **UIElement**.  
  
 Aşağıdaki örnekte (yukarıda gösterilen) SimpleCircleAdorner bağlanır bir <xref:System.Windows.Controls.TextBox> adlı *myTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  Kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] donatıcı başka bir öğeye bağlamak için şu anda desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Donatıcılar genel bakış](../../../../docs/framework/wpf/controls/adorners-overview.md)
