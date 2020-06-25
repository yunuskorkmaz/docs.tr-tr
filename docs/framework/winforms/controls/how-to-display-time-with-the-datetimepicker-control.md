---
title: 'Nasıl Yapılır: DateTimePicker Denetimiyle Zamanı Görüntüleme'
description: Kullanıcıların bir tarih ve saat seçmesini ve bu tarih ve saati belirtilen biçimde görüntülemesini sağlamak için Windows Forms DateTimePicker denetimini nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
ms.openlocfilehash: ab584367a189d05e567bb57d386c6bf629201102
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325590"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a>Nasıl Yapılır: DateTimePicker Denetimiyle Zamanı Görüntüleme
Uygulamanızın, kullanıcıların bir tarih ve saat seçmesini ve bu tarih ve saati belirtilen biçimde görüntülemesini istiyorsanız, <xref:System.Windows.Forms.DateTimePicker> denetimi kullanın. Aşağıdaki yordamda, <xref:System.Windows.Forms.DateTimePicker> zamanı göstermek için denetimin nasıl kullanılacağı gösterilmektedir.  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a>DateTimePicker denetimi ile saati görüntüleme  
  
1. <xref:System.Windows.Forms.DateTimePicker.Format%2A>Özelliğini olarak ayarlayın<xref:System.Windows.Forms.DateTimePickerFormat.Time>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2. İçin <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> özelliğini <xref:System.Windows.Forms.DateTimePicker> olarak ayarlayın `true` .  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.DateTimePicker> kullanıcıların yalnızca bir süre seçmesini sağlayan bir oluşturma yöntemi gösterilmektedir.  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DateTimePicker Denetimi](datetimepicker-control-windows-forms.md)
