---
title: 'Sorun Giderme: Windows Hizmetlerinde Hata Ayıklama'
description: Windows Hizmetleri 'ni hata ayıklama ile çalışmaya başlayın. Bir Windows hizmet uygulamasında hata ayıklarken, hizmetiniz ve Windows Service Manager etkileşime geçin.
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
ms.openlocfilehash: 5846692fa0d90a62dd569253abbd81aa63b5798d
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608900"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="6f339-104">Sorun Giderme: Windows Hizmetlerinde Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6f339-104">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="6f339-105">Bir Windows hizmet uygulamasında hata ayıklarken, hizmetiniz ve **Windows Service Manager** etkileşime geçin.</span><span class="sxs-lookup"><span data-stu-id="6f339-105">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="6f339-106">**Service Manager** yöntemi çağırarak hizmetinizi başlatır <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve sonra yöntemin dönmesi için 30 saniye bekler <xref:System.ServiceProcess.ServiceBase.OnStart%2A> .</span><span class="sxs-lookup"><span data-stu-id="6f339-106">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="6f339-107">Yöntem bu kez dönmezse, yönetici hizmetin başlatılamayacağını belirten bir hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f339-107">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="6f339-108">Yöntemi hata ayıkladığınızda, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> [nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama](how-to-debug-windows-service-applications.md)bölümünde açıklandığı gibi, bu 30 saniyelik sürenin farkında olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f339-108">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="6f339-109">Yöntemine bir kesme noktası yerleştirirseniz <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve 30 saniye içinde ilerlemeyin, yönetici hizmeti başlatmayacak.</span><span class="sxs-lookup"><span data-stu-id="6f339-109">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f339-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f339-110">See also</span></span>

- [<span data-ttu-id="6f339-111">Nasıl yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6f339-111">How to: Debug Windows Service Applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="6f339-112">Windows Hizmet Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="6f339-112">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
