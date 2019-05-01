---
title: "Nasıl yapılır: Bir toolstrip'nin kalan genişliğini (Windows Forms) doldurmak için"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: 707fd2e470a9be1d61d2878eeff845b3cad270db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971931"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a><span data-ttu-id="88f7a-102">Nasıl yapılır: Bir toolstrip'nin kalan genişliğini (Windows Forms) doldurmak için</span><span class="sxs-lookup"><span data-stu-id="88f7a-102">How to: Stretch a ToolStripTextBox to Fill the Remaining Width of a ToolStrip (Windows Forms)</span></span>
<span data-ttu-id="88f7a-103">Ayarladığınızda <xref:System.Windows.Forms.ToolStrip.Stretch%2A> özelliği bir <xref:System.Windows.Forms.ToolStrip> denetimini `true`, denetimi uçtan uca, kapsayıcı doldurur ve kapsayıcısı boyutlandırdığında yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="88f7a-103">When you set the <xref:System.Windows.Forms.ToolStrip.Stretch%2A> property of a <xref:System.Windows.Forms.ToolStrip> control to `true`, the control fills its container from end to end, and resizes when its container resizes.</span></span> <span data-ttu-id="88f7a-104">Bu yapılandırmada, bir öğesi denetiminde gibi esnetme yararlı bir <xref:System.Windows.Forms.ToolStripTextBox>kullanılabilir alanı dolduracak şekilde ve denetim boyutlandırdığında yeniden boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88f7a-104">In this configuration, you may find it useful to stretch an item in the control, such as a <xref:System.Windows.Forms.ToolStripTextBox>, to fill the available space and to resize when the control resizes.</span></span> <span data-ttu-id="88f7a-105">Görünümünü ve davranışını Microsoft® Internet Explorer Adres çubuğuna benzer elde etmek istiyorsanız bu uzatma gibi yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="88f7a-105">This stretching is useful, for example, if you want to achieve appearance and behavior similar to the address bar in Microsoft® Internet Explorer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88f7a-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="88f7a-106">Example</span></span>  
 <span data-ttu-id="88f7a-107">Aşağıdaki kod örneği, türetilen bir sınıf sağlar <xref:System.Windows.Forms.ToolStripTextBox> adlı `ToolStripSpringTextBox`.</span><span class="sxs-lookup"><span data-stu-id="88f7a-107">The following code example provides a class derived from <xref:System.Windows.Forms.ToolStripTextBox> called `ToolStripSpringTextBox`.</span></span> <span data-ttu-id="88f7a-108">Bu sınıf geçersiz kılmalar <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> üst kullanılabilir genişliğini hesaplamak için gereken yöntemini <xref:System.Windows.Forms.ToolStrip> diğer tüm öğelerin birleşik genişliğini çıkarılmasıyla denetim.</span><span class="sxs-lookup"><span data-stu-id="88f7a-108">This class overrides the <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> method to calculate the available width of the parent <xref:System.Windows.Forms.ToolStrip> control after the combined width of all other items has been subtracted.</span></span> <span data-ttu-id="88f7a-109">Bu kod örneği de sağlayan bir <xref:System.Windows.Forms.Form> sınıfı ve bir `Program` yeni davranış göstermek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="88f7a-109">This code example also provides a <xref:System.Windows.Forms.Form> class and a `Program` class to demonstrate the new behavior.</span></span>  
  
 [!code-csharp[ToolStripSpringTextBox#00](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="88f7a-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="88f7a-110">Compiling the Code</span></span>  
 <span data-ttu-id="88f7a-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="88f7a-111">This example requires:</span></span>  
  
- <span data-ttu-id="88f7a-112">Sistem, System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="88f7a-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88f7a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88f7a-113">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [<span data-ttu-id="88f7a-114">ToolStrip Denetim, Mimarisi</span><span class="sxs-lookup"><span data-stu-id="88f7a-114">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="88f7a-115">Nasıl yapılır: Bir StatusStrip içinde Spring özelliğini etkileşimli kullanma</span><span class="sxs-lookup"><span data-stu-id="88f7a-115">How to: Use the Spring Property Interactively in a StatusStrip</span></span>](how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
