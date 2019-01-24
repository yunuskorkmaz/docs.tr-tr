---
title: Windows Forms'ta Güç Yönetimi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
ms.openlocfilehash: 172472cf9a2e1bc7bb81448dc8793a4eaeb12da4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546562"
---
# <a name="power-management-in-windows-forms"></a><span data-ttu-id="ee0a3-102">Windows Forms'ta Güç Yönetimi</span><span class="sxs-lookup"><span data-stu-id="ee0a3-102">Power Management in Windows Forms</span></span>
<span data-ttu-id="ee0a3-103">Windows Forms uygulamalarınızı güç yönetimi özellikleri Windows işletim sisteminde yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee0a3-103">Your Windows Forms applications can take advantage of the power management features in the Windows operating system.</span></span> <span data-ttu-id="ee0a3-104">Uygulamalarınızı bir bilgisayarın güç durumunu izleyebilir ve bir durum değişikliği oluştuğunda harekete.</span><span class="sxs-lookup"><span data-stu-id="ee0a3-104">Your applications can monitor the power status of a computer and take action when a status change occurs.</span></span> <span data-ttu-id="ee0a3-105">Örneğin, uygulamanızın taşınabilir bir bilgisayar üzerinde çalışıyorsa, bilgisayarın pil şarjı altında belirli bir düzeyde düştüğünde, uygulamanızın belirli özelliklerini devre dışı bırakmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee0a3-105">For example, if your application is running on a portable computer, you might want to disable certain features in your application when the computer's battery charge falls under a certain level.</span></span>  
  
 <span data-ttu-id="ee0a3-106">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Sağlayan bir <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> güç durumu, bir kullanıcının ne zaman askıya alır veya işletim sistemi sürdürür gibi veya AC güç durumu veya pil durumu değiştiğinde bir değişiklik olduğunda oluşan olay.</span><span class="sxs-lookup"><span data-stu-id="ee0a3-106">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provides a <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> event that occurs whenever there is a change in power status, such as when a user suspends or resumes the operating system, or when the AC power status or battery status changes.</span></span> <span data-ttu-id="ee0a3-107"><xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> Özelliği <xref:System.Windows.Forms.SystemInformation> sınıfı olabilir aşağıdaki kod örneğinde gösterildiği gibi kullanılan sorgulamak için geçerli durumu.</span><span class="sxs-lookup"><span data-stu-id="ee0a3-107">The <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property of the <xref:System.Windows.Forms.SystemInformation> class can be used to query for the current status, as shown in the following code example.</span></span>  
  
 [!code-csharp[PowerMode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 <span data-ttu-id="ee0a3-108">Yanında <xref:System.Windows.Forms.BatteryChargeStatus> numaralandırmalar <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> özelliği de pil kapasitesi belirlemek için sabit listeleri içerir (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) ve pil yüzdesi ücret (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span><span class="sxs-lookup"><span data-stu-id="ee0a3-108">Besides the <xref:System.Windows.Forms.BatteryChargeStatus> enumerations, the <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property also contains enumerations for determining battery capacity (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) and battery charge percentage (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span></span>  
  
 <span data-ttu-id="ee0a3-109">Kullanabileceğiniz <xref:System.Windows.Forms.Application.SetSuspendState%2A> yöntemi <xref:System.Windows.Forms.Application> bir bilgisayar, hazırda beklemeye veya modu askıya alma.</span><span class="sxs-lookup"><span data-stu-id="ee0a3-109">You can use the <xref:System.Windows.Forms.Application.SetSuspendState%2A> method of the <xref:System.Windows.Forms.Application> to put a computer into hibernation or suspend mode.</span></span> <span data-ttu-id="ee0a3-110">Varsa `force` bağımsız değişkeni ayarlanır `false`, işletim sistemi askıya alma izni isteyen tüm uygulamalar için etkinliği yayınlamak.</span><span class="sxs-lookup"><span data-stu-id="ee0a3-110">If the `force` argument is set to `false`, the operating system will broadcast an event to all applications requesting permission to suspend.</span></span> <span data-ttu-id="ee0a3-111">Varsa `disableWakeEvent` bağımsız değişkeni ayarlanır `true`, işletim sistemi tüm Uyandırma olaylarını devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="ee0a3-111">If the `disableWakeEvent` argument is set to `true`, the operating system disables all wake events.</span></span>  
  
 <span data-ttu-id="ee0a3-112">Aşağıdaki kod örneği, bir bilgisayarı hazırda bekleme moduna gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ee0a3-112">The following code example demonstrates how to put a computer into hibernation.</span></span>  
  
 [!code-csharp[PowerMode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ee0a3-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee0a3-113">See also</span></span>
- <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>
- <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>
- <xref:System.Windows.Forms.Application.SetSuspendState%2A>
- <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
