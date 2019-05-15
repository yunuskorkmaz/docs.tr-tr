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
ms.openlocfilehash: 84f10540e7735ac1043e63eecda84161c10deeef
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591726"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="17e94-102">Nasıl yapılır: DateTimePicker Denetimiyle Zamanı Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="17e94-102">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="17e94-103">Bir tarih ve saat seçin ve bu tarih ve saati belirtilen biçimde görüntülemek için kullanıcıların sağlamak için uygulamanızı isterseniz <xref:System.Windows.Forms.DateTimePicker> denetimi.</span><span class="sxs-lookup"><span data-stu-id="17e94-103">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="17e94-104">Aşağıdaki yordam nasıl kullanılacağını gösterir <xref:System.Windows.Forms.DateTimePicker> denetimi bir saati görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="17e94-104">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="17e94-105">DateTimePicker denetimi ile bir saati görüntüleme</span><span class="sxs-lookup"><span data-stu-id="17e94-105">To display the time with the DateTimePicker control</span></span>  
  
1. <span data-ttu-id="17e94-106">Ayarlama <xref:System.Windows.Forms.DateTimePicker.Format%2A> özelliği <xref:System.Windows.Forms.DateTimePickerFormat.Time></span><span class="sxs-lookup"><span data-stu-id="17e94-106">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to <xref:System.Windows.Forms.DateTimePickerFormat.Time></span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="17e94-107">Ayarlama <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> özelliği <xref:System.Windows.Forms.DateTimePicker> için `true`.</span><span class="sxs-lookup"><span data-stu-id="17e94-107">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="17e94-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="17e94-108">Example</span></span>  
 <span data-ttu-id="17e94-109">Aşağıdaki kod örneği nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Forms.DateTimePicker> kullanıcıların yalnızca bir kez seçim sağlar.</span><span class="sxs-lookup"><span data-stu-id="17e94-109">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="17e94-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="17e94-110">Compiling the Code</span></span>  
 <span data-ttu-id="17e94-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="17e94-111">This example requires:</span></span>  
  
- <span data-ttu-id="17e94-112">Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="17e94-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17e94-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17e94-113">See also</span></span>

- [<span data-ttu-id="17e94-114">DateTimePicker Denetimi</span><span class="sxs-lookup"><span data-stu-id="17e94-114">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
