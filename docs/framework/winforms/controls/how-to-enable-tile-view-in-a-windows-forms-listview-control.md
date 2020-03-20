---
title: ListView Denetiminde Döşeme Görünümü etkinleştirme
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
ms.openlocfilehash: 1478ba5e4f175cd7d9ec7ab5c3c4bc9050ce02fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182160"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="ef11b-102">Nasıl yapılır Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="ef11b-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="ef11b-103"><xref:System.Windows.Forms.ListView> Denetimin döşeme görünümü özelliği yle, grafik ve metinsel bilgiler arasında görsel bir denge sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef11b-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="ef11b-104">Döşeme görünümünde bir öğe için görüntülenen metin bilgileri, ayrıntılar görünümü için tanımlanan sütun bilgileriyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="ef11b-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="ef11b-105">Döşeme <xref:System.Windows.Forms.ListView> görünümü, denetimdeki gruplandırma veya ekleme işareti özellikleriyle birlikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="ef11b-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="ef11b-106">Döşeme görünümü, aşağıdaki resimlerde gösterildiği gibi 32 x 32 piksel simgesi ve birkaç metin satırı kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef11b-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="ef11b-107">![ListView Denetiminde Döşeme Görünümü](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Döşeme görünümü simgeleri ve metin")</span><span class="sxs-lookup"><span data-stu-id="ef11b-107">![Tile View in a ListView Control](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>  

 <span data-ttu-id="ef11b-108">Döşeme görünümünü etkinleştirmek için <xref:System.Windows.Forms.ListView.View%2A> <xref:System.Windows.Forms.View.Tile>özelliği ' niçin ayarla</span><span class="sxs-lookup"><span data-stu-id="ef11b-108">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="ef11b-109"><xref:System.Windows.Forms.ListView.TileSize%2A> Özelliği ayarlayarak kutucukların boyutunu ve <xref:System.Windows.Forms.ListView.Columns%2A> koleksiyonu ayarlayarak kutucukta görüntülenen metin satırlarının sayısını ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef11b-109">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="ef11b-110">Döşeme görünümünü programlı olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ef11b-110">To set tile view programmatically</span></span>  
  
1. <span data-ttu-id="ef11b-111">Denetimin <xref:System.Windows.Forms.View> numaralandırmasını <xref:System.Windows.Forms.ListView> kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef11b-111">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="ef11b-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef11b-112">Example</span></span>  
 <span data-ttu-id="ef11b-113">Aşağıdaki tam kod örneği, üç metin satırı göstermek üzere değiştirilmiş kutucuklarla Kutucuk görünümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef11b-113">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="ef11b-114">Döşeme boyutu, satır kaydırmayı önlemek için ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="ef11b-114">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ef11b-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ef11b-115">Compiling the Code</span></span>  
 <span data-ttu-id="ef11b-116">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="ef11b-116">This example requires:</span></span>  
  
- <span data-ttu-id="ef11b-117">Sistem ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="ef11b-117">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="ef11b-118">Yürütülebilir dosyayla aynı dizinde book.ico adlı bir simge dosyası.</span><span class="sxs-lookup"><span data-stu-id="ef11b-118">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef11b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef11b-119">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="ef11b-120">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="ef11b-120">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="ef11b-121">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ef11b-121">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
