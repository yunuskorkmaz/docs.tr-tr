---
title: DataGridView hücrelerinde konak denetimleri
description: Kullanıcılarınızın çeşitli yollarla değer girmesini ve düzenlemesini sağlamak için Windows Forms DataGridView hücrelerinde denetimlerin nasıl barındıralınacağını öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: 87901cbf86689bec49f5692feeabdae79f6b93ba
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619552"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a>Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma
Bu <xref:System.Windows.Forms.DataGridView> Denetim, kullanıcılarınızın çeşitli yollarla değer girmelerini ve düzenlemesini sağlayan çeşitli sütun türleri sağlar. Bu sütun türleri veri girişi gereksinimlerinizi karşılamıyorsa, seçtiğiniz denetimleri barındıran hücrelerle kendi sütun türlerinizi oluşturabilirsiniz. Bunu yapmak için, ve ' den türetilen sınıfları tanımlamanız gerekir <xref:System.Windows.Forms.DataGridViewColumn> <xref:System.Windows.Forms.DataGridViewCell> . Ayrıca arabiriminden türetilen ve uygulayan bir sınıf tanımlamanız gerekir <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms.IDataGridViewEditingControl> .  
  
 Aşağıdaki kod örneği, bir takvim sütununun nasıl oluşturulacağını göstermektedir. Bu sütunun hücreleri normal metin kutusu hücrelerindeki tarihleri görüntüler, ancak kullanıcı bir hücreyi düzenlediğinde bir <xref:System.Windows.Forms.DateTimePicker> Denetim görüntülenir. Metin kutusu görüntüleme işlevini yeniden uygulamak zorunda kalmamak için sınıf `CalendarCell` <xref:System.Windows.Forms.DataGridViewTextBoxCell> doğrudan sınıfı devralmak yerine sınıftan türetilir <xref:System.Windows.Forms.DataGridViewCell> .  
  
> [!NOTE]
> Türetilmiş sınıfa türeten <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewColumn> yeni özellikler eklediğinizde, `Clone` kopyalama işlemleri sırasında yeni özellikleri kopyalamak için yöntemi geçersiz kıldığınızdan emin olun. Ayrıca temel sınıfın `Clone` özelliklerini yeni hücreye veya sütuna kopyalamak için temel sınıfın yöntemini çağırmanız gerekir.  
  
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
- [DataGridView Denetim Mimarisi](datagridview-control-architecture-windows-forms.md)
- [Windows Forms DataGridView Denetiminde Sütun Türleri](column-types-in-the-windows-forms-datagridview-control.md)
