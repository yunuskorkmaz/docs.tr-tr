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
# <a name="troubleshooting-service-application-won39t-install"></a>Sorun giderme: Hizmet uygulaması kazanılan&#39;t yükleme
Hizmet uygulamanızın doğru şekilde yüklenmezse emin olmak için kontrol <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> Yükleyici bu hizmet için gösterildiği gibi hizmet sınıfı özelliği aynı değere ayarlanır. Değer her iki örnek hizmetinizin doğru bir biçimde yüklenmesi sırayla aynı olmalıdır.  
  
> [!NOTE]
>  Yükleme işlemi ile ilgili geri bildirim almak için yükleme günlüklerine da göz atabilirsiniz.  
  
 Ayrıca zaten yüklü aynı ada sahip başka bir hizmete sahip olup olmadığınızı belirlemek için denetleme yapmalıdır. Hizmet adları yükleme başarılı olması için benzersiz olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
