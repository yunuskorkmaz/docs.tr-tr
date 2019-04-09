---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Satırların Görünüşünü Özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: 107ec75257907b934412d9ee333b00d5df05a99c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110325"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a9a82-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Satırların Görünüşünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="a9a82-102">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a9a82-103">Görünümünü denetleyebilirsiniz <xref:System.Windows.Forms.DataGridView> birini veya her ikisini işleme tarafından satırları <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> olayları.</span><span class="sxs-lookup"><span data-stu-id="a9a82-103">You can control the appearance of <xref:System.Windows.Forms.DataGridView> rows by handling one or both of the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> and <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> events.</span></span> <span data-ttu-id="a9a82-104">Bu olaylar yalnızca while izin vermek istediğiniz boyama yapabileceğiniz şekilde tasarlanmıştır <xref:System.Windows.Forms.DataGridView> denetim boyama rest.</span><span class="sxs-lookup"><span data-stu-id="a9a82-104">These events are designed so that you can paint only what you want to while letting the <xref:System.Windows.Forms.DataGridView> control paint the rest.</span></span> <span data-ttu-id="a9a82-105">Örneğin, özel bir arka plan boyama istiyorsanız işleyebilirsiniz <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> olay ve tek tek hücrelere boyama kendi let ön plan içeriği.</span><span class="sxs-lookup"><span data-stu-id="a9a82-105">For example, if you want to paint a custom background, you can handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event and let the individual cells paint their own foreground content.</span></span> <span data-ttu-id="a9a82-106">Alternatif olarak, kendilerini boyama ve özel ön içerik için bir işleyici eklemek hücreleri sağlayabilirsiniz <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> olay.</span><span class="sxs-lookup"><span data-stu-id="a9a82-106">Alternately, you can let the cells paint themselves and add custom foreground content in a handler for the <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="a9a82-107">Ayrıca hücre boyama devre dışı bırakın ve içindeki her şeyi kendiniz boyama bir <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a9a82-107">You can also disable cell painting and paint everything yourself in a <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event handler.</span></span>  
  
 <span data-ttu-id="a9a82-108">Aşağıdaki kod örneği, arka plan gradyan seçimi ve birden fazla sütuna yayılmış bazı özel ön plan içeriği sağlamak için her iki olay işleyicileri uygular.</span><span class="sxs-lookup"><span data-stu-id="a9a82-108">The following code example implements handlers for both events in order to provide a gradient selection background and some custom foreground content that spans multiple columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9a82-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9a82-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a9a82-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a9a82-110">Compiling the Code</span></span>  
 <span data-ttu-id="a9a82-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a9a82-111">This example requires:</span></span>  
  
-   <span data-ttu-id="a9a82-112">Sistem, System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="a9a82-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="a9a82-113">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a9a82-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="a9a82-114">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9a82-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  

## <a name="see-also"></a><span data-ttu-id="a9a82-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9a82-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [<span data-ttu-id="a9a82-116">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="a9a82-116">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a9a82-117">DataGridView Denetimi Mimarisi</span><span class="sxs-lookup"><span data-stu-id="a9a82-117">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
