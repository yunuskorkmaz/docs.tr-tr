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
ms.openlocfilehash: 0dbbebd14ce0ff5f69a12c256238c7e0a02494cb
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47199950"
---
# <a name="troubleshooting-debugging-windows-services"></a>Sorun Giderme: Windows Hizmetlerinde Hata Ayıklama
Hata ayıklaması yaptığınızda bir Windows hizmet uygulaması, hizmetiniz ve **Windows Service Manager** etkileşim. **Service Manager** hizmetinizi çağrılarak başlatılır <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi ve 30 saniye bekler <xref:System.ServiceProcess.ServiceBase.OnStart%2A> döndürmek için yöntemi. Yöntemi bu süre içinde döndürmezse Yöneticisi hizmeti başlatılamıyor bir hata gösterir.  
  
 Hata ayıklaması yaptığınızda <xref:System.ServiceProcess.ServiceBase.OnStart%2A> açıklandığı yöntemi [nasıl yapılır: Windows hizmet uygulamaları hata ayıklama](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), bu 30 saniyelik süre farkında olmanız gerekir. Bir kesme noktasına yerleştirirseniz <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi ve üzerinden 30 saniye içinde adım değil, Hizmet Yöneticisi başlatılamıyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
