---
title: "Sorun Giderme: Windows Hizmetlerinde Hata Ayıklama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 51c28f6e9b6fa2974fb9861716b2c9fc2a38fe1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="9f3d2-102">Sorun Giderme: Windows Hizmetlerinde Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9f3d2-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="9f3d2-103">Windows hizmet uygulaması, hizmetiniz debug ne zaman ve **Windows Service Manager** etkileşim.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="9f3d2-104">**Service Manager** çağırarak hizmetinizi başlatır <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi ve 30 saniye bekler <xref:System.ServiceProcess.ServiceBase.OnStart%2A> döndürülecek yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="9f3d2-105">Yöntemi bu sürede döndürmezse Yöneticisi hizmeti başlatılamıyor bir hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="9f3d2-106">Ne zaman hata ayıklama <xref:System.ServiceProcess.ServiceBase.OnStart%2A> açıklandığı gibi yöntemi [nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), bu 30 saniyelik süre farkında olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="9f3d2-107">Bir kesme yerleştirirseniz <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi ve üzerinden 30 saniye içinde adım değil, yönetici, hizmet başlamaz.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f3d2-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-108">See Also</span></span>  
 [<span data-ttu-id="9f3d2-109">Nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9f3d2-109">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [<span data-ttu-id="9f3d2-110">Windows hizmet uygulamalarına giriş</span><span class="sxs-lookup"><span data-stu-id="9f3d2-110">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
