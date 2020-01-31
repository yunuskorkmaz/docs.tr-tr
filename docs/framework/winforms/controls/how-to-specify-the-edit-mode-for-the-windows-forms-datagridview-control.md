---
title: DataGridView denetimi için düzenleme modunu belirtin
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: c0318202a80f9a43f1b656201732ef032f430b5b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743769"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminin Düzenleme Modunu Belirtme
Varsayılan olarak, kullanıcılar geçerli <xref:System.Windows.Forms.DataGridView> metin kutusu hücresinin içeriğini yazarak veya F2 tuşuna basarak düzenleyebilir. Bu, aşağıdaki koşulların tümü karşılanıyorsa hücreyi düzenleme moduna geçirir:  
  
- Temel alınan veri kaynağı, düzenlemesini destekler.  
  
- <xref:System.Windows.Forms.DataGridView> denetimi etkinleştirilir.  
  
- <xref:System.Windows.Forms.DataGridView.EditMode%2A> Özellik değeri <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>değil.  
  
- Hücrenin, satırın, sütunun ve denetimin `ReadOnly` özellikleri `false`olarak ayarlanır.  
  
 Düzenleme modunda, Kullanıcı hücre değerini değiştirebilir ve değişikliği kaydetmek için ENTER tuşuna basarak hücreyi özgün değerine döndürebilir.  
  
 Bir <xref:System.Windows.Forms.DataGridView> denetimini, bir hücrenin geçerli hücreye dönüşen kısa sürede düzenleme moduna girmesi için yapılandırabilirsiniz. Bu durumda ENTER ve ESC tuşlarının davranışı değiştirilmez, ancak değer kaydedildikten veya geri döndürüldüğünden hücre düzenleme modunda kalır. Ayrıca, denetimin yalnızca kullanıcılar hücreye yazmaları veya Kullanıcı F2 'ye basması durumunda düzenleme moduna girmesi için denetimi de yapılandırabilirsiniz. Son olarak, <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> yöntemini çağırdığınızda hücrelerin düzenleme moduna girmesini engelleyebilirsiniz.  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a>DataGridView denetiminin düzenleme modunu değiştirmek için  
  
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> özelliğini uygun <xref:System.Windows.Forms.DataGridViewEditMode> sabit listesine ayarlayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- `dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.  
  
- <xref:System> ve <xref:System.Windows.Forms> derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetiminde Veri Girişi](data-entry-in-the-windows-forms-datagridview-control.md)
