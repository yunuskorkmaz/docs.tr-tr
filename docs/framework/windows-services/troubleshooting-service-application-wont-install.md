---
title: "Sorun giderme: Hizmet uygulaması Kazanılan &#39; t yükleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 43c973d83d2d1b614cf0ce49ba8d4af24123b47e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-service-application-won39t-install"></a>Sorun giderme: Hizmet uygulaması Kazanılan &#39; t yükleme
Hizmet uygulamanızın doğru yüklenmez emin olmak için kontrol edin <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> özelliğini hizmet sınıfı bu hizmet için yükleyiciyi gösterildiği gibi aynı değere ayarlayın. Değer her iki örnek sırada hizmetinizin doğru bir şekilde yüklemek aynı olması gerekir.  
  
> [!NOTE]
>  Yükleme işlemi ile ilgili geri bildirim almak için yükleme günlüklerini de bakabilirsiniz.  
  
 Zaten yüklü aynı ada sahip başka bir hizmete sahip olup olmadığını belirlemek için denetlemelisiniz. Hizmet adları yüklemesinin başarılı olması için benzersiz olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
