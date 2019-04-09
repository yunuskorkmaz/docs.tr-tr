---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminin Boyutlandırma Modlarını Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: d92322da6644c110f5e3177acebea62799a0ed89
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085460"
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="b86a1-102">Nasıl yapılır: Windows Forms DataGridView Denetiminin Boyutlandırma Modlarını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="b86a1-102">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b86a1-103">Aşağıdaki yordamlarda, özelleştirme veya boyutlandırma seçenekleri için birleştirme bazı yaygın senaryolar gösterilmektedir <xref:System.Windows.Forms.DataGridView> denetimi ve bir denetiminde özel sütunlar için.</span><span class="sxs-lookup"><span data-stu-id="b86a1-103">The following procedures demonstrate some common scenarios that customize or combine the sizing options available for the <xref:System.Windows.Forms.DataGridView> control and for specific columns in a control.</span></span>  
  
### <a name="to-create-a-fixed-width-column"></a><span data-ttu-id="b86a1-104">Sabit genişlikte sütun oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b86a1-104">To create a fixed-width column</span></span>  
  
-   <span data-ttu-id="b86a1-105">Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> özelliğini <xref:System.Windows.Forms.DataGridViewTriState.False>, <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> özelliğini `true`ve <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> özelliğini uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="b86a1-105">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, the <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> property to <xref:System.Windows.Forms.DataGridViewTriState.False>, the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`, and the <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> property to an appropriate value.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a><span data-ttu-id="b86a1-106">İçeriği sığdırmak için boyutunu ayarlayan bir sütun oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b86a1-106">To create a column that adjusts its size to fit its content</span></span>  
  
-   <span data-ttu-id="b86a1-107">Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> bir içerik tabanlı boyutlandırma modunu özelliği.</span><span class="sxs-lookup"><span data-stu-id="b86a1-107">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to a content-based sizing mode.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a><span data-ttu-id="b86a1-108">Değişen boyutunu ve önem derecesi değerlerini dolgu modunu sütunları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b86a1-108">To create fill-mode columns for values of varying size and importance</span></span>  
  
-   <span data-ttu-id="b86a1-109">Ayarlama <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> özelliğini <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> bu değeri geçersiz kılmaz tüm sütunlar için boyutlandırma modunu ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="b86a1-109">Set the <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> to set the sizing mode for all columns that do not override this value.</span></span> <span data-ttu-id="b86a1-110">Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özellikler için kendi ortalama orantılı olan değerleri sütun genişliklerini içerik.</span><span class="sxs-lookup"><span data-stu-id="b86a1-110">Set the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> properties of the columns to values that are proportional to their average content widths.</span></span> <span data-ttu-id="b86a1-111">Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> kısmi içerik görüntüsü emin olmak için önemli sütunların özellikleri.</span><span class="sxs-lookup"><span data-stu-id="b86a1-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> properties of important columns to ensure partial content display.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="b86a1-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="b86a1-112">Example</span></span>  
 <span data-ttu-id="b86a1-113">Aşağıdaki kod örneği, bu konuda açıklanan boyutlandırma seçenekleri anlamanıza yardımcı olabilecek bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="b86a1-113">The following complete code example provides a demonstration application that can help you understand the sizing options described in this topic.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 <span data-ttu-id="b86a1-114">Bu Tanıtım uygulamasını kullanmak için:</span><span class="sxs-lookup"><span data-stu-id="b86a1-114">To use this demonstration application:</span></span>  
  
-   <span data-ttu-id="b86a1-115">Formun boyutunu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b86a1-115">Change the size of the form.</span></span> <span data-ttu-id="b86a1-116">Oranlarını koruma tarafından gösterilen sırada dolgu modunu sütun genişliklerini nasıl değiştiğini gözlemlersiniz <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özellik değerleri.</span><span class="sxs-lookup"><span data-stu-id="b86a1-116">Observe how the fill-mode columns change their widths while retaining the proportions indicated by the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> property values.</span></span> <span data-ttu-id="b86a1-117">Bir sütunu nasıl 's gözlemleyin <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> form çok küçük olduğunda değiştirmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="b86a1-117">Observe how a column's <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> prevents it from changing when the form is too small.</span></span>  
  
-   <span data-ttu-id="b86a1-118">Fare ile sütun ayırıcılarını sürükleyerek sütunu boyutları değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b86a1-118">Change the column sizes by dragging the column dividers with the mouse.</span></span> <span data-ttu-id="b86a1-119">Bazı sütunları yeniden boyutlandırılan ve nasıl yeniden boyutlandırılabilir nasıl olamaz gözlemleyin sütunları yapılamıyor en düşük genişliklerini dar.</span><span class="sxs-lookup"><span data-stu-id="b86a1-119">Observe how some columns cannot be resized, and how resizable columns cannot be made narrower than their minimum widths.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b86a1-120">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b86a1-120">Compiling the Code</span></span>  
 <span data-ttu-id="b86a1-121">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b86a1-121">This example requires:</span></span>  
  
-   <span data-ttu-id="b86a1-122">Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="b86a1-122">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b86a1-123">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b86a1-123">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b86a1-124">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b86a1-124">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b86a1-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b86a1-125">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
