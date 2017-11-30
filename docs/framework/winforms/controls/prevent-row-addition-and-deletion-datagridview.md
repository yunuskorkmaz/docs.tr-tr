---
title: "Nasıl yapılır: Windows Forms DataGridView Denetiminde Satır Ekleme ve Silmeyi Engelleme"
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
- DataGridView control [Windows Forms], disabling data entry
- data entry [Windows Forms], disabling in grids
- data grids [Windows Forms], disabling data entry
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e90e36ef8a74caf58f6454027971f0711c406d52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Satır Ekleme ve Silmeyi Engelleme
Bazı durumlarda, kullanıcıların yeni veri satırları girmek veya var olan satır silme önlemek isteyebilirsiniz, <xref:System.Windows.Forms.DataGridView> denetim. <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> Özelliği gösterir yeni kayıtlar için satır denetimi altındaki mevcut olup olmadığını while <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> özelliği, satır kaldırılıp kaldırılamayacağını belirtir. Aşağıdaki kod örneğinde bu özellikleri kullanır ve ayrıca ayarlar <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> özelliği salt okunur tamamen denetimi yapın.  
  
 Visual Studio'da bu görev için desteği yoktur.  Ayrıca bkz. [nasıl yapılır: satır ekleme önlemek ve Windows Forms DataGridView denetimi kullanarak Tasarımcı silinmesine](http://msdn.microsoft.com/library/k5c88sw3\(v=vs.110\)).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=nameWithType>  
 [Temel sütun, satır ve hücre özellikleri Windows Forms DataGridView denetiminde](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
