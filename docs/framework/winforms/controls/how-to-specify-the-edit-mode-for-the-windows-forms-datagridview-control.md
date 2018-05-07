---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminin Düzenleme Modunu Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: 5117dfe2e017cf4af1d352fdbf23c6599c0e56a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [Windows Forms DataGridView Denetiminde Veri Girişi](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)
