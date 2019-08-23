---
title: 'Sorun Giderme: Hizmet Uygulaması Yüklenmiyor'
ms.date: 03/30/2017
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
author: ghogen
ms.openlocfilehash: d04a0ddcef9ff7c31abd422f7f9fba34e804d2b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935422"
---
# <a name="troubleshooting-service-application-wont-install"></a><span data-ttu-id="37e17-102">Sorun Giderme: Hizmet Uygulaması Yüklenmiyor</span><span class="sxs-lookup"><span data-stu-id="37e17-102">Troubleshooting: Service Application Won't Install</span></span>
<span data-ttu-id="37e17-103">Hizmet uygulamanız doğru şekilde yüklenemezse, hizmet sınıfı <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> özelliğinin bu hizmet için yükleyicide gösterilen değere ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="37e17-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="37e17-104">Hizmetinizin doğru şekilde yüklenmesi için değerin her iki örnekte de aynı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="37e17-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37e17-105">Yükleme işlemi hakkında geri bildirim almak için yükleme günlüklerine de bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37e17-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="37e17-106">Aynı ada sahip başka bir hizmetin zaten yüklü olup olmadığını da denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="37e17-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="37e17-107">Yüklemenin başarılı olabilmesi için hizmet adları benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="37e17-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37e17-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37e17-108">See also</span></span>

- [<span data-ttu-id="37e17-109">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="37e17-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
