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
ms.openlocfilehash: f75a2f33ecde408d2d8e2f2343197ba56c4b8c21
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143825"
---
# <a name="troubleshooting-service-application-wont-install"></a>Sorun Giderme: Hizmet Uygulaması Yüklenmiyor
Hizmet uygulamanızın doğru şekilde yüklenmezse emin olmak için kontrol <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> Yükleyici bu hizmet için gösterildiği gibi hizmet sınıfı özelliği aynı değere ayarlanır. Değer her iki örnek hizmetinizin doğru bir biçimde yüklenmesi sırayla aynı olmalıdır.  
  
> [!NOTE]
>  Yükleme işlemi ile ilgili geri bildirim almak için yükleme günlüklerine da göz atabilirsiniz.  
  
 Ayrıca zaten yüklü aynı ada sahip başka bir hizmete sahip olup olmadığınızı belirlemek için denetleme yapmalıdır. Hizmet adları yükleme başarılı olması için benzersiz olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
