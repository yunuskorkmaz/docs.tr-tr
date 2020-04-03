---
title: 'Nasıl yapılır: Özel Açılan Pencerenin Konumunu Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: b48dedc044b418062642af5c5bb40afab78a3c97
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635743"
---
# <a name="how-to-specify-a-custom-popup-position"></a>Nasıl yapılır: Özel Açılan Pencerenin Konumunu Belirtme
Bu örnek, <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özellik . <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> Özellik <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>ayarlandığında, <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> temsilcinin tanımlı bir örneği çağırır. Bu temsilci, hedef alanın sol üst köşesine ve hedef alanın sol üst köşesine <xref:System.Windows.Controls.Primitives.Popup>göre görebilen olası noktalar kümesini döndürür. Yerleşim, <xref:System.Windows.Controls.Primitives.Popup> en iyi görünürlüğü sağlayan noktada gerçekleşir.  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliği . <xref:System.Windows.Controls.Primitives.PlacementMode.Custom> Ayrıca, <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> <xref:System.Windows.Controls.Primitives.Popup>bir temsilciyi konumlandırmak için nasıl oluşturulup atanın caiz olduğunu da gösterir.  Geri arama temsilcisi <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> iki nesne döndürür.  <xref:System.Windows.Controls.Primitives.Popup> İlk konumda bir ekran kenarı tarafından <xref:System.Windows.Controls.Primitives.Popup> gizlenmişse, ikinci konuma yerleştirilir.  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 Tam örnek için [Popup Yerleştirme Örneği'ne](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Primitives.Popup>
- [Pop-up'a genel bakış](popup-overview.md)
- [Nasıl dır makaleleri](popup-how-to-topics.md)
