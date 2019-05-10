---
title: 'Nasıl yapılır: BindingSource ile Windows Forms Denetiminde Veri Kaynağı Güncelleştirmelerini Yansıtma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], updating
- BindingSource component [Windows Forms], updating data binding
- examples [Windows Forms], BindingSource component
- data sources [Windows Forms], updating
- BindingSource component [Windows Forms], examples
ms.assetid: bd8bd9b2-af8a-4f11-a3d5-54eecbe2400b
ms.openlocfilehash: e3ee6fd0f90840a8af3322e5ed66c0f7885211ae
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614696"
---
# <a name="how-to-reflect-data-source-updates-in-a-windows-forms-control-with-the-bindingsource"></a><span data-ttu-id="1b4ea-102">Nasıl yapılır: BindingSource ile Windows Forms Denetiminde Veri Kaynağı Güncelleştirmelerini Yansıtma</span><span class="sxs-lookup"><span data-stu-id="1b4ea-102">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>
<span data-ttu-id="1b4ea-103">Verilere bağlı denetimler kullandığınızda, bazen veri kaynağındaki değişiklikleri veri kaynağına listesi değişti olayları oluşturmaz, yanıtlamak zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b4ea-103">When you use data-bound controls, you sometimes have to respond to changes in the data source when the data source does not raise list-changed events.</span></span> <span data-ttu-id="1b4ea-104">Kullandığınızda, <xref:System.Windows.Forms.BindingSource> bileşen veri kaynağınızın bir Windows Forms denetimine bağlamak için veri kaynağınızın çağırarak değişti denetim bildirebilir <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1b4ea-104">When you use the <xref:System.Windows.Forms.BindingSource> component to bind your data source to a Windows Forms control, you can notify the control that your data source has changed by calling the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b4ea-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="1b4ea-105">Example</span></span>  
 <span data-ttu-id="1b4ea-106">Aşağıdaki kod örneği kullanmayı gösterir <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> ilişkili bir denetimi veri kaynağında bir güncelleştirme hakkında bilgilendirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1b4ea-106">The following code example demonstrates using the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method to notify a bound control about an update in the data source.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1b4ea-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1b4ea-107">Compiling the Code</span></span>  
 <span data-ttu-id="1b4ea-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="1b4ea-108">This example requires:</span></span>  
  
- <span data-ttu-id="1b4ea-109">Sistem, System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="1b4ea-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="1b4ea-110">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1b4ea-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1b4ea-111">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b4ea-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b4ea-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b4ea-112">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="1b4ea-113">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="1b4ea-113">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="1b4ea-114">Nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama</span><span class="sxs-lookup"><span data-stu-id="1b4ea-114">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
