---
title: 'Sorun giderme: Hizmet uygulaması yüklenmiyor'
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
ms.openlocfilehash: ecbaa3b2fb0e0fc85ed383385368617bf361f497
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289449"
---
# <a name="troubleshooting-service-application-wont-install"></a>Sorun giderme: Hizmet uygulaması yüklenmiyor
Hizmet uygulamanızın doğru şekilde yüklenmezse emin olmak için kontrol <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> Yükleyici bu hizmet için gösterildiği gibi hizmet sınıfı özelliği aynı değere ayarlanır. Değer her iki örnek hizmetinizin doğru bir biçimde yüklenmesi sırayla aynı olmalıdır.  
  
> [!NOTE]
>  Yükleme işlemi ile ilgili geri bildirim almak için yükleme günlüklerine da göz atabilirsiniz.  
  
 Ayrıca zaten yüklü aynı ada sahip başka bir hizmete sahip olup olmadığınızı belirlemek için denetleme yapmalıdır. Hizmet adları yükleme başarılı olması için benzersiz olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
