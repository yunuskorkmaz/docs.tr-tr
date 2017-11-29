---
title: "Nasıl yapılır: Çizilmiş Metinde Sekme Durakları Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e561e8096780301230071e869dac482a6a908a5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a><span data-ttu-id="4efcb-102">Nasıl yapılır: Çizilmiş Metinde Sekme Durakları Ayarlama</span><span class="sxs-lookup"><span data-stu-id="4efcb-102">How to: Set Tab Stops in Drawn Text</span></span>
<span data-ttu-id="4efcb-103">Çağrılarak metin için sekme durakları ayarlayabilirsiniz <xref:System.Drawing.StringFormat.SetTabStops%2A> yöntemi bir <xref:System.Drawing.StringFormat> nesne ve, geçirme <xref:System.Drawing.StringFormat> nesnesini <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4efcb-103">You can set tab stops for text by calling the <xref:System.Drawing.StringFormat.SetTabStops%2A> method of a <xref:System.Drawing.StringFormat> object and then passing that <xref:System.Drawing.StringFormat> object to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4efcb-104"><xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> Sekmesini durdurur çizilmiş metni varolan sekmesini genişletebilirsiniz rağmen ekleme desteklemediğinden durdurur kullanarak mu <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> bayrağı.</span><span class="sxs-lookup"><span data-stu-id="4efcb-104">The <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> does not support adding tab stops to drawn text, although you can expand existing tab stops using the <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> flag.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4efcb-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="4efcb-105">Example</span></span>  
 <span data-ttu-id="4efcb-106">Aşağıdaki örnek, 150, 250 ve 350 sekme durakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4efcb-106">The following example sets tab stops at 150, 250, and 350.</span></span> <span data-ttu-id="4efcb-107">Ardından, kod adları ve test puanları sekmeli listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4efcb-107">Then, the code displays a tabbed list of names and test scores.</span></span>  
  
 <span data-ttu-id="4efcb-108">Aşağıdaki çizimde sekmeli metni gösterir.</span><span class="sxs-lookup"><span data-stu-id="4efcb-108">The following illustration shows the tabbed text.</span></span>  
  
 <span data-ttu-id="4efcb-109">![Yazı tipleri metin](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")</span><span class="sxs-lookup"><span data-stu-id="4efcb-109">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")</span></span>  
  
 <span data-ttu-id="4efcb-110">Aşağıdaki kod iki bağımsız değişken geçirir <xref:System.Drawing.StringFormat.SetTabStops%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4efcb-110">The following code passes two arguments to the <xref:System.Drawing.StringFormat.SetTabStops%2A> method.</span></span> <span data-ttu-id="4efcb-111">İkinci bağımsız değişkeni sekmesini uzaklıkları içeren bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="4efcb-111">The second argument is an array that contains tab offsets.</span></span> <span data-ttu-id="4efcb-112">Geçirilen ilk bağımsız değişken <xref:System.Drawing.StringFormat.SetTabStops%2A> dizideki ilk uzaklığı konumundan 0, sınırlayıcı dikdörtgenini sol kenarı ölçülür gösteren 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="4efcb-112">The first argument passed to <xref:System.Drawing.StringFormat.SetTabStops%2A> is 0, which indicates that the first offset in the array is measured from position 0, the left edge of the bounding rectangle.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4efcb-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="4efcb-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="4efcb-114">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="4efcb-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4efcb-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4efcb-115">See Also</span></span>  
 [<span data-ttu-id="4efcb-116">Yazı tipleri ve metin kullanma</span><span class="sxs-lookup"><span data-stu-id="4efcb-116">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="4efcb-117">Nasıl yapılır: GDI ile metin çizme</span><span class="sxs-lookup"><span data-stu-id="4efcb-117">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
