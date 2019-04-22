---
title: 'Sorun Giderme: Windows hizmetlerinde hata ayıklama'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- troubleshooting service applications
- services, troubleshooting
- troubleshooting debugging, Windows Services
- Windows Service applications, debugging
- services, debugging
- Windows Service applications, troubleshooting
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
author: ghogen
ms.openlocfilehash: 0552fc005a25e83065bb44e425770f9cef84f71b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082587"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="5eec1-102">Sorun Giderme: Windows hizmetlerinde hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5eec1-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="5eec1-103">Hata ayıklaması yaptığınızda bir Windows hizmet uygulaması, hizmetiniz ve **Windows Service Manager** etkileşim.</span><span class="sxs-lookup"><span data-stu-id="5eec1-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="5eec1-104">**Service Manager** hizmetinizi çağrılarak başlatılır <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi ve 30 saniye bekler <xref:System.ServiceProcess.ServiceBase.OnStart%2A> döndürmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5eec1-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="5eec1-105">Yöntemi bu süre içinde döndürmezse Yöneticisi hizmeti başlatılamıyor bir hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="5eec1-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="5eec1-106">Hata ayıklaması yaptığınızda <xref:System.ServiceProcess.ServiceBase.OnStart%2A> açıklandığı yöntemi [nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), bu 30 saniyelik süre farkında olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5eec1-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="5eec1-107">Bir kesme noktasına yerleştirirseniz <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi ve üzerinden 30 saniye içinde adım değil, Hizmet Yöneticisi başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="5eec1-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eec1-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5eec1-108">See also</span></span>

- [<span data-ttu-id="5eec1-109">Nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5eec1-109">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="5eec1-110">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="5eec1-110">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
