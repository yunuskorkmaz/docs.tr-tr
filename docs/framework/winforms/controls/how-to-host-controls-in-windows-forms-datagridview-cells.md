---
title: 'Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: a97af9bf0ef4016e54f877d934ed401b8dde7d4e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966602"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a>Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma
Bu <xref:System.Windows.Forms.DataGridView> denetim, kullanıcılarınızın çeşitli yollarla değer girmelerini ve düzenlemesini sağlayan çeşitli sütun türleri sağlar. Bu sütun türleri veri girişi gereksinimlerinizi karşılamıyorsa, seçtiğiniz denetimleri barındıran hücrelerle kendi sütun türlerinizi oluşturabilirsiniz. Bunu yapmak için, ve ' <xref:System.Windows.Forms.DataGridViewColumn> <xref:System.Windows.Forms.DataGridViewCell>den türetilen sınıfları tanımlamanız gerekir. Ayrıca <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms.IDataGridViewEditingControl> arabiriminden türetilen ve uygulayan bir sınıf tanımlamanız gerekir.  
  
 Aşağıdaki kod örneği, bir takvim sütununun nasıl oluşturulacağını göstermektedir. Bu sütunun hücreleri normal metin kutusu hücrelerindeki tarihleri görüntüler, ancak kullanıcı bir hücreyi düzenlediğinde bir <xref:System.Windows.Forms.DateTimePicker> denetim görüntülenir. Metin kutusu görüntüleme işlevini yeniden `CalendarCell` uygulamak zorunda kalmamak için sınıf doğrudan <xref:System.Windows.Forms.DataGridViewCell> sınıfı devralmak yerine <xref:System.Windows.Forms.DataGridViewTextBoxCell> sınıftan türetilir.  
  
> [!NOTE]
> Türetilmiş sınıfa türeten <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewColumn> yeni özellikler eklediğinizde, kopyalama işlemleri sırasında yeni özellikleri kopyalamak için `Clone` yöntemi geçersiz kıldığınızdan emin olun. Ayrıca temel sınıfın özelliklerini yeni hücreye veya sütuna `Clone` kopyalamak için temel sınıfın yöntemini çağırmanız gerekir.  
  
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
