---
title: "Nasıl yapılır: Windows Forms DataGridView Denetiminde Yeni Satırlar İçin Varsayılan Değerleri Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], default values for new rows
- DataGridView control [Windows Forms], data entry
- rows [Windows Forms], specifying default values
- DataGridView control [Windows Forms], default values for new rows
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 577d5c3bc4b4afef845cd51b62b7d48fcc9d4a7e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Yeni Satırlar İçin Varsayılan Değerleri Belirtme
Uygulama varsayılan değerleri yeni eklenen satırların doldurduğunda veri girişi daha kullanışlı hale getirebilir. İle <xref:System.Windows.Forms.DataGridView> sınıfı, doldurabilirsiniz varsayılan değerlerle <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> olay. Kullanıcı yeni kayıtlar için satır girdiğinde, bu olay tetiklenir. Kodunuzu bu olay işlediğinde, seçtiğiniz değerlerle istenen hücreleri doldurabilirsiniz.  
  
 Aşağıdaki kod örneği kullanarak yeni satırlar için varsayılan değerler belirtmek gösterilmiştir <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> olay.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   A `NewCustomerId` benzersiz oluşturmak için işlevi `CustomerID` değerleri.  
  
-   Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 [Veri girişi Windows Forms DataGridView denetimi](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView denetiminde yeni kayıtlar için satır kullanma](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
