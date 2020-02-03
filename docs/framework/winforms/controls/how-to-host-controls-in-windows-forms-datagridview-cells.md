---
title: DataGridView hücrelerinde konak denetimleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: a64521a15a272ca8140302f39d15e7f17e0c423b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736531"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a>Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma
<xref:System.Windows.Forms.DataGridView> denetimi, kullanıcılarınızın çeşitli yollarla değer girmelerini ve düzenlemesini sağlayan çeşitli sütun türleri sağlar. Bu sütun türleri veri girişi gereksinimlerinizi karşılamıyorsa, seçtiğiniz denetimleri barındıran hücrelerle kendi sütun türlerinizi oluşturabilirsiniz. Bunu yapmak için, <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.Windows.Forms.DataGridViewCell>türetilen sınıfları tanımlamanız gerekir. Ayrıca, <xref:System.Windows.Forms.Control> türetilen ve <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimini uygulayan bir sınıf tanımlamanız gerekir.  
  
 Aşağıdaki kod örneği, bir takvim sütununun nasıl oluşturulacağını göstermektedir. Bu sütunun hücreleri normal metin kutusu hücrelerindeki tarihleri görüntüler, ancak kullanıcı bir hücreyi düzenlediğinde bir <xref:System.Windows.Forms.DateTimePicker> denetimi görünür. Metin kutusu görüntüleme işlevini yeniden uygulamak zorunda kalmamak için `CalendarCell` sınıfı, <xref:System.Windows.Forms.DataGridViewCell> sınıfını doğrudan devralmak yerine <xref:System.Windows.Forms.DataGridViewTextBoxCell> sınıfından türetilir.  
  
> [!NOTE]
> <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewColumn> türettiğinizde ve türetilmiş sınıfa yeni özellikler eklediğinizde, kopyalama işlemleri sırasında yeni özellikleri kopyalamak için `Clone` yöntemini geçersiz kıldığınızdan emin olun. Temel sınıfın özelliklerinin yeni hücreye veya sütuna kopyalanabilmesi için temel sınıfın `Clone` yöntemini de çağırmalısınız.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Aşağıdaki örnek şunları gerektirir:  
  
- System ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [Windows Forms DataGridView Denetimini Özelleştirme](customizing-the-windows-forms-datagridview-control.md)
- [DataGridView Denetimi Mimarisi](datagridview-control-architecture-windows-forms.md)
- [Windows Forms DataGridView Denetiminde Sütun Türleri](column-types-in-the-windows-forms-datagridview-control.md)
