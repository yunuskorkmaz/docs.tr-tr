---
title: 'Sorun Giderme: Windows Hizmetlerinde Hata Ayıklama'
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
manager: douge
ms.openlocfilehash: 77a0c19c2da2d1886beaf396650fa024fc1243a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510143"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="06483-102">Sorun Giderme: Windows Hizmetlerinde Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="06483-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="06483-103">Windows hizmet uygulaması, hizmetiniz debug ne zaman ve **Windows Service Manager** etkileşim.</span><span class="sxs-lookup"><span data-stu-id="06483-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="06483-104">**Service Manager** çağırarak hizmetinizi başlatır <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi ve 30 saniye bekler <xref:System.ServiceProcess.ServiceBase.OnStart%2A> döndürülecek yöntemi.</span><span class="sxs-lookup"><span data-stu-id="06483-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="06483-105">Yöntemi bu sürede döndürmezse Yöneticisi hizmeti başlatılamıyor bir hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="06483-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="06483-106">Ne zaman hata ayıklama <xref:System.ServiceProcess.ServiceBase.OnStart%2A> açıklandığı gibi yöntemi [nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), bu 30 saniyelik süre farkında olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="06483-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="06483-107">Bir kesme yerleştirirseniz <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi ve üzerinden 30 saniye içinde adım değil, yönetici, hizmet başlamaz.</span><span class="sxs-lookup"><span data-stu-id="06483-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06483-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06483-108">See Also</span></span>  
 [<span data-ttu-id="06483-109">Nasıl Yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="06483-109">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [<span data-ttu-id="06483-110">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="06483-110">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
