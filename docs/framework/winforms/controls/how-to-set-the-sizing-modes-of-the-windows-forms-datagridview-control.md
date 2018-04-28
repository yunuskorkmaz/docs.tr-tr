---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminin Boyutlandırma Modlarını Ayarlama'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 62eb5c9dde5686bf2734e445b9c2a25477a5876f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="2a705-102">Nasıl yapılır: Windows Forms DataGridView Denetiminin Boyutlandırma Modlarını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="2a705-102">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="2a705-103">Aşağıdaki yordamlarda özelleştirme veya boyutlandırma seçenekleri için birleştirme bazı ortak senaryolar gösterilmektedir <xref:System.Windows.Forms.DataGridView> denetim ve belirli bir denetim sütunlar için.</span><span class="sxs-lookup"><span data-stu-id="2a705-103">The following procedures demonstrate some common scenarios that customize or combine the sizing options available for the <xref:System.Windows.Forms.DataGridView> control and for specific columns in a control.</span></span>  
  
### <a name="to-create-a-fixed-width-column"></a><span data-ttu-id="2a705-104">Bir sabit genişlikli sütun oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2a705-104">To create a fixed-width column</span></span>  
  
-   <span data-ttu-id="2a705-105">Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> özelliğine <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> özelliğine <xref:System.Windows.Forms.DataGridViewTriState.False>, <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> özelliğine `true`ve <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> uygun bir değere özelliği.</span><span class="sxs-lookup"><span data-stu-id="2a705-105">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, the <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> property to <xref:System.Windows.Forms.DataGridViewTriState.False>, the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`, and the <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> property to an appropriate value.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a><span data-ttu-id="2a705-106">Boyutuna içeriğinin sığması için ayarlayan bir sütun oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2a705-106">To create a column that adjusts its size to fit its content</span></span>  
  
-   <span data-ttu-id="2a705-107">Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> içerik tabanlı boyutlandırma modunu özelliğine.</span><span class="sxs-lookup"><span data-stu-id="2a705-107">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to a content-based sizing mode.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a><span data-ttu-id="2a705-108">Değişen boyutu ve önem derecesi değerlerini doldurma modu sütunlar oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2a705-108">To create fill-mode columns for values of varying size and importance</span></span>  
  
-   <span data-ttu-id="2a705-109">Ayarlama <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> özelliğine <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> bu değeri geçersiz kılmaz tüm sütunları boyutlandırma modunu ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="2a705-109">Set the <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> to set the sizing mode for all columns that do not override this value.</span></span> <span data-ttu-id="2a705-110">Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> kendi ortalama orantılı değerleri sütunlara özelliklerini içerik genişliği.</span><span class="sxs-lookup"><span data-stu-id="2a705-110">Set the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> properties of the columns to values that are proportional to their average content widths.</span></span> <span data-ttu-id="2a705-111">Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> kısmi içerik görüntüleme emin olmak için önemli sütunları özelliklerini.</span><span class="sxs-lookup"><span data-stu-id="2a705-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> properties of important columns to ensure partial content display.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="2a705-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a705-112">Example</span></span>  
 <span data-ttu-id="2a705-113">Aşağıdaki tam kod örneği, bu konuda açıklanan boyutlandırma seçenekleri anlamanıza yardımcı olabilir bir tanıtım uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a705-113">The following complete code example provides a demonstration application that can help you understand the sizing options described in this topic.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 <span data-ttu-id="2a705-114">Bu Demo uygulamayı kullanmak için:</span><span class="sxs-lookup"><span data-stu-id="2a705-114">To use this demonstration application:</span></span>  
  
-   <span data-ttu-id="2a705-115">Formun boyutunu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2a705-115">Change the size of the form.</span></span> <span data-ttu-id="2a705-116">Oranları koruma tarafından gösterilen sırada doldurma modu sütun genişliklerini nasıl değiştiğini gözlemleyin <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özellik değerleri.</span><span class="sxs-lookup"><span data-stu-id="2a705-116">Observe how the fill-mode columns change their widths while retaining the proportions indicated by the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> property values.</span></span> <span data-ttu-id="2a705-117">Bir sütun nasıl 's gözlemlemek <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> formun çok küçük olduğunda değiştirmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="2a705-117">Observe how a column's <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> prevents it from changing when the form is too small.</span></span>  
  
-   <span data-ttu-id="2a705-118">Sütun boyutlarını fareyle sütun Bölücü sürükleyerek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a705-118">Change the column sizes by dragging the column dividers with the mouse.</span></span> <span data-ttu-id="2a705-119">Bazı sütunları yeniden boyutlandırılan ve nasıl yeniden boyutlandırılabilir nasıl olamaz gözlemlemek sütun yapılamaz minimum genişliklerini dar.</span><span class="sxs-lookup"><span data-stu-id="2a705-119">Observe how some columns cannot be resized, and how resizable columns cannot be made narrower than their minimum widths.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2a705-120">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2a705-120">Compiling the Code</span></span>  
 <span data-ttu-id="2a705-121">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="2a705-121">This example requires:</span></span>  
  
-   <span data-ttu-id="2a705-122">Sistem ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="2a705-122">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="2a705-123">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2a705-123">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="2a705-124">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a705-124">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="2a705-125">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="2a705-125">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a705-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a705-126">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
