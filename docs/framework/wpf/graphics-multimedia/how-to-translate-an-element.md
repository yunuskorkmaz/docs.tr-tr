---
title: 'Nasıl yapılır: Bir Öğeyi Çevirme'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: 04e1e8288bcccc4a310f05abff01fbdf160cdb11
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505914"
---
# <a name="how-to-translate-an-element"></a>Nasıl yapılır: Bir Öğeyi Çevirme
Bu örnek nasıl çevrileceği (taşıma) kullanarak bir öğe gösterir bir <xref:System.Windows.Media.TranslateTransform>.  
  
 <xref:System.Windows.Media.TranslateTransform> Sınıfı, konumlandırmayı mutlak desteklemeyen bir panel içinde öğeleri taşımak için özellikle kullanışlıdır. Örneğin, uygulama tarafından bir <xref:System.Windows.Media.TranslateTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> özellik öğesinin içindeki bir öğeye taşıyabilirsiniz bir <xref:System.Windows.Controls.StackPanel> veya <xref:System.Windows.Controls.DockPanel>.  
  
 Kullanım <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği <xref:System.Windows.Media.TranslateTransform> miktarını piksel cinsinden öğe x ekseni boyunca taşımak için belirtmek için. Kullanım <xref:System.Windows.Media.TranslateTransform.Y%2A> özelliği miktarını piksel cinsinden öğe ve y ekseni boyunca taşımak için belirtin. Son olarak, uygulama <xref:System.Windows.Media.TranslateTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> öğesinin özelliği.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.TranslateTransform> öğesi 50 piksel doğru ve 50 piksel olarak aşağı taşımak için.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 Tam bir örnek için bkz. [2B dönüşüm örnek](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dönüşümlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
