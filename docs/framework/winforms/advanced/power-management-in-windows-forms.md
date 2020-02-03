---
title: Güç yönetimi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
ms.openlocfilehash: 9ac39df43a08f62e50116c61c4bdeda4cd1c8281
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746859"
---
# <a name="power-management-in-windows-forms"></a><span data-ttu-id="83003-102">Windows Forms'ta Güç Yönetimi</span><span class="sxs-lookup"><span data-stu-id="83003-102">Power Management in Windows Forms</span></span>
<span data-ttu-id="83003-103">Windows Forms uygulamalarınız Windows işletim sistemindeki güç yönetimi özelliklerinden yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="83003-103">Your Windows Forms applications can take advantage of the power management features in the Windows operating system.</span></span> <span data-ttu-id="83003-104">Uygulamalarınız bir bilgisayarın güç durumunu izleyebilir ve bir durum değişikliği gerçekleştiğinde işlem gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="83003-104">Your applications can monitor the power status of a computer and take action when a status change occurs.</span></span> <span data-ttu-id="83003-105">Örneğin, uygulamanız taşınabilir bir bilgisayarda çalışıyorsa, bilgisayarın pil ücreti belirli bir düzeyde kaldığında uygulamanızdaki belirli özellikleri devre dışı bırakmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83003-105">For example, if your application is running on a portable computer, you might want to disable certain features in your application when the computer's battery charge falls under a certain level.</span></span>  
  
 <span data-ttu-id="83003-106">.NET Framework, bir kullanıcının işletim sistemini askıya aldığı veya kaldığı zaman ya da AC güç durumu veya pil durumu değiştiğinde, güç durumunda gerçekleşen bir <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> olayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="83003-106">The .NET Framework provides a <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> event that occurs whenever there is a change in power status, such as when a user suspends or resumes the operating system, or when the AC power status or battery status changes.</span></span> <span data-ttu-id="83003-107">Aşağıdaki kod örneğinde gösterildiği gibi, <xref:System.Windows.Forms.SystemInformation> sınıfının <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> özelliği geçerli durumu sorgulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="83003-107">The <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property of the <xref:System.Windows.Forms.SystemInformation> class can be used to query for the current status, as shown in the following code example.</span></span>  
  
 [!code-csharp[PowerMode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 <span data-ttu-id="83003-108"><xref:System.Windows.Forms.BatteryChargeStatus> Numaralandırmaların yanı sıra, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> özelliği pil kapasitesi (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) ve pil ücreti yüzdesi (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>) belirlemek için numaralandırmalar da içerir.</span><span class="sxs-lookup"><span data-stu-id="83003-108">Besides the <xref:System.Windows.Forms.BatteryChargeStatus> enumerations, the <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property also contains enumerations for determining battery capacity (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) and battery charge percentage (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span></span>  
  
 <span data-ttu-id="83003-109">Bir bilgisayarı hazırda bekleme veya askıya alma moduna almak için <xref:System.Windows.Forms.Application> <xref:System.Windows.Forms.Application.SetSuspendState%2A> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83003-109">You can use the <xref:System.Windows.Forms.Application.SetSuspendState%2A> method of the <xref:System.Windows.Forms.Application> to put a computer into hibernation or suspend mode.</span></span> <span data-ttu-id="83003-110">`force` bağımsız değişkeni `false`olarak ayarlanırsa, işletim sistemi askıya almak için izin isteyen tüm uygulamalara bir olay yayınlar.</span><span class="sxs-lookup"><span data-stu-id="83003-110">If the `force` argument is set to `false`, the operating system will broadcast an event to all applications requesting permission to suspend.</span></span> <span data-ttu-id="83003-111">`disableWakeEvent` bağımsız değişkeni `true`olarak ayarlanırsa, işletim sistemi tüm uyanma olaylarını devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="83003-111">If the `disableWakeEvent` argument is set to `true`, the operating system disables all wake events.</span></span>  
  
 <span data-ttu-id="83003-112">Aşağıdaki kod örneği, bir bilgisayarın hazırda beklemeye nasıl yerleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="83003-112">The following code example demonstrates how to put a computer into hibernation.</span></span>  
  
 [!code-csharp[PowerMode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="83003-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83003-113">See also</span></span>

- <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>
- <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>
- <xref:System.Windows.Forms.Application.SetSuspendState%2A>
- <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
