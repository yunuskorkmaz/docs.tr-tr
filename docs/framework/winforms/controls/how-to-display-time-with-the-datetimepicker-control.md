---
title: 'Nasıl Yapılır: DateTimePicker Denetimiyle Zamanı Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
ms.openlocfilehash: 16e09225c9447f9ec8be3b658ac0ed1aa3b2edab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531836"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="6c62e-102">Nasıl Yapılır: DateTimePicker Denetimiyle Zamanı Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="6c62e-102">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="6c62e-103">Kullanıcıların bir tarih ve saati seçin ve bu tarih ve saati belirtilen biçimde görüntülemek için kullanmak uygulamanızı isteyip istemediğinizi <xref:System.Windows.Forms.DateTimePicker> denetim.</span><span class="sxs-lookup"><span data-stu-id="6c62e-103">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="6c62e-104">Aşağıdaki yordam nasıl kullanılacağını gösterir <xref:System.Windows.Forms.DateTimePicker> zaman görüntülemek için denetim.</span><span class="sxs-lookup"><span data-stu-id="6c62e-104">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="6c62e-105">DateTimePicker denetimi ile zaman görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="6c62e-105">To display the time with the DateTimePicker control</span></span>  
  
1.  <span data-ttu-id="6c62e-106">Ayarlama <xref:System.Windows.Forms.DateTimePicker.Format%2A> özelliği <xref:System.Windows.Forms.DateTimePickerFormat.Time></span><span class="sxs-lookup"><span data-stu-id="6c62e-106">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to <xref:System.Windows.Forms.DateTimePickerFormat.Time></span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2.  <span data-ttu-id="6c62e-107">Ayarlama <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> özelliği için <xref:System.Windows.Forms.DateTimePicker> için `true`.</span><span class="sxs-lookup"><span data-stu-id="6c62e-107">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="6c62e-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c62e-108">Example</span></span>  
 <span data-ttu-id="6c62e-109">Aşağıdaki kod örneği nasıl oluşturulacağını gösterir bir <xref:System.Windows.Forms.DateTimePicker> kullanıcıların yalnızca bir kez seçmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c62e-109">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6c62e-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="6c62e-110">Compiling the Code</span></span>  
 <span data-ttu-id="6c62e-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="6c62e-111">This example requires:</span></span>  
  
-   <span data-ttu-id="6c62e-112">Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="6c62e-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="6c62e-113">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6c62e-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6c62e-114">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c62e-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="6c62e-115">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="6c62e-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c62e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c62e-116">See Also</span></span>  
 [<span data-ttu-id="6c62e-117">DateTimePicker Denetimi</span><span class="sxs-lookup"><span data-stu-id="6c62e-117">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)
