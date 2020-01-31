---
title: "Nasıl yapılır: ToolStripTextBox'nu bir ToolStrip'nin Kalan Genişliğini Kaplayacak Şekilde Genişletme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: c60cc2a377f08a73159f25b2ab5f2812d41f0c10
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742845"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a><span data-ttu-id="e1b71-102">Nasıl Yapılır: ToolStripTextBox'nu bir ToolStrip'nin Kalan Genişliğini Kaplayacak Şekilde Genişletme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e1b71-102">How to: Stretch a ToolStripTextBox to Fill the Remaining Width of a ToolStrip (Windows Forms)</span></span>
<span data-ttu-id="e1b71-103">Bir <xref:System.Windows.Forms.ToolStrip> denetiminin <xref:System.Windows.Forms.ToolStrip.Stretch%2A> özelliğini `true`olarak ayarladığınızda denetim, kapsayıcısını uçtan uca doldurur ve kapsayıcısı yeniden boyutlandırdığında yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e1b71-103">When you set the <xref:System.Windows.Forms.ToolStrip.Stretch%2A> property of a <xref:System.Windows.Forms.ToolStrip> control to `true`, the control fills its container from end to end, and resizes when its container resizes.</span></span> <span data-ttu-id="e1b71-104">Bu yapılandırmada, denetimdeki bir öğeyi (<xref:System.Windows.Forms.ToolStripTextBox>gibi), kullanılabilir alanı dolduracak ve denetimin yeniden boyutlandırılıp boyutlandırılacağını anlamak için yararlı bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1b71-104">In this configuration, you may find it useful to stretch an item in the control, such as a <xref:System.Windows.Forms.ToolStripTextBox>, to fill the available space and to resize when the control resizes.</span></span> <span data-ttu-id="e1b71-105">Bu uzatma, örneğin Microsoft® Internet Explorer 'da adres çubuğuna benzer görünüm ve davranış elde etmek istiyorsanız yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="e1b71-105">This stretching is useful, for example, if you want to achieve appearance and behavior similar to the address bar in Microsoft® Internet Explorer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1b71-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1b71-106">Example</span></span>  
 <span data-ttu-id="e1b71-107">Aşağıdaki kod örneği, `ToolStripSpringTextBox`çağrılan <xref:System.Windows.Forms.ToolStripTextBox> türetilmiş bir sınıf sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1b71-107">The following code example provides a class derived from <xref:System.Windows.Forms.ToolStripTextBox> called `ToolStripSpringTextBox`.</span></span> <span data-ttu-id="e1b71-108">Bu sınıf, diğer tüm öğelerin Birleşik genişliği çıkarılmasıyla sonra üst <xref:System.Windows.Forms.ToolStrip> denetiminin kullanılabilir genişliğini hesaplamak için <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e1b71-108">This class overrides the <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> method to calculate the available width of the parent <xref:System.Windows.Forms.ToolStrip> control after the combined width of all other items has been subtracted.</span></span> <span data-ttu-id="e1b71-109">Bu kod örneği Ayrıca yeni davranışı göstermek için bir <xref:System.Windows.Forms.Form> sınıfı ve bir `Program` sınıfı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1b71-109">This code example also provides a <xref:System.Windows.Forms.Form> class and a `Program` class to demonstrate the new behavior.</span></span>  
  
 [!code-csharp[ToolStripSpringTextBox#00](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e1b71-110">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="e1b71-110">Compiling the Code</span></span>  
 <span data-ttu-id="e1b71-111">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e1b71-111">This example requires:</span></span>  
  
- <span data-ttu-id="e1b71-112">System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="e1b71-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1b71-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1b71-113">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e1b71-114">ToolStrip Denetim, Mimarisi</span><span class="sxs-lookup"><span data-stu-id="e1b71-114">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="e1b71-115">Nasıl yapılır: Bir StatusStrip içinde Spring Özelliğini Etkileşimli Kullanma</span><span class="sxs-lookup"><span data-stu-id="e1b71-115">How to: Use the Spring Property Interactively in a StatusStrip</span></span>](how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
