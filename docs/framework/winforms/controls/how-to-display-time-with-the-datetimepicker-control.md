---
title: 'Nasıl yapılır: DateTimePicker Denetimiyle Zamanı Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
ms.openlocfilehash: 7906811d5a324ba3f2bd73cc057298e007ac311b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941563"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a>Nasıl yapılır: DateTimePicker Denetimiyle Zamanı Görüntüleme
Bir tarih ve saat seçin ve bu tarih ve saati belirtilen biçimde görüntülemek için kullanıcıların sağlamak için uygulamanızı isterseniz <xref:System.Windows.Forms.DateTimePicker> denetimi. Aşağıdaki yordam nasıl kullanılacağını gösterir <xref:System.Windows.Forms.DateTimePicker> denetimi bir saati görüntüleme.  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a>DateTimePicker denetimi ile bir saati görüntüleme  
  
1. Ayarlama <xref:System.Windows.Forms.DateTimePicker.Format%2A> özelliği <xref:System.Windows.Forms.DateTimePickerFormat.Time>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2. Ayarlama <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> özelliği <xref:System.Windows.Forms.DateTimePicker> için `true`.  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Forms.DateTimePicker> kullanıcıların yalnızca bir kez seçim sağlar.  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DateTimePicker Denetimi](datetimepicker-control-windows-forms.md)
