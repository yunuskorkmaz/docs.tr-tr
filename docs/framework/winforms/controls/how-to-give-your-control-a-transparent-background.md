---
title: 'Nasıl yapılır: Denetiminize Saydam Arka Plan Verme'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: a82807ea3873b2217d1f05f6c720c599ea79abdd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966646"
---
# <a name="how-to-give-your-control-a-transparent-background"></a><span data-ttu-id="c4280-102">Nasıl yapılır: Denetiminize Saydam Arka Plan Verme</span><span class="sxs-lookup"><span data-stu-id="c4280-102">How to: Give Your Control a Transparent Background</span></span>
<span data-ttu-id="c4280-103">.NET Framework önceki sürümlerinde denetimler, önce formların oluşturucusunda <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemi ayarlamadan saydam geri renklerin ayarlanmasını desteklemezler.</span><span class="sxs-lookup"><span data-stu-id="c4280-103">In earlier versions of the .NET Framework, controls didn't support setting transparent backcolors without first setting the <xref:System.Windows.Forms.Control.SetStyle%2A> method in the forms's constructor.</span></span> <span data-ttu-id="c4280-104">Geçerli Framework sürümünde, çoğu denetim için BackColor, tasarım zamanında **Özellikler** penceresinde veya formun <xref:System.Drawing.Color.Transparent%2A> oluşturucusunda kodda olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="c4280-104">In the current framework version, the backcolor for most controls can be set to <xref:System.Drawing.Color.Transparent%2A> in the **Properties** window at design time, or in code in the form's constructor.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4280-105">Windows Forms denetimleri gerçek saydamlığı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c4280-105">Windows Forms controls do not support true transparency.</span></span> <span data-ttu-id="c4280-106">Saydam Windows Forms denetiminin arka planı üst öğesi tarafından boyanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c4280-106">The background of a transparent Windows Forms control is painted by its parent.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4280-107">Denetim, <xref:System.Windows.Forms.ButtonBase.BackColor%2A> özelliği olarak<xref:System.Drawing.Color.Transparent%2A>ayarlanmış olsa bile saydam BackColor 'ı desteklemez. <xref:System.Windows.Controls.Button></span><span class="sxs-lookup"><span data-stu-id="c4280-107">The <xref:System.Windows.Controls.Button> control doesn't support a transparent backcolor even when the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property is set to <xref:System.Drawing.Color.Transparent%2A>.</span></span>  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a><span data-ttu-id="c4280-108">Denetimine saydam bir BackColor sağlamak için</span><span class="sxs-lookup"><span data-stu-id="c4280-108">To give your control a transparent backcolor</span></span>  
  
- <span data-ttu-id="c4280-109">Özellikler penceresi, <xref:System.Windows.Forms.ButtonBase.BackColor%2A> özelliğini seçin ve<xref:System.Drawing.Color.Transparent%2A></span><span class="sxs-lookup"><span data-stu-id="c4280-109">In the Properties window, choose the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property and set it to <xref:System.Drawing.Color.Transparent%2A></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4280-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4280-110">See also</span></span>

- <xref:System.Drawing.Color.FromArgb%2A>
- [<span data-ttu-id="c4280-111">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="c4280-111">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="c4280-112">Yönetilen Grafik Sınıflarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="c4280-112">Using Managed Graphics Classes</span></span>](../advanced/using-managed-graphics-classes.md)
- [<span data-ttu-id="c4280-113">Nasıl yapılır: Donuk ve yarı saydam çizgiler çizme</span><span class="sxs-lookup"><span data-stu-id="c4280-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../advanced/how-to-draw-opaque-and-semitransparent-lines.md)
