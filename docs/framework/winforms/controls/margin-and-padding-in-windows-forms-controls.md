---
title: Denetimlerde kenar boşluğu ve doldurma
ms.date: 03/30/2017
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
ms.openlocfilehash: 02cabccd0d51a3501a8aafb8733a5273deef6c49
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728565"
---
# <a name="margin-and-padding-in-windows-forms-controls"></a><span data-ttu-id="cc340-102">Windows Forms Denetimlerinde Kenar Boşluğu Bırakma ve Doldurma</span><span class="sxs-lookup"><span data-stu-id="cc340-102">Margin and Padding in Windows Forms Controls</span></span>
<span data-ttu-id="cc340-103">Denetimlerin formunuza kesin olarak yerleştirilmesi birçok uygulama için yüksek önceliktir.</span><span class="sxs-lookup"><span data-stu-id="cc340-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="cc340-104"><xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı, bunu gerçekleştirmek için size çok sayıda düzen özelliği sunar.</span><span class="sxs-lookup"><span data-stu-id="cc340-104">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout features to accomplish this.</span></span> <span data-ttu-id="cc340-105">En önemlileri <xref:System.Windows.Forms.Control.Margin%2A> ve <xref:System.Windows.Forms.Control.Padding%2A> özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="cc340-105">Two of the most important are the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties.</span></span>  
  
 <span data-ttu-id="cc340-106"><xref:System.Windows.Forms.Control.Margin%2A> özelliği, denetimin kenarlıklarından belirli bir uzaklıkta bulunan diğer denetimleri tutan denetimin etrafındaki boşluğu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cc340-106">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="cc340-107"><xref:System.Windows.Forms.Control.Padding%2A> özelliği, denetimin içeriklerini (örneğin, <xref:System.Windows.Forms.Control.Text%2A> özelliğinin değeri) denetimin kenarlıklarından belirtilen mesafeden tutan bir denetimin iç kısmında yer alan alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cc340-107">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="cc340-108">Aşağıdaki çizimde bir denetimdeki <xref:System.Windows.Forms.Control.Padding%2A> ve <xref:System.Windows.Forms.Control.Margin%2A> özellikleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cc340-108">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>  
  
 <span data-ttu-id="cc340-109">![Windows Forms denetimleri için doldurma ve kenar boşluğu](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span><span class="sxs-lookup"><span data-stu-id="cc340-109">![Padding And Margin for Windows Forms Controls](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span></span>  
  
 <span data-ttu-id="cc340-110">Visual Studio 'da bu özellik için tasarım zamanı desteği vardır.</span><span class="sxs-lookup"><span data-stu-id="cc340-110">There is design-time support for this feature in Visual Studio.</span></span> <span data-ttu-id="cc340-111">Ayrıca bkz. [Izlenecek yol: doldurma, kenar boşlukları ve AutoSize özelliği ile Windows Forms denetimleri yerleştirme](windows-forms-controls-padding-autosize.md).</span><span class="sxs-lookup"><span data-stu-id="cc340-111">Also see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](windows-forms-controls-padding-autosize.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc340-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc340-112">See also</span></span>

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
