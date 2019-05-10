---
title: 'Nasıl yapılır: Denetiminize Saydam Arka Plan Verme'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: 8a03d9afec5340cd77af465c4470b7484b8926be
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609710"
---
# <a name="how-to-give-your-control-a-transparent-background"></a><span data-ttu-id="8a146-102">Nasıl yapılır: Denetiminize Saydam Arka Plan Verme</span><span class="sxs-lookup"><span data-stu-id="8a146-102">How to: Give Your Control a Transparent Background</span></span>
<span data-ttu-id="8a146-103">Önceki .NET Framework sürümlerinde ilk ayarlamadan saydam backcolors ayarı denetimleri desteklemekteydi <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemi Formlar'ın Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="8a146-103">In earlier versions of the .NET Framework, controls didn't support setting transparent backcolors without first setting the <xref:System.Windows.Forms.Control.SetStyle%2A> method in the forms's constructor.</span></span> <span data-ttu-id="8a146-104">Geçerli framework sürümü backcolor çoğu denetimleri için ayarlanabilir <xref:System.Drawing.Color.Transparent%2A> içinde **özellikleri** tasarım zamanında ya da formun Oluşturucusu kodunda penceresi.</span><span class="sxs-lookup"><span data-stu-id="8a146-104">In the current framework version, the backcolor for most controls can be set to <xref:System.Drawing.Color.Transparent%2A> in the **Properties** window at design time, or in code in the form's constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a146-105">Windows Forms denetimleri gerçek saydamlık desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8a146-105">Windows Forms controls do not support true transparency.</span></span> <span data-ttu-id="8a146-106">Üst öğesi tarafından saydam bir Windows Forms denetiminin arka planı boyanmadan.</span><span class="sxs-lookup"><span data-stu-id="8a146-106">The background of a transparent Windows Forms control is painted by its parent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a146-107"><xref:System.Windows.Controls.Button> Denetim saydam bir arka plan rengi desteklemiyorsa bile <xref:System.Windows.Forms.ButtonBase.BackColor%2A> özelliği <xref:System.Drawing.Color.Transparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="8a146-107">The <xref:System.Windows.Controls.Button> control doesn't support a transparent backcolor even when the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property is set to <xref:System.Drawing.Color.Transparent%2A>.</span></span>  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a><span data-ttu-id="8a146-108">Saydam bir arka plan rengi, denetim sağlamak için</span><span class="sxs-lookup"><span data-stu-id="8a146-108">To give your control a transparent backcolor</span></span>  
  
- <span data-ttu-id="8a146-109">Özellikler penceresinde <xref:System.Windows.Forms.ButtonBase.BackColor%2A> özelliği ve ayarlayın <xref:System.Drawing.Color.Transparent%2A></span><span class="sxs-lookup"><span data-stu-id="8a146-109">In the Properties window, choose the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property and set it to <xref:System.Drawing.Color.Transparent%2A></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a146-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a146-110">See also</span></span>

- <xref:System.Drawing.Color.FromArgb%2A>
- [<span data-ttu-id="8a146-111">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="8a146-111">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="8a146-112">Yönetilen Grafik Sınıflarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="8a146-112">Using Managed Graphics Classes</span></span>](../advanced/using-managed-graphics-classes.md)
- [<span data-ttu-id="8a146-113">Nasıl yapılır: Donuk ve yarı saydam çizgiler çizme</span><span class="sxs-lookup"><span data-stu-id="8a146-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../advanced/how-to-draw-opaque-and-semitransparent-lines.md)
