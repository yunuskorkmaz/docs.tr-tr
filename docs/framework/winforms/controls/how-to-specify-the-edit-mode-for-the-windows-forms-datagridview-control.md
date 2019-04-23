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
ms.openlocfilehash: 7cb9278cd311d211ef95df238b930970ae472d05
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080403"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminin Düzenleme Modunu Belirtme
Varsayılan olarak, kullanıcılar geçerli içeriğini düzenleyebilir <xref:System.Windows.Forms.DataGridView> yazmak ya da F2 tuşuna basarak metin kutusu hücre. Tüm aşağıdaki koşullardan biri karşılanırsa bu hücre düzenleme moduna girer:  
  
-   Temel alınan veri kaynağına düzenlemeyi destekler.  
  
-   <xref:System.Windows.Forms.DataGridView> Denetimi etkinleştirildi.  
  
-   <xref:System.Windows.Forms.DataGridView.EditMode%2A> Özellik değeri değil <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.  
  
-   `ReadOnly` Hücre, satır, sütun ve denetim özellikleri olan tüm kümesine `false`.  
  
 Kullanıcı düzenleme modunda hücre değerini değiştirin ve değişikliği veya özgün değerine hücreye dönmek için ESC kaydetmek için ENTER tuşuna basın.  
  
 Yapılandırabileceğiniz bir <xref:System.Windows.Forms.DataGridView> böylece geçerli hücreyi duruma geldiğinde bir hücre düzenleme moduna girer. Bu durumda ENTER ve ESC anahtarları davranışını değiştirilmez, ancak değeri kaydedilmiş veya geri sonra hücre düzenleme modunda kalır. Yalnızca kullanıcılar hücre veya yalnızca, kullanıcılar F2 tuşuna yazarken hücre düzenleme moduna girin. böylece, denetimi yapılandırabilirsiniz. Son olarak, çağırdığınızda dışında düzenleme moduna geçmesini hücreleri engelleyebilir miyim <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> yöntemi.  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a>DataGridView denetiminin düzenleme modunu değiştirmek için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> özelliğini uygun <xref:System.Windows.Forms.DataGridViewEditMode> sabit listesi.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   Başvurular <xref:System> ve <xref:System.Windows.Forms> derlemeler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetiminde Veri Girişi](data-entry-in-the-windows-forms-datagridview-control.md)
