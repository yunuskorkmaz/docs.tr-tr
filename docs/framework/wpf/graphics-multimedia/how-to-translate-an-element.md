---
title: "Nasıl yapılır: Bir Öğeyi Çevirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2f9b8363f0c3b9e0a9653dfc9864727c9460f695
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-translate-an-element"></a>Nasıl yapılır: Bir Öğeyi Çevirme
Bu örnek, kullanarak bir öğe (Taşı) çevirmek nasıl gösterir bir <xref:System.Windows.Media.TranslateTransform>.  
  
 <xref:System.Windows.Media.TranslateTransform> Sınıfı, mutlak konumlandırmayı desteklemeyen panolar içinde öğeleri taşımak için özellikle yararlıdır. Örneğin, uygulama tarafından bir <xref:System.Windows.Media.TranslateTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> özelliği, bir öğenin bir öğenin içine taşıyabilirsiniz bir <xref:System.Windows.Controls.StackPanel> veya <xref:System.Windows.Controls.DockPanel>.  
  
 Kullanım <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği <xref:System.Windows.Media.TranslateTransform> x ekseni boyunca öğe taşımak için piksel cinsinden miktarı belirtmek için. Kullanım <xref:System.Windows.Media.TranslateTransform.Y%2A> özelliği y ekseni boyunca öğe taşımak için piksel cinsinden miktarını belirtin. Son olarak, uygulama <xref:System.Windows.Media.TranslateTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> öğesi özelliği.  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.TranslateTransform> bir öğe 50 piksel sağ ve 50 piksel olarak aşağı taşımak için.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 Tam bir örnek için bkz: [2-D dönüşümler örnek](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dönüşümlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
