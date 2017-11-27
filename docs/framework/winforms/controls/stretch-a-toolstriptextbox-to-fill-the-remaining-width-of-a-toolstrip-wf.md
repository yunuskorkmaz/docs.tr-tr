---
title: "Nasıl Yapılır: ToolStripTextBox'nu bir ToolStrip'nin Kalan Genişliğini Kaplayacak Şekilde Genişletme (Windows Forms)"
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
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 213929e52f08fff19eb7641092789501c31648e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a><span data-ttu-id="24acf-102">Nasıl Yapılır: ToolStripTextBox'nu bir ToolStrip'nin Kalan Genişliğini Kaplayacak Şekilde Genişletme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="24acf-102">How to: Stretch a ToolStripTextBox to Fill the Remaining Width of a ToolStrip (Windows Forms)</span></span>
<span data-ttu-id="24acf-103">Ayarladığınızda <xref:System.Windows.Forms.ToolStrip.Stretch%2A> özelliği bir <xref:System.Windows.Forms.ToolStrip> denetimini `true`, denetimin kapsayıcısının uçtan uca doldurur ve öğenin kapsayıcısına göre yeniden boyutlandırır olduğunda yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="24acf-103">When you set the <xref:System.Windows.Forms.ToolStrip.Stretch%2A> property of a <xref:System.Windows.Forms.ToolStrip> control to `true`, the control fills its container from end to end, and resizes when its container resizes.</span></span> <span data-ttu-id="24acf-104">Bu yapılandırmada, öğeyi denetiminde gibi uzatmak yararlı bir <xref:System.Windows.Forms.ToolStripTextBox>, kullanılabilir alanı dolduracak şekilde ve denetimi yeniden boyutlandırır yeniden boyutlandırmak için.</span><span class="sxs-lookup"><span data-stu-id="24acf-104">In this configuration, you may find it useful to stretch an item in the control, such as a <xref:System.Windows.Forms.ToolStripTextBox>, to fill the available space and to resize when the control resizes.</span></span> <span data-ttu-id="24acf-105">Görünüm ve davranış Microsoft® Internet Explorer Adres çubuğuna benzer elde etmek istiyorsanız bu uzatma Örneğin, yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="24acf-105">This stretching is useful, for example, if you want to achieve appearance and behavior similar to the address bar in Microsoft® Internet Explorer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24acf-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="24acf-106">Example</span></span>  
 <span data-ttu-id="24acf-107">Aşağıdaki kod örneğinde türetilmiş bir sınıf sağlar <xref:System.Windows.Forms.ToolStripTextBox> adlı `ToolStripSpringTextBox`.</span><span class="sxs-lookup"><span data-stu-id="24acf-107">The following code example provides a class derived from <xref:System.Windows.Forms.ToolStripTextBox> called `ToolStripSpringTextBox`.</span></span> <span data-ttu-id="24acf-108">Bu sınıf geçersiz kılmaları <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> üst kullanılabilir genişliğini hesaplamak için yöntem <xref:System.Windows.Forms.ToolStrip> diğer tüm öğeleri birleşik genişliğini çıkarılmasıyla denetim.</span><span class="sxs-lookup"><span data-stu-id="24acf-108">This class overrides the <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> method to calculate the available width of the parent <xref:System.Windows.Forms.ToolStrip> control after the combined width of all other items has been subtracted.</span></span> <span data-ttu-id="24acf-109">Bu kod örneği de sağlayan bir <xref:System.Windows.Forms.Form> sınıfı ve bir `Program` yeni davranışı göstermek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="24acf-109">This code example also provides a <xref:System.Windows.Forms.Form> class and a `Program` class to demonstrate the new behavior.</span></span>  
  
 [!code-csharp[ToolStripSpringTextBox#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="24acf-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="24acf-110">Compiling the Code</span></span>  
 <span data-ttu-id="24acf-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="24acf-111">This example requires:</span></span>  
  
-   <span data-ttu-id="24acf-112">Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="24acf-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24acf-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24acf-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripTextBox>  
 <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="24acf-114">ToolStrip denetim mimarisi</span><span class="sxs-lookup"><span data-stu-id="24acf-114">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="24acf-115">Nasıl yapılır: bir StatusStrip içinde Spring özelliğini etkileşimli olarak kullanma</span><span class="sxs-lookup"><span data-stu-id="24acf-115">How to: Use the Spring Property Interactively in a StatusStrip</span></span>](../../../../docs/framework/winforms/controls/how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
