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
ms.openlocfilehash: cbedb0051cbb08c2875e145a2bad35ae4d02a74e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053505"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="5322c-102">Sorun Giderme: Windows Hizmetlerinde Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5322c-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="5322c-103">Bir Windows hizmet uygulamasında hata ayıklarken, hizmetiniz ve **Windows Service Manager** etkileşime geçin.</span><span class="sxs-lookup"><span data-stu-id="5322c-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="5322c-104">**Service Manager** <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi çağırarak hizmetinizi başlatır ve sonra <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemin dönmesi için 30 saniye bekler.</span><span class="sxs-lookup"><span data-stu-id="5322c-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="5322c-105">Yöntem bu kez dönmezse, yönetici hizmetin başlatılamayacağını belirten bir hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="5322c-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="5322c-106"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> Yöntemi hata ayıkladığınızda, [nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama](how-to-debug-windows-service-applications.md)bölümünde açıklandığı gibi, bu 30 saniyelik sürenin farkında olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5322c-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="5322c-107"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> Yöntemine bir kesme noktası yerleştirirseniz ve 30 saniye içinde ilerlemeyin, yönetici hizmeti başlatmayacak.</span><span class="sxs-lookup"><span data-stu-id="5322c-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5322c-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5322c-108">See also</span></span>

- [<span data-ttu-id="5322c-109">Nasıl Yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5322c-109">How to: Debug Windows Service Applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="5322c-110">Windows Hizmet Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="5322c-110">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
