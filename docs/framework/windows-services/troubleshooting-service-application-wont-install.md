---
title: 'Sorun giderme: Hizmet uygulaması kazanılan&#39;t yükleme'
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
manager: douge
ms.openlocfilehash: 1f3e5674f9a52627efdc24d6c70c0ab16dcdbbbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509666"
---
# <a name="troubleshooting-service-application-won39t-install"></a><span data-ttu-id="1be08-102">Sorun giderme: Hizmet uygulaması kazanılan&#39;t yükleme</span><span class="sxs-lookup"><span data-stu-id="1be08-102">Troubleshooting: Service Application Won&#39;t Install</span></span>
<span data-ttu-id="1be08-103">Hizmet uygulamanızın doğru yüklenmez emin olmak için kontrol edin <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> özelliğini hizmet sınıfı bu hizmet için yükleyiciyi gösterildiği gibi aynı değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1be08-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="1be08-104">Değer her iki örnek sırada hizmetinizin doğru bir şekilde yüklemek aynı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1be08-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1be08-105">Yükleme işlemi ile ilgili geri bildirim almak için yükleme günlüklerini de bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1be08-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="1be08-106">Zaten yüklü aynı ada sahip başka bir hizmete sahip olup olmadığını belirlemek için denetlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="1be08-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="1be08-107">Hizmet adları yüklemesinin başarılı olması için benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1be08-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1be08-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1be08-108">See Also</span></span>  
 [<span data-ttu-id="1be08-109">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="1be08-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
