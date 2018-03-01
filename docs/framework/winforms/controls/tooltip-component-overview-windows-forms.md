---
title: "ToolTip Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fce1cb5750197e52461b4883f1238325fa10fc5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="tooltip-component-overview-windows-forms"></a><span data-ttu-id="40dd7-102">ToolTip Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="40dd7-102">ToolTip Component Overview (Windows Forms)</span></span>
<span data-ttu-id="40dd7-103">Windows Forms <xref:System.Windows.Forms.ToolTip> bileşen kullanıcı denetimleri işaret ettiğinde metin görüntüler.</span><span class="sxs-lookup"><span data-stu-id="40dd7-103">The Windows Forms <xref:System.Windows.Forms.ToolTip> component displays text when the user points at controls.</span></span> <span data-ttu-id="40dd7-104">Bir araç ipucu herhangi bir denetimle ilişkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="40dd7-104">A ToolTip can be associated with any control.</span></span> <span data-ttu-id="40dd7-105">Bu bileşen örnek kullanımını: bir form üzerinde alanı kaydetmek için küçük bir simge bir düğme görüntüleyebilir ve düğmenin işlevi açıklamak için bir araç ipucunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="40dd7-105">An example use of this component: to save space on a form, you can display a small icon on a button and use a ToolTip to explain the button's function.</span></span>  
  
## <a name="working-with-the-tooltip-component"></a><span data-ttu-id="40dd7-106">ToolTip bileşeni ile çalışma</span><span class="sxs-lookup"><span data-stu-id="40dd7-106">Working with the ToolTip Component</span></span>  
 <span data-ttu-id="40dd7-107">A <xref:System.Windows.Forms.ToolTip> bileşen sağlayan bir `ToolTip` denetimlere birden çok Windows Form veya diğer kapsayıcı özelliği.</span><span class="sxs-lookup"><span data-stu-id="40dd7-107">A <xref:System.Windows.Forms.ToolTip> component provides a `ToolTip` property to multiple controls on a Windows Form or other container.</span></span> <span data-ttu-id="40dd7-108">Örneğin, biri yerleştirileceği <xref:System.Windows.Forms.ToolTip> bileşen bir form üzerinde "adını buraya yazın" görüntüleyebilir bir <xref:System.Windows.Forms.TextBox> denetlemek ve "değişiklikleri kaydetmek için burayı tıklatın" bir <xref:System.Windows.Forms.Button> denetim.</span><span class="sxs-lookup"><span data-stu-id="40dd7-108">For example, if you place one <xref:System.Windows.Forms.ToolTip> component on a form, you can display "Type your name here" for a <xref:System.Windows.Forms.TextBox> control and "Click here to save changes" for a <xref:System.Windows.Forms.Button> control.</span></span>  
  
 <span data-ttu-id="40dd7-109">Anahtar yöntemleri <xref:System.Windows.Forms.ToolTip> bileşeni olan <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> ve <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>.</span><span class="sxs-lookup"><span data-stu-id="40dd7-109">The key methods of the <xref:System.Windows.Forms.ToolTip> component are <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> and <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>.</span></span> <span data-ttu-id="40dd7-110">Kullanabileceğiniz <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> görüntülenen denetimler için araç ipuçları ayarlamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="40dd7-110">You can use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method to set the ToolTips displayed for controls.</span></span> <span data-ttu-id="40dd7-111">Daha fazla bilgi için bkz: [nasıl yapılır: tasarım zamanında Windows formundaki denetimler için araç ipuçları kümesi](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="40dd7-111">For more information, see [How to: Set ToolTips for Controls on a Windows Form at Design Time](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md).</span></span> <span data-ttu-id="40dd7-112">Anahtar Özellikler <xref:System.Windows.Forms.ToolTip.Active%2A>, hangi ayarlanmalıdır `true` görünmesi araç ipucu için ve <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, araç ipucu dize gösterilen süreyi ayarlar, ne kadar süreyle kullanıcı işaret etmelidir görünmesi araç ipucu denetimi sırasında ve onu uzun nasıl Sonraki araç ipucu windows görünmesi alır.</span><span class="sxs-lookup"><span data-stu-id="40dd7-112">The key properties are <xref:System.Windows.Forms.ToolTip.Active%2A>, which must be set to `true` for the ToolTip to appear, and <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, which sets the length of time that the ToolTip string is shown, how long the user must point at the control for the ToolTip to appear, and how long it takes for subsequent ToolTip windows to appear.</span></span> <span data-ttu-id="40dd7-113">Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms ToolTip bileşeninin gecikmesini değiştirme](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).</span><span class="sxs-lookup"><span data-stu-id="40dd7-113">For more information, see [How to: Change the Delay of the Windows Forms ToolTip Component](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40dd7-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40dd7-114">See Also</span></span>  
 <xref:System.Windows.Forms.ToolTip>  
 [<span data-ttu-id="40dd7-115">Nasıl yapılır: Tasarım Zamanında Windows Formundaki Denetimler için ToolTips Ayarlama</span><span class="sxs-lookup"><span data-stu-id="40dd7-115">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [<span data-ttu-id="40dd7-116">Nasıl yapılır: Windows Forms ToolTip Bileşeninin Gecikmesini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="40dd7-116">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
