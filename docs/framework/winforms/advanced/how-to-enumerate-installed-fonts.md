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
ms.openlocfilehash: 0124d2bdd8b9c60dc2bf2508348044d76a2c7eb4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602240"
---
# <a name="how-to-enumerate-installed-fonts"></a><span data-ttu-id="faa51-102">Nasıl yapılır: Yüklü yazı tiplerini numaralandırma</span><span class="sxs-lookup"><span data-stu-id="faa51-102">How to: Enumerate Installed Fonts</span></span>
<span data-ttu-id="faa51-103"><xref:System.Drawing.Text.InstalledFontCollection> Sınıfının devraldığı <xref:System.Drawing.Text.FontCollection> soyut temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="faa51-103">The <xref:System.Drawing.Text.InstalledFontCollection> class inherits from the <xref:System.Drawing.Text.FontCollection> abstract base class.</span></span> <span data-ttu-id="faa51-104">Kullanabileceğiniz bir <xref:System.Drawing.Text.InstalledFontCollection> bilgisayarda yüklü yazı tiplerini numaralandırma nesnesi.</span><span class="sxs-lookup"><span data-stu-id="faa51-104">You can use an <xref:System.Drawing.Text.InstalledFontCollection> object to enumerate the fonts installed on the computer.</span></span> <span data-ttu-id="faa51-105"><xref:System.Drawing.Text.FontCollection.Families%2A> Özelliği bir <xref:System.Drawing.Text.InstalledFontCollection> nesnesi olan bir dizi <xref:System.Drawing.FontFamily> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="faa51-105">The <xref:System.Drawing.Text.FontCollection.Families%2A> property of an <xref:System.Drawing.Text.InstalledFontCollection> object is an array of <xref:System.Drawing.FontFamily> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="faa51-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="faa51-106">Example</span></span>  
 <span data-ttu-id="faa51-107">Aşağıdaki örnek, bilgisayarda yüklü tüm yazı tipi aileleri adlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="faa51-107">The following example lists the names of all the font families installed on the computer.</span></span> <span data-ttu-id="faa51-108">Kod alır <xref:System.Drawing.FontFamily.Name%2A> her özellik <xref:System.Drawing.FontFamily> tarafından döndürülen dizi nesnesinde <xref:System.Drawing.Text.FontCollection.Families%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="faa51-108">The code retrieves the <xref:System.Drawing.FontFamily.Name%2A> property of each <xref:System.Drawing.FontFamily> object in the array returned by the <xref:System.Drawing.Text.FontCollection.Families%2A> property.</span></span> <span data-ttu-id="faa51-109">Ailesi adları alınır gibi bunlar için form virgülle ayrılmış bir liste bitiştirilir.</span><span class="sxs-lookup"><span data-stu-id="faa51-109">As the family names are retrieved, they are concatenated to form a comma-separated list.</span></span> <span data-ttu-id="faa51-110">Ardından <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı virgülle ayrılmış bir liste içinde bir dikdörtgen çizer.</span><span class="sxs-lookup"><span data-stu-id="faa51-110">Then the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class draws the comma-separated list in a rectangle.</span></span>  
  
 <span data-ttu-id="faa51-111">Kod örneği çalıştırırsanız, çıktıyı aşağıdaki çizimde gösterilen şuna benzer olacaktır.</span><span class="sxs-lookup"><span data-stu-id="faa51-111">If you run the example code, the output will be similar to that shown in the following illustration.</span></span>  
  
 <span data-ttu-id="faa51-112">![Yazı tipi yüklü](../../../../docs/framework/winforms/advanced/media/csfontstext6.png "csfontstext6")</span><span class="sxs-lookup"><span data-stu-id="faa51-112">![Installed Fonts](../../../../docs/framework/winforms/advanced/media/csfontstext6.png "csfontstext6")</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="faa51-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="faa51-113">Compiling the Code</span></span>  
 <span data-ttu-id="faa51-114">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="faa51-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span> <span data-ttu-id="faa51-115">Ayrıca, almalısınız <xref:System.Drawing.Text> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="faa51-115">In addition, you should import the <xref:System.Drawing.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faa51-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="faa51-116">See also</span></span>
- [<span data-ttu-id="faa51-117">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="faa51-117">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
