---
title: "Nasıl yapılır: Windows Forms DataGridView Denetiminin Düzenleme Modunu Belirtme"
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
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 70bf241865eef3366444e1b4dc20c19adaff983e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminin Düzenleme Modunu Belirtme
Varsayılan olarak, kullanıcılar geçerli içeriğini düzenleyebilir <xref:System.Windows.Forms.DataGridView> metin kutusu hücresinin içine yazarak veya F2 tuşuna basın. Aşağıdaki koşulların tümü yerine getirilirse bu hücre düzenleme moduna girer:  
  
-   Veri kaynağındaki düzenlemeyi destekler.  
  
-   <xref:System.Windows.Forms.DataGridView> Denetim etkin.  
  
-   <xref:System.Windows.Forms.DataGridView.EditMode%2A> Özellik değeri değil <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.  
  
-   `ReadOnly` Hücre, satır, sütun ve denetim özellikleridir tüm kümesine `false`.  
  
 Düzenleme modunda kullanıcı hücrenin değerini değiştirin ve değişikliği veya özgün değeri hücreye geri dönmek için ESC yürütmek için ENTER tuşuna basın.  
  
 Yapılandırabileceğiniz bir <xref:System.Windows.Forms.DataGridView> geçerli hücreyi hale hemen bir hücre düzenleme moduna girer. böylece denetim. ENTER ve ESC anahtarları davranışını bu durumda değiştirilmez, ancak değeri yürütülmeli veya geri sonra hücre düzenleme modunda kalır. Böylece yalnızca kullanıcı hücrenin veya yalnızca kullanıcıların F2 basın yazarken hücre düzenleme moduna denetimi de yapılandırabilirsiniz. Son olarak, çağırdığınızda dışında düzenleme moduna geçmesini hücreleri engel olabilirsiniz <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> yöntemi.  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a>DataGridView denetiminin düzenleme modunu değiştirmek için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> özelliğine uygun <xref:System.Windows.Forms.DataGridViewEditMode> numaralandırması.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   Başvurular <xref:System> ve <xref:System.Windows.Forms> derlemeler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 [Veri girişi Windows Forms DataGridView denetimi](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)
