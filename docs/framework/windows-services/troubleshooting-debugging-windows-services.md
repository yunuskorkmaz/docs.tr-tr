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
ms.openlocfilehash: 5846692fa0d90a62dd569253abbd81aa63b5798d
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608900"
---
# <a name="troubleshooting-debugging-windows-services"></a>Sorun Giderme: Windows Hizmetlerinde Hata Ayıklama
Bir Windows hizmet uygulamasında hata ayıklarken, hizmetiniz ve **Windows Service Manager** etkileşime geçin. **Service Manager** yöntemi çağırarak hizmetinizi başlatır <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve sonra yöntemin dönmesi için 30 saniye bekler <xref:System.ServiceProcess.ServiceBase.OnStart%2A> . Yöntem bu kez dönmezse, yönetici hizmetin başlatılamayacağını belirten bir hata gösterir.  
  
 Yöntemi hata ayıkladığınızda, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> [nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama](how-to-debug-windows-service-applications.md)bölümünde açıklandığı gibi, bu 30 saniyelik sürenin farkında olmanız gerekir. Yöntemine bir kesme noktası yerleştirirseniz <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve 30 saniye içinde ilerlemeyin, yönetici hizmeti başlatmayacak.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama](how-to-debug-windows-service-applications.md)
- [Windows Hizmet Uygulamalarına Giriş](introduction-to-windows-service-applications.md)
