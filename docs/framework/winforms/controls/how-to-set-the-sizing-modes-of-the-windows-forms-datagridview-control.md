---
title: DataGridView denetiminin boyutlandırma modlarını ayarlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: 15b084afa4149ac43d40aeae7f35f0eaff5ac0e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738398"
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="168eb-102">Nasıl yapılır: Windows Forms DataGridView Denetiminin Boyutlandırma Modlarını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="168eb-102">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="168eb-103">Aşağıdaki yordamlarda <xref:System.Windows.Forms.DataGridView> denetimi ve denetimdeki belirli sütunlar için kullanılabilir boyutlandırma seçeneklerini özelleştiren veya birleştiren bazı yaygın senaryolar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="168eb-103">The following procedures demonstrate some common scenarios that customize or combine the sizing options available for the <xref:System.Windows.Forms.DataGridView> control and for specific columns in a control.</span></span>  
  
### <a name="to-create-a-fixed-width-column"></a><span data-ttu-id="168eb-104">Sabit genişlikte bir sütun oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="168eb-104">To create a fixed-width column</span></span>  
  
- <span data-ttu-id="168eb-105"><xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> özelliğini <xref:System.Windows.Forms.DataGridViewTriState.False>, <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> özelliğini `true`ve <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> özelliğini uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="168eb-105">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, the <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> property to <xref:System.Windows.Forms.DataGridViewTriState.False>, the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`, and the <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> property to an appropriate value.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a><span data-ttu-id="168eb-106">Boyutunu içeriğe sığacak şekilde ayarlayan bir sütun oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="168eb-106">To create a column that adjusts its size to fit its content</span></span>  
  
- <span data-ttu-id="168eb-107"><xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> özelliğini içerik tabanlı boyutlandırma moduna ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="168eb-107">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to a content-based sizing mode.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a><span data-ttu-id="168eb-108">Değişen boyut ve önem düzeyi değerleri için Fill-Mode sütunları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="168eb-108">To create fill-mode columns for values of varying size and importance</span></span>  
  
- <span data-ttu-id="168eb-109">Bu değeri geçersiz kılmayan tüm sütunlar için boyutlandırma modunu ayarlamak için <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> özelliğini <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="168eb-109">Set the <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> to set the sizing mode for all columns that do not override this value.</span></span> <span data-ttu-id="168eb-110">Sütunların <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özelliklerini, ortalama içerik genişlikleriyle orantılı değerlere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="168eb-110">Set the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> properties of the columns to values that are proportional to their average content widths.</span></span> <span data-ttu-id="168eb-111">Kısmi içerik görüntülenmesini sağlamak için önemli sütunların <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="168eb-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> properties of important columns to ensure partial content display.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="168eb-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="168eb-112">Example</span></span>  
 <span data-ttu-id="168eb-113">Aşağıdaki kod örneği, bu konuda açıklanan boyutlandırma seçeneklerini anlamanıza yardımcı olabilecek bir tanıtım uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="168eb-113">The following complete code example provides a demonstration application that can help you understand the sizing options described in this topic.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 <span data-ttu-id="168eb-114">Bu demo uygulamasını kullanmak için:</span><span class="sxs-lookup"><span data-stu-id="168eb-114">To use this demonstration application:</span></span>  
  
- <span data-ttu-id="168eb-115">Formun boyutunu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="168eb-115">Change the size of the form.</span></span> <span data-ttu-id="168eb-116"><xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özellik değerleri tarafından belirtilen oranları korurken, Fill modundaki sütunların genişliklerini nasıl değiştirdiğini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="168eb-116">Observe how the fill-mode columns change their widths while retaining the proportions indicated by the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> property values.</span></span> <span data-ttu-id="168eb-117">Form çok küçük olduğunda bir sütunun <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> değiştirilmesini nasıl önlütürdiğini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="168eb-117">Observe how a column's <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> prevents it from changing when the form is too small.</span></span>  
  
- <span data-ttu-id="168eb-118">Sütun bölücüleri fareyle sürükleyerek sütun boyutlarını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="168eb-118">Change the column sizes by dragging the column dividers with the mouse.</span></span> <span data-ttu-id="168eb-119">Bazı sütunların yeniden boyutlandırılamayacağını ve yeniden boyutlandırılabilir sütunların minimum genişliklerinden daha dar bir şekilde yapıllamayacağını gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="168eb-119">Observe how some columns cannot be resized, and how resizable columns cannot be made narrower than their minimum widths.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="168eb-120">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="168eb-120">Compiling the Code</span></span>  
 <span data-ttu-id="168eb-121">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="168eb-121">This example requires:</span></span>  
  
- <span data-ttu-id="168eb-122">System ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="168eb-122">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="168eb-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="168eb-123">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
