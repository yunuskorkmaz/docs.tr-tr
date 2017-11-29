---
title: "Nasıl yapılır: Görüntüsü Bulunan bir Düğme Oluşturma"
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
helpviewer_keywords: Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fa3aa5454629d53fd8864df6a4f204e22028208f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-button-that-has-an-image"></a>Nasıl yapılır: Görüntüsü Bulunan bir Düğme Oluşturma
Bu örnek, bir resim eklemek gösterilmiştir bir <xref:System.Windows.Controls.Button>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte iki oluşturur <xref:System.Windows.Controls.Button> kontrol eder. Bir <xref:System.Windows.Controls.Button> metni içeren ve diğeri bir görüntü içerir. Örneğin proje klasörün bir alt veri adlı bir klasöre görüntüdür. Bir kullanıcı tıkladığında <xref:System.Windows.Controls.Button> görüntü, arka plan ve diğer metin olan <xref:System.Windows.Controls.Button> değiştirin.  
  
 Bu örnekte <xref:System.Windows.Controls.Button> denetleyen biçimlendirme kullanarak ancak kod yazmak için kullandığı <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicileri.  
  
 [!code-xaml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetimleri](../../../../docs/framework/wpf/controls/index.md)  
 [Denetim Kitaplığı](../../../../docs/framework/wpf/controls/control-library.md)
