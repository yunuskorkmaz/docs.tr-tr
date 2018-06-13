---
title: 'Nasıl yapılır: Metinle Düzgünleştirme Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
ms.openlocfilehash: 842c1fb0b73533fd2e87474b9e8cfa282eba2a70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523116"
---
# <a name="how-to-use-antialiasing-with-text"></a><span data-ttu-id="09e46-102">Nasıl yapılır: Metinle Düzgünleştirme Kullanma</span><span class="sxs-lookup"><span data-stu-id="09e46-102">How to: Use Antialiasing with Text</span></span>
<span data-ttu-id="09e46-103">*Düzgünleştirme* çizilmiş grafik ve bunların görünümünü ve okunabilirliğini artırmak için metin çentikli kenarları düzgünleştirme başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="09e46-103">*Antialiasing* refers to the smoothing of jagged edges of drawn graphics and text to improve their appearance or readability.</span></span> <span data-ttu-id="09e46-104">Yönetilen ile [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sınıfları, daha düşük Kalite metin yanı sıra, yüksek kaliteli antialiased metin işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09e46-104">With the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes, you can render high quality antialiased text, as well as lower quality text.</span></span> <span data-ttu-id="09e46-105">Genellikle, daha yüksek kaliteli işleme alt kalite işleme'den daha fazla işleme zaman alır.</span><span class="sxs-lookup"><span data-stu-id="09e46-105">Typically, higher quality rendering takes more processing time than lower quality rendering.</span></span> <span data-ttu-id="09e46-106">Metin kalite düzeyini ayarlamak için ayarlayın <xref:System.Drawing.Graphics.TextRenderingHint%2A> özelliği bir <xref:System.Drawing.Graphics> öğelerinden birine <xref:System.Drawing.Text.TextRenderingHint> numaralandırması</span><span class="sxs-lookup"><span data-stu-id="09e46-106">To set the text quality level, set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property of a <xref:System.Drawing.Graphics> to one of the elements of the <xref:System.Drawing.Text.TextRenderingHint> enumeration</span></span>  
  
## <a name="example"></a><span data-ttu-id="09e46-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="09e46-107">Example</span></span>  
 <span data-ttu-id="09e46-108">Aşağıdaki kod örneği iki farklı kalite ayarlarını metinle çizer.</span><span class="sxs-lookup"><span data-stu-id="09e46-108">The following code example draws text with two different quality settings.</span></span>  
  
 <span data-ttu-id="09e46-109">Aşağıdaki çizimde örnek kod cod çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="09e46-109">The following illustration shows the output of the cod example code.</span></span>  
  
 <span data-ttu-id="09e46-110">![Yazı tipleri metin](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")</span><span class="sxs-lookup"><span data-stu-id="09e46-110">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="09e46-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="09e46-111">Compiling the Code</span></span>  
 <span data-ttu-id="09e46-112">Önceki kod örneğinde Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="09e46-112">The preceding code example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e46-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="09e46-113">See Also</span></span>  
 [<span data-ttu-id="09e46-114">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="09e46-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
