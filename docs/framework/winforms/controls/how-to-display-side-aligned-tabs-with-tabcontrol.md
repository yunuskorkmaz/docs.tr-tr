---
title: 'Nasıl yapılır: TabControl ile yana hizalanmış sekmeler görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
ms.openlocfilehash: 8715cb1a1f0d5795afc4003afcecdb3fb89912c3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705197"
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a><span data-ttu-id="8c542-102">Nasıl yapılır: TabControl ile yana hizalanmış sekmeler görüntüleme</span><span class="sxs-lookup"><span data-stu-id="8c542-102">How to: Display Side-Aligned Tabs with TabControl</span></span>
<span data-ttu-id="8c542-103"><xref:System.Windows.Forms.TabControl.Alignment%2A> Özelliği <xref:System.Windows.Forms.TabControl> yatay (üst veya alt denetimin) olarak, dikey (sol veya sağ kenarı boyunca denetimi), sekmeler görüntüleme destekler.</span><span class="sxs-lookup"><span data-stu-id="8c542-103">The <xref:System.Windows.Forms.TabControl.Alignment%2A> property of <xref:System.Windows.Forms.TabControl> supports displaying tabs vertically (along the left or right edge of the control), as opposed to horizontally (across the top or bottom of the control).</span></span> <span data-ttu-id="8c542-104">Varsayılan olarak, çünkü bu dikey ekran bir kullanıcı deneyimi zayıf içinde sonuçları <xref:System.Windows.Forms.TabPage.Text%2A> özelliği <xref:System.Windows.Forms.TabPage> nesne görsel stiller etkinken sekmede görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="8c542-104">By default, this vertical display results in a poor user experience, because the <xref:System.Windows.Forms.TabPage.Text%2A> property of the <xref:System.Windows.Forms.TabPage> object does not display in the tab when visual styles are enabled.</span></span> <span data-ttu-id="8c542-105">Sekme içindeki metnin yönünü denetlemek için doğrudan bir yol yoktur. Sahibi kullanabileceğiniz üzerine çizileceği <xref:System.Windows.Forms.TabControl> iyi bir deneyim sunmak için.</span><span class="sxs-lookup"><span data-stu-id="8c542-105">There is also no direct way to control the direction of the text within the tab. You can use owner draw on <xref:System.Windows.Forms.TabControl> to improve this experience.</span></span>  
  
 <span data-ttu-id="8c542-106">Aşağıdaki yordam, soldan sağa "sahibi Çiz" özelliğini kullanarak çalışan sekmesini metin içeren sağa hizalanmış sekmeler, nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8c542-106">The following procedure shows how to render right-aligned tabs, with the tab text running from left to right, by using the "owner draw" feature.</span></span>  
  
### <a name="to-display-right-aligned-tabs"></a><span data-ttu-id="8c542-107">Sağa hizalı sekmelerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="8c542-107">To display right-aligned tabs</span></span>  
  
1.  <span data-ttu-id="8c542-108">Ekleme bir <xref:System.Windows.Forms.TabControl> formunuza.</span><span class="sxs-lookup"><span data-stu-id="8c542-108">Add a <xref:System.Windows.Forms.TabControl> to your form.</span></span>  
  
2.  <span data-ttu-id="8c542-109">Ayarlama <xref:System.Windows.Forms.TabControl.Alignment%2A> özelliğini <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="8c542-109">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property to <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
3.  <span data-ttu-id="8c542-110">Ayarlama <xref:System.Windows.Forms.TabControl.SizeMode%2A> özelliğini <xref:System.Windows.Forms.TabSizeMode.Fixed>, böylece tüm sekmeler aynı genişliktedir.</span><span class="sxs-lookup"><span data-stu-id="8c542-110">Set the <xref:System.Windows.Forms.TabControl.SizeMode%2A> property to <xref:System.Windows.Forms.TabSizeMode.Fixed>, so that all tabs are the same width.</span></span>  
  
4.  <span data-ttu-id="8c542-111">Ayarlama <xref:System.Windows.Forms.TabControl.ItemSize%2A> özelliği tercih edilen sekmeleri boyutu sabit.</span><span class="sxs-lookup"><span data-stu-id="8c542-111">Set the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property to the preferred fixed size for the tabs.</span></span> <span data-ttu-id="8c542-112">Aklınızda <xref:System.Windows.Forms.TabControl.ItemSize%2A> özelliği, sekmeleri en üstte gibi davranarak sağa hizalı olmasına rağmen davranır.</span><span class="sxs-lookup"><span data-stu-id="8c542-112">Keep in mind that the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property behaves as though the tabs were on top, although they are right-aligned.</span></span> <span data-ttu-id="8c542-113">Sonuç olarak, sekmeleri geniş hale getirmek için değiştirmeniz gerekir <xref:System.Drawing.Size.Height%2A> özelliği ve uzun hale getirmek için değiştirmelisiniz <xref:System.Drawing.Size.Width%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="8c542-113">As a result, in order to make the tabs wider, you must change the <xref:System.Drawing.Size.Height%2A> property, and in order to make them taller, you must change the <xref:System.Drawing.Size.Width%2A> property.</span></span>  
  
     <span data-ttu-id="8c542-114">Aşağıdaki kod örneği ile en iyi sonuç için kümesi <xref:System.Drawing.Size.Width%2A> 25 sekmeleri ve <xref:System.Drawing.Size.Height%2A> 100.</span><span class="sxs-lookup"><span data-stu-id="8c542-114">For best result with the code example below, set the <xref:System.Drawing.Size.Width%2A> of the tabs to 25 and the <xref:System.Drawing.Size.Height%2A> to 100.</span></span>  
  
5.  <span data-ttu-id="8c542-115">Ayarlama <xref:System.Windows.Forms.TabControl.DrawMode%2A> özelliğini <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.</span><span class="sxs-lookup"><span data-stu-id="8c542-115">Set the <xref:System.Windows.Forms.TabControl.DrawMode%2A> property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.</span></span>  
  
6.  <span data-ttu-id="8c542-116">Tanımlamak için bir işleyici <xref:System.Windows.Forms.TabControl.DrawItem> olayı <xref:System.Windows.Forms.TabControl> , soldan sağa metnin işler.</span><span class="sxs-lookup"><span data-stu-id="8c542-116">Define a handler for the <xref:System.Windows.Forms.TabControl.DrawItem> event of <xref:System.Windows.Forms.TabControl> that renders the text from left to right.</span></span>  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](~/samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8c542-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c542-117">See also</span></span>
- [<span data-ttu-id="8c542-118">TabControl Denetimi</span><span class="sxs-lookup"><span data-stu-id="8c542-118">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
