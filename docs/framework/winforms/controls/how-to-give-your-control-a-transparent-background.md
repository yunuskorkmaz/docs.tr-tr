---
title: "Nasıl yapılır: Denetiminize Saydam Arka Plan Verme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a5ec2c353a960626c54c05009393bcd80dac1b38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-give-your-control-a-transparent-background"></a><span data-ttu-id="649bc-102">Nasıl yapılır: Denetiminize Saydam Arka Plan Verme</span><span class="sxs-lookup"><span data-stu-id="649bc-102">How to: Give Your Control a Transparent Background</span></span>
<span data-ttu-id="649bc-103">Önceki sürümlerde .NET Framework'ün, ilk ayarlamadan saydam backcolors ayarlama denetimleri desteklemekteydi <xref:System.Windows.Forms.Control.SetStyle%2A> formları 's Oluşturucusu yöntemi.</span><span class="sxs-lookup"><span data-stu-id="649bc-103">In earlier versions of the .NET Framework, controls didn't support setting transparent backcolors without first setting the <xref:System.Windows.Forms.Control.SetStyle%2A> method in the forms's constructor.</span></span> <span data-ttu-id="649bc-104">Geçerli framework sürümünde çoğu denetimleri için backcolor ayarlanabilir <xref:System.Drawing.Color.Transparent%2A> içinde **özellikleri** penceresi tasarım zamanında ya da formun oluşturucuda kod.</span><span class="sxs-lookup"><span data-stu-id="649bc-104">In the current framework version, the backcolor for most controls can be set to <xref:System.Drawing.Color.Transparent%2A> in the **Properties** window at design time, or in code in the form's constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="649bc-105">Windows Forms denetimleri true saydamlığı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="649bc-105">Windows Forms controls do not support true transparency.</span></span> <span data-ttu-id="649bc-106">Arka plan saydam bir Windows Forms denetiminin üst tarafından boyanır.</span><span class="sxs-lookup"><span data-stu-id="649bc-106">The background of a transparent Windows Forms control is painted by its parent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="649bc-107"><xref:System.Windows.Controls.Button> Denetim saydam backcolor desteklemiyor bile <xref:System.Windows.Forms.ButtonBase.BackColor%2A> özelliği ayarlanmış <xref:System.Drawing.Color.Transparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="649bc-107">The <xref:System.Windows.Controls.Button> control doesn't support a transparent backcolor even when the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property is set to <xref:System.Drawing.Color.Transparent%2A>.</span></span>  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a><span data-ttu-id="649bc-108">Saydam arka plan rengi, denetim sağlamak için</span><span class="sxs-lookup"><span data-stu-id="649bc-108">To give your control a transparent backcolor</span></span>  
  
-   <span data-ttu-id="649bc-109">Özellikler penceresinde seçin <xref:System.Windows.Forms.ButtonBase.BackColor%2A> özelliği ve ayarlayın<xref:System.Drawing.Color.Transparent%2A></span><span class="sxs-lookup"><span data-stu-id="649bc-109">In the Properties window, choose the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property and set it to <xref:System.Drawing.Color.Transparent%2A></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="649bc-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="649bc-110">See Also</span></span>  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [<span data-ttu-id="649bc-111">Özel Windows Forms denetimleri .NET Framework ile geliştirme</span><span class="sxs-lookup"><span data-stu-id="649bc-111">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="649bc-112">Yönetilen grafik sınıflarını kullanma</span><span class="sxs-lookup"><span data-stu-id="649bc-112">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 [<span data-ttu-id="649bc-113">Nasıl yapılır: donuk ve yarı saydam çizgiler çizme</span><span class="sxs-lookup"><span data-stu-id="649bc-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
