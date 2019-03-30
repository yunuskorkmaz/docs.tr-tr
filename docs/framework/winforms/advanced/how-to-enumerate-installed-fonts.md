---
title: 'Nasıl yapılır: Yüklü yazı tiplerini numaralandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], enumerating installed
- examples [Windows Forms], fonts
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
ms.openlocfilehash: e56f06d6f7a762a1ef1ff85fa30751ea64f9f14b
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653749"
---
# <a name="how-to-enumerate-installed-fonts"></a><span data-ttu-id="cb30d-102">Nasıl yapılır: Yüklü yazı tiplerini numaralandırma</span><span class="sxs-lookup"><span data-stu-id="cb30d-102">How to: Enumerate Installed Fonts</span></span>
<span data-ttu-id="cb30d-103"><xref:System.Drawing.Text.InstalledFontCollection> Sınıfının devraldığı <xref:System.Drawing.Text.FontCollection> soyut temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="cb30d-103">The <xref:System.Drawing.Text.InstalledFontCollection> class inherits from the <xref:System.Drawing.Text.FontCollection> abstract base class.</span></span> <span data-ttu-id="cb30d-104">Kullanabileceğiniz bir <xref:System.Drawing.Text.InstalledFontCollection> bilgisayarda yüklü yazı tiplerini numaralandırma nesnesi.</span><span class="sxs-lookup"><span data-stu-id="cb30d-104">You can use an <xref:System.Drawing.Text.InstalledFontCollection> object to enumerate the fonts installed on the computer.</span></span> <span data-ttu-id="cb30d-105"><xref:System.Drawing.Text.FontCollection.Families%2A> Özelliği bir <xref:System.Drawing.Text.InstalledFontCollection> nesnesi olan bir dizi <xref:System.Drawing.FontFamily> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="cb30d-105">The <xref:System.Drawing.Text.FontCollection.Families%2A> property of an <xref:System.Drawing.Text.InstalledFontCollection> object is an array of <xref:System.Drawing.FontFamily> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb30d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb30d-106">Example</span></span>  
 <span data-ttu-id="cb30d-107">Aşağıdaki örnek, bilgisayarda yüklü tüm yazı tipi aileleri adlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="cb30d-107">The following example lists the names of all the font families installed on the computer.</span></span> <span data-ttu-id="cb30d-108">Kod alır <xref:System.Drawing.FontFamily.Name%2A> her özellik <xref:System.Drawing.FontFamily> tarafından döndürülen dizi nesnesinde <xref:System.Drawing.Text.FontCollection.Families%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="cb30d-108">The code retrieves the <xref:System.Drawing.FontFamily.Name%2A> property of each <xref:System.Drawing.FontFamily> object in the array returned by the <xref:System.Drawing.Text.FontCollection.Families%2A> property.</span></span> <span data-ttu-id="cb30d-109">Ailesi adları alınır gibi bunlar için form virgülle ayrılmış bir liste bitiştirilir.</span><span class="sxs-lookup"><span data-stu-id="cb30d-109">As the family names are retrieved, they are concatenated to form a comma-separated list.</span></span> <span data-ttu-id="cb30d-110">Ardından <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı virgülle ayrılmış bir liste içinde bir dikdörtgen çizer.</span><span class="sxs-lookup"><span data-stu-id="cb30d-110">Then the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class draws the comma-separated list in a rectangle.</span></span>  
  
 <span data-ttu-id="cb30d-111">Kod örneği çalıştırırsanız, çıktıyı aşağıdaki çizimde gösterilen şuna benzeyecektir:</span><span class="sxs-lookup"><span data-stu-id="cb30d-111">If you run the example code, the output will be similar to that shown in the following illustration:</span></span>  
  
 ![Yüklü yazı tipi aileleri gösteren ekran görüntüsü.](./media/how-to-enumerate-installed-fonts/list-installed-font-families.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cb30d-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="cb30d-113">Compiling the Code</span></span>  
 <span data-ttu-id="cb30d-114">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="cb30d-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span> <span data-ttu-id="cb30d-115">Ayrıca, almalısınız <xref:System.Drawing.Text> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="cb30d-115">In addition, you should import the <xref:System.Drawing.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb30d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb30d-116">See also</span></span>
- [<span data-ttu-id="cb30d-117">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="cb30d-117">Using Fonts and Text</span></span>](using-fonts-and-text.md)
