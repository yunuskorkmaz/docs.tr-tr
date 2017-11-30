---
title: "Windows Forms'ta Güç Yönetimi"
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
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e12f39a63a4f81e6deec4512a4e18ad2bda7e5e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="power-management-in-windows-forms"></a><span data-ttu-id="fe607-102">Windows Forms'ta Güç Yönetimi</span><span class="sxs-lookup"><span data-stu-id="fe607-102">Power Management in Windows Forms</span></span>
<span data-ttu-id="fe607-103">Windows Forms uygulamaları güç yönetimi özellikleri Windows işletim sisteminde yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="fe607-103">Your Windows Forms applications can take advantage of the power management features in the Windows operating system.</span></span> <span data-ttu-id="fe607-104">Uygulamalarınızı, bir bilgisayarın güç durumunu izlemek ve bir durum değişikliği oluştuğunda eylemi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="fe607-104">Your applications can monitor the power status of a computer and take action when a status change occurs.</span></span> <span data-ttu-id="fe607-105">Örneğin, uygulamanızın taşınabilir bir bilgisayarda çalışıyorsa, bilgisayarın pili belirli bir düzey altında düştüğünde, uygulamanızın belirli özelliklerini devre dışı bırakmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe607-105">For example, if your application is running on a portable computer, you might want to disable certain features in your application when the computer's battery charge falls under a certain level.</span></span>  
  
 <span data-ttu-id="fe607-106">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Sağlayan bir <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> güç durumu, bir kullanıcı askıya alır veya işletim sistemi sürdürür gibi veya AC güç durumu veya pil durumu değiştiğinde bir değişiklik olduğunda oluşan olay.</span><span class="sxs-lookup"><span data-stu-id="fe607-106">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provides a <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> event that occurs whenever there is a change in power status, such as when a user suspends or resumes the operating system, or when the AC power status or battery status changes.</span></span> <span data-ttu-id="fe607-107"><xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> Özelliği <xref:System.Windows.Forms.SystemInformation> sınıfı olabilir sorgulamak için geçerli durum, kullanılan aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="fe607-107">The <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property of the <xref:System.Windows.Forms.SystemInformation> class can be used to query for the current status, as shown in the following code example.</span></span>  
  
 [!code-csharp[PowerMode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 <span data-ttu-id="fe607-108">Yanında <xref:System.Windows.Forms.BatteryChargeStatus> numaralandırmalar, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> özelliği de pil kapasitesini belirlemek için numaralandırmalar içerir (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) ve yüzde ücret pil (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span><span class="sxs-lookup"><span data-stu-id="fe607-108">Besides the <xref:System.Windows.Forms.BatteryChargeStatus> enumerations, the <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property also contains enumerations for determining battery capacity (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) and battery charge percentage (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span></span>  
  
 <span data-ttu-id="fe607-109">Kullanabileceğiniz <xref:System.Windows.Forms.Application.SetSuspendState%2A> yöntemi <xref:System.Windows.Forms.Application> bir bilgisayarı hazırda beklemeye veya askıya alma modu.</span><span class="sxs-lookup"><span data-stu-id="fe607-109">You can use the <xref:System.Windows.Forms.Application.SetSuspendState%2A> method of the <xref:System.Windows.Forms.Application> to put a computer into hibernation or suspend mode.</span></span> <span data-ttu-id="fe607-110">Varsa `force` bağımsız değişkeni olarak ayarlanmış `false`, işletim sistemi askıya almak için izin istiyor tüm uygulamalar için bir olay yayın.</span><span class="sxs-lookup"><span data-stu-id="fe607-110">If the `force` argument is set to `false`, the operating system will broadcast an event to all applications requesting permission to suspend.</span></span> <span data-ttu-id="fe607-111">Varsa `disableWakeEvent` bağımsız değişkeni olarak ayarlanmış `true`, tüm uyku modundan çıkarma olayları işletim sistemi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="fe607-111">If the `disableWakeEvent` argument is set to `true`, the operating system disables all wake events.</span></span>  
  
 <span data-ttu-id="fe607-112">Aşağıdaki kod örneği, bir bilgisayarı hazırda bekleme moduna gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fe607-112">The following code example demonstrates how to put a computer into hibernation.</span></span>  
  
 [!code-csharp[PowerMode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="fe607-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe607-113">See Also</span></span>  
 <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>  
 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>  
 <xref:System.Windows.Forms.Application.SetSuspendState%2A>  
 <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
