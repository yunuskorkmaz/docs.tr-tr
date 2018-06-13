---
title: 'Nasıl yapılır: Denetiminize Saydam Arka Plan Verme'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: ad814c9179fd33955fe4df2666f8a47606bfbff0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531823"
---
# <a name="how-to-give-your-control-a-transparent-background"></a><span data-ttu-id="e1a06-102">Nasıl yapılır: Denetiminize Saydam Arka Plan Verme</span><span class="sxs-lookup"><span data-stu-id="e1a06-102">How to: Give Your Control a Transparent Background</span></span>
<span data-ttu-id="e1a06-103">Önceki sürümlerde .NET Framework'ün, ilk ayarlamadan saydam backcolors ayarlama denetimleri desteklemekteydi <xref:System.Windows.Forms.Control.SetStyle%2A> formları 's Oluşturucusu yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e1a06-103">In earlier versions of the .NET Framework, controls didn't support setting transparent backcolors without first setting the <xref:System.Windows.Forms.Control.SetStyle%2A> method in the forms's constructor.</span></span> <span data-ttu-id="e1a06-104">Geçerli framework sürümünde çoğu denetimleri için backcolor ayarlanabilir <xref:System.Drawing.Color.Transparent%2A> içinde **özellikleri** penceresi tasarım zamanında ya da formun oluşturucuda kod.</span><span class="sxs-lookup"><span data-stu-id="e1a06-104">In the current framework version, the backcolor for most controls can be set to <xref:System.Drawing.Color.Transparent%2A> in the **Properties** window at design time, or in code in the form's constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1a06-105">Windows Forms denetimleri true saydamlığı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e1a06-105">Windows Forms controls do not support true transparency.</span></span> <span data-ttu-id="e1a06-106">Arka plan saydam bir Windows Forms denetiminin üst tarafından boyanır.</span><span class="sxs-lookup"><span data-stu-id="e1a06-106">The background of a transparent Windows Forms control is painted by its parent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1a06-107"><xref:System.Windows.Controls.Button> Denetim saydam backcolor desteklemiyor bile <xref:System.Windows.Forms.ButtonBase.BackColor%2A> özelliği ayarlanmış <xref:System.Drawing.Color.Transparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="e1a06-107">The <xref:System.Windows.Controls.Button> control doesn't support a transparent backcolor even when the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property is set to <xref:System.Drawing.Color.Transparent%2A>.</span></span>  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a><span data-ttu-id="e1a06-108">Saydam arka plan rengi, denetim sağlamak için</span><span class="sxs-lookup"><span data-stu-id="e1a06-108">To give your control a transparent backcolor</span></span>  
  
-   <span data-ttu-id="e1a06-109">Özellikler penceresinde seçin <xref:System.Windows.Forms.ButtonBase.BackColor%2A> özelliği ve ayarlayın <xref:System.Drawing.Color.Transparent%2A></span><span class="sxs-lookup"><span data-stu-id="e1a06-109">In the Properties window, choose the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property and set it to <xref:System.Drawing.Color.Transparent%2A></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1a06-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e1a06-110">See Also</span></span>  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [<span data-ttu-id="e1a06-111">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="e1a06-111">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="e1a06-112">Yönetilen Grafik Sınıflarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="e1a06-112">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 [<span data-ttu-id="e1a06-113">Nasıl yapılır: Donuk ve Yarı Saydam Çizgiler Çizme</span><span class="sxs-lookup"><span data-stu-id="e1a06-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
