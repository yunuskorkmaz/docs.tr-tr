---
title: 'Sorun Giderme: Hizmet Uygulaması Yüklenmiyor'
description: Hizmet uygulamanız yüklenememesi durumunda sorun giderme yapın. Hizmet sınıfı için ServiceName özelliğinin doğru ayarlandığından emin olun.
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
ms.openlocfilehash: 4a57fb6975a6ded48abf7c8fd7eacec16e4f94d8
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925533"
---
# <a name="troubleshooting-service-application-wont-install"></a><span data-ttu-id="a390e-104">Sorun Giderme: Hizmet Uygulaması Yüklenmiyor</span><span class="sxs-lookup"><span data-stu-id="a390e-104">Troubleshooting: Service Application Won't Install</span></span>
<span data-ttu-id="a390e-105">Hizmet uygulamanız doğru şekilde yüklenemezse, <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> hizmet sınıfı özelliğinin bu hizmet için yükleyicide gösterilen değere ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="a390e-105">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="a390e-106">Hizmetinizin doğru şekilde yüklenmesi için değerin her iki örnekte de aynı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a390e-106">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a390e-107">Yükleme işlemi hakkında geri bildirim almak için yükleme günlüklerine de bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a390e-107">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="a390e-108">Aynı ada sahip başka bir hizmetin zaten yüklü olup olmadığını da denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a390e-108">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="a390e-109">Yüklemenin başarılı olabilmesi için hizmet adları benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a390e-109">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a390e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a390e-110">See also</span></span>

- [<span data-ttu-id="a390e-111">Windows Hizmet Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="a390e-111">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
