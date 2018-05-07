---
title: 'Nasıl yapılır: Özel Açılan Pencerenin Konumunu Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: 8714cfa4f7e5bb0ca157ee9d551392571303f60e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-a-custom-popup-position"></a>Nasıl yapılır: Özel Açılan Pencerenin Konumunu Belirtme
Bu örnek için özel bir konum belirtmek nasıl gösterir bir <xref:System.Windows.Controls.Primitives.Popup> denetimi <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliği ayarlanmış <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.  
  
## <a name="example"></a>Örnek  
 Zaman <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliği ayarlanmış <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, <xref:System.Windows.Controls.Primitives.Popup> tanımlanmış bir örneğini çağırır <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> temsilci. Bu temsilci hedef alanının sol üst ve sol üst köşesine göre olası noktalar kümesini döndürür <xref:System.Windows.Controls.Primitives.Popup>. <xref:System.Windows.Controls.Primitives.Popup> Yerleştirme en iyi görünürlük sağlayan bir noktada ortaya çıkar.  
  
 Aşağıdaki örnek konumunu tanımlamak nasıl gösterir bir <xref:System.Windows.Controls.Primitives.Popup> ayarlayarak <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğine <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Ayrıca oluşturmak ve atamak nasıl gösterir bir <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> konumlandırmak için temsilci <xref:System.Windows.Controls.Primitives.Popup>.  Geri çağırma temsilcisini iki döndürür <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> nesneleri.  Varsa <xref:System.Windows.Controls.Primitives.Popup> ilk konumunda ekran kenarı tarafından gizli <xref:System.Windows.Controls.Primitives.Popup> ikinci konumuna yerleştirilir.  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 Tam bir örnek için bkz: [açılan yerleştirme örnek](http://go.microsoft.com/fwlink/?LinkID=160032).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [Açılan Pencereye Genel Bakış](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
