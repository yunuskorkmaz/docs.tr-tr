---
title: 'Nasıl yapılır: (Visual Studio) DataRepeater denetimi düzenini değiştirme'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, changing layout style
- DataRepeater, changing orientation
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
ms.openlocfilehash: 3389daa6383444b48faab4c5383b281e44349bce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625607"
---
# <a name="how-to-change-the-layout-of-a-datarepeater-control-visual-studio"></a><span data-ttu-id="087b6-102">Nasıl yapılır: (Visual Studio) DataRepeater denetimi düzenini değiştirme</span><span class="sxs-lookup"><span data-stu-id="087b6-102">How to: Change the Layout of a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="087b6-103"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Denetim görüntülenebilir bir (öğeleri kaydırma dikey) dikey veya yatay (öğeleri kaydırma yatay olarak) yönlendirmesi.</span><span class="sxs-lookup"><span data-stu-id="087b6-103">The <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control can be displayed in either a vertical (items scroll vertically) or horizontal (items scroll horizontally) orientation.</span></span> <span data-ttu-id="087b6-104">Tasarım zamanında veya çalışma zamanında yönünü değiştirerek değiştirebilirsiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="087b6-104">You can change the orientation at design time or at run time by changing the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property.</span></span> <span data-ttu-id="087b6-105">Değiştirirseniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> özelliği çalışma zamanında da isteyebilirsiniz yeniden boyutlandırmak <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> ve alt denetimler yeniden konumlandırma.</span><span class="sxs-lookup"><span data-stu-id="087b6-105">If you change the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property at run time, you may also want to resize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> and reposition the child controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="087b6-106">Denetimleri üzerinde yeniden konumlandırmak varsa <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> çalışma zamanında çağırmanız gerekir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> ve <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> denetimleri yeniden konumlandırır kod bloğunun sonunda ve başındaki yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="087b6-106">If you reposition controls on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> at run time, you will need to call the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> and <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> methods at the beginning and end of the code block that repositions the controls.</span></span>  
  
### <a name="to-change-the-layout-at-design-time"></a><span data-ttu-id="087b6-107">Tasarım zamanında düzenini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="087b6-107">To change the layout at design time</span></span>  
  
1.  <span data-ttu-id="087b6-108">Windows Form Tasarımcısı'nda seçin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.</span><span class="sxs-lookup"><span data-stu-id="087b6-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="087b6-109">Dış kenarlığı seçmelisiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> değil, üst denetimin alt bölgede tıklayarak denetim <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> bölge.</span><span class="sxs-lookup"><span data-stu-id="087b6-109">You must select the outer border of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control by clicking in the lower region of the control, not in the upper <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> region.</span></span>  
  
2.  <span data-ttu-id="087b6-110">Özellikler penceresinde ayarlayın <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> ya da özellik <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> veya <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.</span><span class="sxs-lookup"><span data-stu-id="087b6-110">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property to either <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.</span></span>  
  
### <a name="to-change-the-layout-at-run-time"></a><span data-ttu-id="087b6-111">Çalışma zamanında düzenini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="087b6-111">To change the layout at run time</span></span>  
  
1.  <span data-ttu-id="087b6-112">Bir düğmeyi veya menüyü aşağıdaki kodu ekleyin `Click` olay işleyicisi:</span><span class="sxs-lookup"><span data-stu-id="087b6-112">Add the following code to a button or menu `Click` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  <span data-ttu-id="087b6-113">Çoğu durumda, yeniden boyutlandırmak için örnek bölümünde gösterilen benzer kod eklemek isteyeceksiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> ve denetimleri yeni yönlendirmesini sığacak şekilde yeniden düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="087b6-113">In most cases, you will want to add code similar to that shown in the Example section to resize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> and rearrange controls to fit the new orientation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="087b6-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="087b6-114">Example</span></span>  
 <span data-ttu-id="087b6-115">Aşağıdaki örnek nasıl yanıt verileceğini gösterir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> olayı olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="087b6-115">The following example shows how to respond to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> event in an event handler.</span></span> <span data-ttu-id="087b6-116">Bu örnekte, olmasını gerektirir. bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> adlı Denetim `DataRepeater1` form ve, kendi <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> iki içeren <xref:System.Windows.Forms.TextBox> adlarında `TextBox1` ve `TextBox2`.</span><span class="sxs-lookup"><span data-stu-id="087b6-116">This example requires that you have a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control named `DataRepeater1` on a form and that its <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> contain two <xref:System.Windows.Forms.TextBox> controls named `TextBox1` and `TextBox2`.</span></span>  
  
 [!code-csharp[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="087b6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="087b6-117">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>
- [<span data-ttu-id="087b6-118">DataRepeater Denetimine Giriş</span><span class="sxs-lookup"><span data-stu-id="087b6-118">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="087b6-119">DataRepeater Denetiminde Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="087b6-119">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="087b6-120">Nasıl yapılır: DataRepeater denetiminin görünümünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="087b6-120">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
