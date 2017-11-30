---
title: "Nasıl yapılır: Yüklü Yazı Tiplerini Numaralandırma"
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
- fonts [Windows Forms], enumerating installed
- examples [Windows Forms], fonts
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bca536ed2f3e493e8d50fe8f1a0115327f1d8720
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-enumerate-installed-fonts"></a><span data-ttu-id="c6510-102">Nasıl yapılır: Yüklü Yazı Tiplerini Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="c6510-102">How to: Enumerate Installed Fonts</span></span>
<span data-ttu-id="c6510-103"><xref:System.Drawing.Text.InstalledFontCollection> Sınıfının devraldığı <xref:System.Drawing.Text.FontCollection> soyut taban sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c6510-103">The <xref:System.Drawing.Text.InstalledFontCollection> class inherits from the <xref:System.Drawing.Text.FontCollection> abstract base class.</span></span> <span data-ttu-id="c6510-104">Kullanabileceğiniz bir <xref:System.Drawing.Text.InstalledFontCollection> bilgisayarda yüklü yazı tiplerini numaralandırma nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c6510-104">You can use an <xref:System.Drawing.Text.InstalledFontCollection> object to enumerate the fonts installed on the computer.</span></span> <span data-ttu-id="c6510-105"><xref:System.Drawing.Text.FontCollection.Families%2A> Özelliği bir <xref:System.Drawing.Text.InstalledFontCollection> nesnesi olan bir dizi <xref:System.Drawing.FontFamily> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c6510-105">The <xref:System.Drawing.Text.FontCollection.Families%2A> property of an <xref:System.Drawing.Text.InstalledFontCollection> object is an array of <xref:System.Drawing.FontFamily> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6510-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6510-106">Example</span></span>  
 <span data-ttu-id="c6510-107">Aşağıdaki örnek bilgisayarda yüklü tüm yazı tipi aileleri adlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="c6510-107">The following example lists the names of all the font families installed on the computer.</span></span> <span data-ttu-id="c6510-108">Kodu alır <xref:System.Drawing.FontFamily.Name%2A> her özellik <xref:System.Drawing.FontFamily> nesnesi tarafından döndürülen dizideki <xref:System.Drawing.Text.FontCollection.Families%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c6510-108">The code retrieves the <xref:System.Drawing.FontFamily.Name%2A> property of each <xref:System.Drawing.FontFamily> object in the array returned by the <xref:System.Drawing.Text.FontCollection.Families%2A> property.</span></span> <span data-ttu-id="c6510-109">Aile adları alınır gibi bunlar için form virgülle ayrılmış listesini birleşir.</span><span class="sxs-lookup"><span data-stu-id="c6510-109">As the family names are retrieved, they are concatenated to form a comma-separated list.</span></span> <span data-ttu-id="c6510-110">Ardından <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics> dikdörtgene sınıfı çizer virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="c6510-110">Then the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class draws the comma-separated list in a rectangle.</span></span>  
  
 <span data-ttu-id="c6510-111">Kod örneği çalıştırırsanız, çıktı aşağıdaki çizimde gösterilen benzer olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c6510-111">If you run the example code, the output will be similar to that shown in the following illustration.</span></span>  
  
 <span data-ttu-id="c6510-112">![Yazı tipleri yüklü](../../../../docs/framework/winforms/advanced/media/csfontstext6.png "csfontstext6")</span><span class="sxs-lookup"><span data-stu-id="c6510-112">![Installed Fonts](../../../../docs/framework/winforms/advanced/media/csfontstext6.png "csfontstext6")</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c6510-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c6510-113">Compiling the Code</span></span>  
 <span data-ttu-id="c6510-114">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="c6510-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span> <span data-ttu-id="c6510-115">Ayrıca, almalısınız <xref:System.Drawing.Text> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="c6510-115">In addition, you should import the <xref:System.Drawing.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6510-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6510-116">See Also</span></span>  
 [<span data-ttu-id="c6510-117">Yazı tipleri ve metin kullanma</span><span class="sxs-lookup"><span data-stu-id="c6510-117">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
