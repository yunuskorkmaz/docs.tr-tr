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
ms.openlocfilehash: 0912ff0909ffa5b22bed07543a2e514de4fb1ff5
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48035837"
---
# <a name="troubleshooting-service-application-won39t-install"></a><span data-ttu-id="b1852-102">Sorun giderme: Hizmet uygulaması kazanılan&#39;t yükleme</span><span class="sxs-lookup"><span data-stu-id="b1852-102">Troubleshooting: Service Application Won&#39;t Install</span></span>
<span data-ttu-id="b1852-103">Hizmet uygulamanızın doğru şekilde yüklenmezse emin olmak için kontrol <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> Yükleyici bu hizmet için gösterildiği gibi hizmet sınıfı özelliği aynı değere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b1852-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="b1852-104">Değer her iki örnek hizmetinizin doğru bir biçimde yüklenmesi sırayla aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b1852-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1852-105">Yükleme işlemi ile ilgili geri bildirim almak için yükleme günlüklerine da göz atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1852-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="b1852-106">Ayrıca zaten yüklü aynı ada sahip başka bir hizmete sahip olup olmadığınızı belirlemek için denetleme yapmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b1852-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="b1852-107">Hizmet adları yükleme başarılı olması için benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b1852-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1852-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1852-108">See Also</span></span>  
 [<span data-ttu-id="b1852-109">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="b1852-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
