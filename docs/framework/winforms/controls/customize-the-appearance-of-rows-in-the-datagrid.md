---
title: DataGridView Denetimindeki satırların görünümünü özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: 099b2104e7a4887aa846c4d65273db2dd4f60559
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744033"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="44b05-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Satırların Görünüşünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="44b05-102">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="44b05-103"><xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> olaylarının bir veya her ikisini de işleyerek <xref:System.Windows.Forms.DataGridView> satırlarının görünümünü denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44b05-103">You can control the appearance of <xref:System.Windows.Forms.DataGridView> rows by handling one or both of the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> and <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> events.</span></span> <span data-ttu-id="44b05-104">Bu olaylar, <xref:System.Windows.Forms.DataGridView> denetimine geri kalanı boyamak için yalnızca istediğiniz şeyi boyamak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="44b05-104">These events are designed so that you can paint only what you want to while letting the <xref:System.Windows.Forms.DataGridView> control paint the rest.</span></span> <span data-ttu-id="44b05-105">Örneğin, özel bir arka plan boyamak isterseniz, <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> olayını işleyebilir ve tek tek hücrelerin kendi ön plan içeriğini boyamasına izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44b05-105">For example, if you want to paint a custom background, you can handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event and let the individual cells paint their own foreground content.</span></span> <span data-ttu-id="44b05-106">Alternatif olarak, hücrelerin kendilerini boyamasına izin verebilir ve <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> olayı için bir işleyiciye özel ön plan içeriği ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44b05-106">Alternately, you can let the cells paint themselves and add custom foreground content in a handler for the <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="44b05-107">Ayrıca, hücre boyamayı devre dışı bırakıp <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> olay işleyicisindeki her şeyi boyayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44b05-107">You can also disable cell painting and paint everything yourself in a <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event handler.</span></span>  
  
 <span data-ttu-id="44b05-108">Aşağıdaki kod örneği, bir gradyan seçim arka planı ve birden çok sütuna yayılan bazı özel ön plan içerikleri sağlamak için her iki olay için işleyicileri uygular.</span><span class="sxs-lookup"><span data-stu-id="44b05-108">The following code example implements handlers for both events in order to provide a gradient selection background and some custom foreground content that spans multiple columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44b05-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="44b05-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="44b05-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="44b05-110">Compiling the Code</span></span>  
 <span data-ttu-id="44b05-111">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="44b05-111">This example requires:</span></span>  
  
- <span data-ttu-id="44b05-112">System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="44b05-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b05-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44b05-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [<span data-ttu-id="44b05-114">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="44b05-114">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="44b05-115">DataGridView Denetimi Mimarisi</span><span class="sxs-lookup"><span data-stu-id="44b05-115">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
