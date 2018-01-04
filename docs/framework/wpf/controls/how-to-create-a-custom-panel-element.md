---
title: "Nasıl yapılır: Özel Panel Öğesi Oluşturma"
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
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5eacc5435e259c20c25b64d6e82c33d07338602a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-panel-element"></a>Nasıl yapılır: Özel Panel Öğesi Oluşturma
## <a name="example"></a>Örnek  
 Bu örnek, varsayılan düzen davranışını geçersiz kılmak nasıl gösterir <xref:System.Windows.Controls.Panel> öğesi ve türetilmiş özel düzen öğelerinin <xref:System.Windows.Controls.Panel>.  
  
 Basit özel bir örnek tanımlar <xref:System.Windows.Controls.Panel> adlı öğe `PlotPanel`, alt öğeleri göre iki sabit kodlanmış x ve y-koordinatlarına yerleştirir. Bu örnekte, `x` ve `y` her ikisi de ayarlamak `50`; bu nedenle, tüm alt öğelerini x ve y yerde konumlandırılır eksenleri.  
  
 Özel uygulamak için <xref:System.Windows.Controls.Panel> davranışları, örnek kullanan <xref:System.Windows.FrameworkElement.MeasureOverride%2A> ve <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> yöntemleri. Her yöntem <xref:System.Windows.Size> getirin ve alt öğelerini işlemek gerekli olan veriler.  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Panel>  
 [Panellere Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Özel bir içerik kaydırma Panel örneği oluşturma](http://go.microsoft.com/fwlink/?LinkID=159979)
