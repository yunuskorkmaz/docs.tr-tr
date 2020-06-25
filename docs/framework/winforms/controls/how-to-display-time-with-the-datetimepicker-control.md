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
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="cedd2-103">Nasıl Yapılır: DateTimePicker Denetimiyle Zamanı Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="cedd2-103">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="cedd2-104">Uygulamanızın, kullanıcıların bir tarih ve saat seçmesini ve bu tarih ve saati belirtilen biçimde görüntülemesini istiyorsanız, <xref:System.Windows.Forms.DateTimePicker> denetimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="cedd2-104">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="cedd2-105">Aşağıdaki yordamda, <xref:System.Windows.Forms.DateTimePicker> zamanı göstermek için denetimin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cedd2-105">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="cedd2-106">DateTimePicker denetimi ile saati görüntüleme</span><span class="sxs-lookup"><span data-stu-id="cedd2-106">To display the time with the DateTimePicker control</span></span>  
  
1. <span data-ttu-id="cedd2-107"><xref:System.Windows.Forms.DateTimePicker.Format%2A>Özelliğini olarak ayarlayın<xref:System.Windows.Forms.DateTimePickerFormat.Time></span><span class="sxs-lookup"><span data-stu-id="cedd2-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to <xref:System.Windows.Forms.DateTimePickerFormat.Time></span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="cedd2-108">İçin <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> özelliğini <xref:System.Windows.Forms.DateTimePicker> olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="cedd2-108">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="cedd2-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="cedd2-109">Example</span></span>  
 <span data-ttu-id="cedd2-110">Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.DateTimePicker> kullanıcıların yalnızca bir süre seçmesini sağlayan bir oluşturma yöntemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cedd2-110">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cedd2-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="cedd2-111">Compiling the Code</span></span>  
 <span data-ttu-id="cedd2-112">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="cedd2-112">This example requires:</span></span>  
  
- <span data-ttu-id="cedd2-113">System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="cedd2-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cedd2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cedd2-114">See also</span></span>

- [<span data-ttu-id="cedd2-115">DateTimePicker Denetimi</span><span class="sxs-lookup"><span data-stu-id="cedd2-115">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
