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
ms.openlocfilehash: 31edc75114c5dad613e5b65e7d8b051e2c3713af
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799138"
---
# <a name="how-to-create-a-custom-panel-element"></a>Nasıl yapılır: Özel Panel Öğesi Oluşturma
## <a name="example"></a>Örnek  
 Bu örnek, <xref:System.Windows.Controls.Panel> öğesinin varsayılan düzen davranışının nasıl geçersiz kılınacağını ve <xref:System.Windows.Controls.Panel>türetilen özel düzen öğelerinin nasıl oluşturulacağını gösterir.  
  
 Örnek, alt öğeleri iki sabit kodlanmış x ve y koordinatlarına göre konumlandırır `PlotPanel`adlı basit bir özel <xref:System.Windows.Controls.Panel> öğesi tanımlar. Bu örnekte, `x` ve `y` her ikisi de `50`olarak ayarlanmıştır; Bu nedenle, tüm alt öğeler x ve y eksenlerinde bu konumda konumlandırılır.  
  
 Özel <xref:System.Windows.Controls.Panel> davranışları uygulamak için, örnek <xref:System.Windows.FrameworkElement.MeasureOverride%2A> ve <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> yöntemlerini kullanır. Her yöntem alt öğeleri konumlandırmak ve işlemek için gereken <xref:System.Windows.Size> verileri döndürür.  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Panel>
- [Panellere Genel Bakış](panels-overview.md)
