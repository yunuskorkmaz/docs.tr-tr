---
title: "Nasıl yapılır: Kılavuz Kullanarak Standart UI İletişim Kutusu Oluşturma"
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
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69dba9b76f823e1779c4555521552b4a423c844c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a>Nasıl yapılır: Kılavuz Kullanarak Standart UI İletişim Kutusu Oluşturma
Bu örnek, bir standart oluşturmaya gösterilmiştir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] iletişim kutusunu kullanarak <xref:System.Windows.Controls.Grid> öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek gibi bir iletişim kutusu oluşturur **çalıştırmak** iletişim kutusunda [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] işletim sistemi.  
  
 Örnekte bir <xref:System.Windows.Controls.Grid> ve kullandığı <xref:System.Windows.Controls.ColumnDefinition> ve <xref:System.Windows.Controls.RowDefinition> beş sütun ve dört satır tanımlamak için sınıflar.  
  
 Örnek sonra ekler ve konumlandırır bir <xref:System.Windows.Controls.Image>, `RunIcon.png`, iletişim kutusunda bulunan resmi temsil edecek. Görüntünün ilk sütun ve satır yerleştirilir <xref:System.Windows.Controls.Grid> (sol üst köşesinde).  
  
 Ardından, örnek, bir <xref:System.Windows.Controls.TextBlock> ilk satırın kalan sütunlarını kapsayan ilk sütun öğesi. Başka bir ekler <xref:System.Windows.Controls.TextBlock> temsil etmek için ilk sütunun ikinci satırında öğesine **açık** metin kutusu. A <xref:System.Windows.Controls.TextBlock> aşağıdaki gibi veri giriş alanı temsil eder.  
  
 Son olarak, örnek üç ekler <xref:System.Windows.Controls.Button> temsil eden son satır öğelerine **Tamam**, **iptal**, ve **Gözat** olaylar.  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.GridUnitType>  
 [Panellere Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/grid-how-to-topics.md)
