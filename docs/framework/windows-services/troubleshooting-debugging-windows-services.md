---
title: 'Sorun Giderme: Windows Hizmetlerinde Hata Ayıklama'
description: Windows Hizmetleri 'ni hata ayıklama ile çalışmaya başlayın. Bir Windows hizmet uygulamasında hata ayıklarken, hizmetiniz ve Windows Service Manager etkileşime geçin.
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
ms.openlocfilehash: 2c1180ef8e3e44c50f10a263d86dcae830d9cd0e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270399"
---
# <a name="troubleshooting-debugging-windows-services"></a>Sorun Giderme: Windows Hizmetlerinde Hata Ayıklama

Bir Windows hizmet uygulamasında hata ayıklarken, hizmetiniz ve **Windows Service Manager** etkileşime geçin. **Service Manager** yöntemi çağırarak hizmetinizi başlatır <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve sonra yöntemin dönmesi için 30 saniye bekler <xref:System.ServiceProcess.ServiceBase.OnStart%2A> . Yöntem bu kez dönmezse, yönetici hizmetin başlatılamayacağını belirten bir hata gösterir.  
  
 Yöntemi hata ayıkladığınızda, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> [nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama](how-to-debug-windows-service-applications.md)bölümünde açıklandığı gibi, bu 30 saniyelik sürenin farkında olmanız gerekir. Yöntemine bir kesme noktası yerleştirirseniz <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve 30 saniye içinde ilerlemeyin, yönetici hizmeti başlatmayacak.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama](how-to-debug-windows-service-applications.md)
- [Windows Hizmet Uygulamalarına Giriş](introduction-to-windows-service-applications.md)
