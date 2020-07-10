---
title: Denetimlerde kenar boşluğu ve doldurma
description: Kenar boşluğu ve doldurma özellikleriyle Windows form denetimlerinde kenar boşlukları ve doldurma ekleme hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
ms.openlocfilehash: 4279f39bb4f89fbda8be472f49c8e60853abcac6
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174490"
---
# <a name="margin-and-padding-in-windows-forms-controls"></a><span data-ttu-id="5774c-103">Windows Forms Denetimlerinde Kenar Boşluğu Bırakma ve Doldurma</span><span class="sxs-lookup"><span data-stu-id="5774c-103">Margin and Padding in Windows Forms Controls</span></span>
<span data-ttu-id="5774c-104">Denetimlerin formunuza kesin olarak yerleştirilmesi birçok uygulama için yüksek önceliktir.</span><span class="sxs-lookup"><span data-stu-id="5774c-104">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="5774c-105"><xref:System.Windows.Forms?displayProperty=nameWithType>Ad alanı, bunu gerçekleştirmek için size birçok düzen özelliği sunar.</span><span class="sxs-lookup"><span data-stu-id="5774c-105">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout features to accomplish this.</span></span> <span data-ttu-id="5774c-106">En önemlisi ikisi <xref:System.Windows.Forms.Control.Margin%2A> ve <xref:System.Windows.Forms.Control.Padding%2A> özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="5774c-106">Two of the most important are the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties.</span></span>  
  
 <span data-ttu-id="5774c-107">Özelliği, denetimin <xref:System.Windows.Forms.Control.Margin%2A> kenarlıklarından belirli bir uzaklıkta bulunan diğer denetimleri tutan denetimin etrafındaki boşluğu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5774c-107">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="5774c-108">Özelliği, denetimin <xref:System.Windows.Forms.Control.Padding%2A> içeriklerini (örneğin, <xref:System.Windows.Forms.Control.Text%2A> özelliğinin değeri) denetimin kenarlıklarından belirtilen uzaklıktan tutup denetimin içeriğini tutan bir denetimin iç kısmında yer alan alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5774c-108">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="5774c-109">Aşağıdaki çizim, <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Control.Margin%2A> bir denetimdeki ve özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5774c-109">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>  
  
 <span data-ttu-id="5774c-110">![Windows Forms denetimleri için doldurma ve kenar boşluğu](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span><span class="sxs-lookup"><span data-stu-id="5774c-110">![Padding And Margin for Windows Forms Controls](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span></span>  
  
 <span data-ttu-id="5774c-111">Visual Studio 'da bu özellik için tasarım zamanı desteği vardır.</span><span class="sxs-lookup"><span data-stu-id="5774c-111">There is design-time support for this feature in Visual Studio.</span></span> <span data-ttu-id="5774c-112">Ayrıca bkz. [Izlenecek yol: doldurma, kenar boşlukları ve AutoSize özelliği ile Windows Forms denetimleri yerleştirme](windows-forms-controls-padding-autosize.md).</span><span class="sxs-lookup"><span data-stu-id="5774c-112">Also see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](windows-forms-controls-padding-autosize.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5774c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5774c-113">See also</span></span>

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
