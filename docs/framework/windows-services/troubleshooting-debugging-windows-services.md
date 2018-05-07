---
title: 'Sorun Giderme: Windows Hizmetlerinde Hata Ayıklama'
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
manager: douge
ms.openlocfilehash: 77a0c19c2da2d1886beaf396650fa024fc1243a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-debugging-windows-services"></a>Sorun Giderme: Windows Hizmetlerinde Hata Ayıklama
Windows hizmet uygulaması, hizmetiniz debug ne zaman ve **Windows Service Manager** etkileşim. **Service Manager** çağırarak hizmetinizi başlatır <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi ve 30 saniye bekler <xref:System.ServiceProcess.ServiceBase.OnStart%2A> döndürülecek yöntemi. Yöntemi bu sürede döndürmezse Yöneticisi hizmeti başlatılamıyor bir hata gösterir.  
  
 Ne zaman hata ayıklama <xref:System.ServiceProcess.ServiceBase.OnStart%2A> açıklandığı gibi yöntemi [nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), bu 30 saniyelik süre farkında olmanız gerekir. Bir kesme yerleştirirseniz <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi ve üzerinden 30 saniye içinde adım değil, yönetici, hizmet başlamaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
