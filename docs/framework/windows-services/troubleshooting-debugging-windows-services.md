---
title: 'Sorun Giderme: Windows hizmetlerinde hata ayıklama'
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
author: ghogen
ms.openlocfilehash: cbedb0051cbb08c2875e145a2bad35ae4d02a74e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053505"
---
# <a name="troubleshooting-debugging-windows-services"></a>Sorun Giderme: Windows hizmetlerinde hata ayıklama
Bir Windows hizmet uygulamasında hata ayıklarken, hizmetiniz ve **Windows Service Manager** etkileşime geçin. **Service Manager** <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi çağırarak hizmetinizi başlatır ve sonra <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemin dönmesi için 30 saniye bekler. Yöntem bu kez dönmezse, yönetici hizmetin başlatılamayacağını belirten bir hata gösterir.  
  
 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Yöntemi[hata ayıkladığınızda, nasıl yapılır: Windows hizmet uygulamalarında](how-to-debug-windows-service-applications.md)hata ayıklayın, bu 30 saniyelik sürenin farkında olmalısınız. <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Yöntemine bir kesme noktası yerleştirirseniz ve 30 saniye içinde ilerlemeyin, yönetici hizmeti başlatmayacak.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama](how-to-debug-windows-service-applications.md)
- [Windows Hizmeti Uygulamalarına Giriş](introduction-to-windows-service-applications.md)
