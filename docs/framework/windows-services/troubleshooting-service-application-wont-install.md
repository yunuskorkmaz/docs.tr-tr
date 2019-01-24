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
ms.openlocfilehash: 998c7a3f5ca405b3bd66b877d027126f6c76cc15
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494424"
---
# <a name="troubleshooting-service-application-won39t-install"></a><span data-ttu-id="6d032-102">Sorun giderme: Hizmet uygulaması kazanılan&#39;t yükleme</span><span class="sxs-lookup"><span data-stu-id="6d032-102">Troubleshooting: Service Application Won&#39;t Install</span></span>
<span data-ttu-id="6d032-103">Hizmet uygulamanızın doğru şekilde yüklenmezse emin olmak için kontrol <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> Yükleyici bu hizmet için gösterildiği gibi hizmet sınıfı özelliği aynı değere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="6d032-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="6d032-104">Değer her iki örnek hizmetinizin doğru bir biçimde yüklenmesi sırayla aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6d032-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d032-105">Yükleme işlemi ile ilgili geri bildirim almak için yükleme günlüklerine da göz atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d032-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="6d032-106">Ayrıca zaten yüklü aynı ada sahip başka bir hizmete sahip olup olmadığınızı belirlemek için denetleme yapmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6d032-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="6d032-107">Hizmet adları yükleme başarılı olması için benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6d032-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d032-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d032-108">See also</span></span>
- [<span data-ttu-id="6d032-109">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="6d032-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
