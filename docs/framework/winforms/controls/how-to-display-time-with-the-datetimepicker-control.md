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
ms.openlocfilehash: f1c1a0abaeddadb44b40d56eb2f8a28e4b58f4f5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651779"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="36d4b-102">Nasıl yapılır: DateTimePicker Denetimiyle Zamanı Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="36d4b-102">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="36d4b-103">Bir tarih ve saat seçin ve bu tarih ve saati belirtilen biçimde görüntülemek için kullanıcıların sağlamak için uygulamanızı isterseniz <xref:System.Windows.Forms.DateTimePicker> denetimi.</span><span class="sxs-lookup"><span data-stu-id="36d4b-103">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="36d4b-104">Aşağıdaki yordam nasıl kullanılacağını gösterir <xref:System.Windows.Forms.DateTimePicker> denetimi bir saati görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="36d4b-104">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="36d4b-105">DateTimePicker denetimi ile bir saati görüntüleme</span><span class="sxs-lookup"><span data-stu-id="36d4b-105">To display the time with the DateTimePicker control</span></span>  
  
1. <span data-ttu-id="36d4b-106">Ayarlama <xref:System.Windows.Forms.DateTimePicker.Format%2A> özelliği <xref:System.Windows.Forms.DateTimePickerFormat.Time></span><span class="sxs-lookup"><span data-stu-id="36d4b-106">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to <xref:System.Windows.Forms.DateTimePickerFormat.Time></span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="36d4b-107">Ayarlama <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> özelliği <xref:System.Windows.Forms.DateTimePicker> için `true`.</span><span class="sxs-lookup"><span data-stu-id="36d4b-107">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="36d4b-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="36d4b-108">Example</span></span>  
 <span data-ttu-id="36d4b-109">Aşağıdaki kod örneği nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Forms.DateTimePicker> kullanıcıların yalnızca bir kez seçim sağlar.</span><span class="sxs-lookup"><span data-stu-id="36d4b-109">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="36d4b-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="36d4b-110">Compiling the Code</span></span>  
 <span data-ttu-id="36d4b-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="36d4b-111">This example requires:</span></span>  
  
- <span data-ttu-id="36d4b-112">Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="36d4b-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="36d4b-113">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="36d4b-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="36d4b-114">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36d4b-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d4b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36d4b-115">See also</span></span>

- [<span data-ttu-id="36d4b-116">DateTimePicker Denetimi</span><span class="sxs-lookup"><span data-stu-id="36d4b-116">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
