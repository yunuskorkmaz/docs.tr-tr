---
title: 'Nasıl yapılır: Özel Açılan Pencerenin Konumunu Belirtin'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: 2ffba3d1a0fee236f803dd5877d541084192418b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358489"
---
# <a name="how-to-specify-a-custom-popup-position"></a>Nasıl yapılır: Özel Açılan Pencerenin Konumunu Belirtin
Bu örnek için özel bir konum belirtmek nasıl gösterir bir <xref:System.Windows.Controls.Primitives.Popup> denetimi <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliği <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.  
  
## <a name="example"></a>Örnek  
 Zaman <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliği <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, <xref:System.Windows.Controls.Primitives.Popup> tanımlanmış bir örneğini çağırır <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> temsilci. Bu temsilci hedef alanın sol üst ve sol üst köşesine göre olan olası noktaları kümesini döndürür <xref:System.Windows.Controls.Primitives.Popup>. <xref:System.Windows.Controls.Primitives.Popup> Yerleştirme en iyi görünürlük sağlayan bir noktada gerçekleşir.  
  
 Aşağıdaki örnek, konumunu tanımlamak gösterilmiştir bir <xref:System.Windows.Controls.Primitives.Popup> ayarlayarak <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğini <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Ayrıca nasıl oluşturulup atanacağını gösterir bir <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> konumlandırmak için temsilci <xref:System.Windows.Controls.Primitives.Popup>.  İki geri çağırma temsilcisini döndürür <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> nesneleri.  Varsa <xref:System.Windows.Controls.Primitives.Popup> ilk konumunda bir ekranın kenarı tarafından gizleniyor <xref:System.Windows.Controls.Primitives.Popup> ikinci konumuna yerleştirilir.  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 Tam bir örnek için bkz. [açılan pencere yerleştirme örnek](https://go.microsoft.com/fwlink/?LinkID=160032).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.Primitives.Popup>
- [Açılan Pencereye Genel Bakış](popup-overview.md)
- [Nasıl Yapılır Konuları](popup-how-to-topics.md)
