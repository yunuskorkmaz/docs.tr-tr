---
title: Windows Forms Denetimlerinde Kenar Boşluğu Bırakma ve Doldurma
ms.date: 03/30/2017
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
ms.openlocfilehash: bf1f88f6efcedd740bff92dda391470391f16ce5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094063"
---
# <a name="margin-and-padding-in-windows-forms-controls"></a><span data-ttu-id="dbfe5-102">Windows Forms Denetimlerinde Kenar Boşluğu Bırakma ve Doldurma</span><span class="sxs-lookup"><span data-stu-id="dbfe5-102">Margin and Padding in Windows Forms Controls</span></span>
<span data-ttu-id="dbfe5-103">Formunuzdaki denetimleri kesin yerleşimini birçok uygulama için yüksek öncelik taşır.</span><span class="sxs-lookup"><span data-stu-id="dbfe5-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="dbfe5-104"><xref:System.Windows.Forms?displayProperty=nameWithType> Ad alanı bunu gerçekleştirmek için çok sayıda düzen özelliklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbfe5-104">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout features to accomplish this.</span></span> <span data-ttu-id="dbfe5-105">En önemli iki <xref:System.Windows.Forms.Control.Margin%2A> ve <xref:System.Windows.Forms.Control.Padding%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="dbfe5-105">Two of the most important are the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties.</span></span>  
  
 <span data-ttu-id="dbfe5-106"><xref:System.Windows.Forms.Control.Margin%2A> Tutar diğer denetimleri belirtilen bir denetimin kenarlık uzaklıkta çevresindeki boşluk özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dbfe5-106">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="dbfe5-107"><xref:System.Windows.Forms.Control.Padding%2A> Özelliği, denetimin içeriği tutan bir denetimin iç alanı tanımlar (örneğin, değerini kendi <xref:System.Windows.Forms.Control.Text%2A> özelliği) belirtilen bir denetimin kenarlık uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="dbfe5-107">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="dbfe5-108">Aşağıdaki çizimde gösterildiği <xref:System.Windows.Forms.Control.Padding%2A> ve <xref:System.Windows.Forms.Control.Margin%2A> denetim özellikleri.</span><span class="sxs-lookup"><span data-stu-id="dbfe5-108">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>  
  
 <span data-ttu-id="dbfe5-109">![Doldurma ve kenar boşlukları için Windows Forms denetimlerine](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span><span class="sxs-lookup"><span data-stu-id="dbfe5-109">![Padding And Margin for Windows Forms Controls](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span></span>  
  
 <span data-ttu-id="dbfe5-110">Visual Studio'da bu özellik için tasarım zamanı desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="dbfe5-110">There is design-time support for this feature in Visual Studio.</span></span> <span data-ttu-id="dbfe5-111">Ayrıca bkz: [izlenecek yol: Yerleştirme Windows Forms denetimleri doldurma, kenar boşlukları ve AutoSize özelliği ile](windows-forms-controls-padding-autosize.md).</span><span class="sxs-lookup"><span data-stu-id="dbfe5-111">Also see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](windows-forms-controls-padding-autosize.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbfe5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbfe5-112">See also</span></span>

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
