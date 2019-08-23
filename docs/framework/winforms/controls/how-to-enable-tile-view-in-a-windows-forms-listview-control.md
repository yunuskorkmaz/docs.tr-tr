---
title: 'Nasıl yapılır: Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tile view feature
- tiling
- Windows Forms, controls
- ListView control [Windows Forms], tile view
ms.assetid: c20e67a3-2d94-413d-9fcf-ecbd0fe251da
ms.openlocfilehash: 44d34ddb00005a0fb86b2d06c4c14e2a5b949819
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966686"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="cd00b-102">Nasıl yapılır: Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="cd00b-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="cd00b-103"><xref:System.Windows.Forms.ListView> Denetimin kutucuk görünümü özelliği ile grafik ve metin bilgileri arasında bir görsel denge sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd00b-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="cd00b-104">Kutucuk görünümündeki bir öğe için görünen metin bilgileri, Ayrıntılar görünümü için tanımlanan sütun bilgileri ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="cd00b-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="cd00b-105">Kutucuk görünümü, <xref:System.Windows.Forms.ListView> denetimdeki gruplandırma ya da ekleme işareti özellikleriyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cd00b-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="cd00b-106">Kutucuk görünümü, aşağıdaki görüntülerde gösterildiği gibi bir 32 x 32 piksel simgesi ve birkaç satırlık metin kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd00b-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="cd00b-107">![ListView denetimindeki kutucuk görünümü](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Kutucuk görünümü simgeleri ve metni")</span><span class="sxs-lookup"><span data-stu-id="cd00b-107">![Tile View in a ListView Control](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>  
 
 <span data-ttu-id="cd00b-108">Kutucuk görünümünü etkinleştirmek için <xref:System.Windows.Forms.ListView.View%2A> özelliğini olarak <xref:System.Windows.Forms.View.Tile>ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cd00b-108">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="cd00b-109"><xref:System.Windows.Forms.ListView.TileSize%2A> Özelliği ayarlayarak kutucukların boyutunu ve <xref:System.Windows.Forms.ListView.Columns%2A> koleksiyonu ayarlayarak kutucukta görünen metin çizgilerinin sayısını ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd00b-109">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd00b-110">Kutucuk görünümü yalnızca [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanız <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi çağırdığında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd00b-110">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cd00b-111">Önceki işletim sistemlerinde, kutucuk görünümüyle ilgili tüm kodlar etkisizdir ve <xref:System.Windows.Forms.ListView> denetim büyük simge görünümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cd00b-111">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="cd00b-112">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cd00b-112">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="cd00b-113">Kutucuk görünümünü programlı bir şekilde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="cd00b-113">To set tile view programmatically</span></span>  
  
1. <span data-ttu-id="cd00b-114"><xref:System.Windows.Forms.ListView> Denetimin <xref:System.Windows.Forms.View> numaralandırmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd00b-114">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="cd00b-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd00b-115">Example</span></span>  
 <span data-ttu-id="cd00b-116">Aşağıdaki kod örneği, üç satırlık metin göstermek için değiştirilen kutucukları içeren kutucuk görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd00b-116">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="cd00b-117">Kutucuk boyutu, satır kaydırmayı engelleyecek şekilde ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="cd00b-117">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cd00b-118">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="cd00b-118">Compiling the Code</span></span>  
 <span data-ttu-id="cd00b-119">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="cd00b-119">This example requires:</span></span>  
  
- <span data-ttu-id="cd00b-120">System ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="cd00b-120">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="cd00b-121">Yürütülebilir dosya ile aynı dizinde Book. ico adlı bir simge dosyası.</span><span class="sxs-lookup"><span data-stu-id="cd00b-121">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd00b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd00b-122">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="cd00b-123">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="cd00b-123">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="cd00b-124">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cd00b-124">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
