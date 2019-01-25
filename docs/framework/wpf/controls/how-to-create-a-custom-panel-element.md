---
title: 'Nasıl yapılır: Özel Panel Öğesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: 93d9ebacda8c753ab5a4446999e1aa86828a2b9e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621938"
---
# <a name="how-to-create-a-custom-panel-element"></a>Nasıl yapılır: Özel Panel Öğesi Oluşturma
## <a name="example"></a>Örnek  
 Bu örnekte, varsayılan düzen davranışını geçersiz kılmak gösterilmektedir <xref:System.Windows.Controls.Panel> öğesi öğesinden türetilen özel düzen öğelerini oluşturup <xref:System.Windows.Controls.Panel>.  
  
 Örnek, basit bir özel tanımlar <xref:System.Windows.Controls.Panel> adlı öğesi `PlotPanel`, alt öğeleri göre iki sabit kodlanmış x ve y-koordinatlarına yerleştirir. Bu örnekte, `x` ve `y` hem ayarlamak `50`; bu nedenle, tüm alt öğeleri x ve y yerde konumlandırılır eksenleri.  
  
 Özel uygulamak için <xref:System.Windows.Controls.Panel> davranışları örnekte <xref:System.Windows.FrameworkElement.MeasureOverride%2A> ve <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> yöntemleri. Her yöntem döndürür <xref:System.Windows.Size> alt öğeleri konumlandırmak ve işlemek gerekli olan veriler.  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.Panel>
- [Panellere Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)
- [Özel içerik kaydırma paneli örneği oluşturma](https://go.microsoft.com/fwlink/?LinkID=159979)
