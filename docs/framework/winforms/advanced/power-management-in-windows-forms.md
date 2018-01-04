---
title: "Windows Forms'ta Güç Yönetimi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7600ae42194b3333c404d217c2605a226df99e7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="power-management-in-windows-forms"></a>Windows Forms'ta Güç Yönetimi
Windows Forms uygulamaları güç yönetimi özellikleri Windows işletim sisteminde yararlanabilir. Uygulamalarınızı, bir bilgisayarın güç durumunu izlemek ve bir durum değişikliği oluştuğunda eylemi gerçekleştirin. Örneğin, uygulamanızın taşınabilir bir bilgisayarda çalışıyorsa, bilgisayarın pili belirli bir düzey altında düştüğünde, uygulamanızın belirli özelliklerini devre dışı bırakmak isteyebilirsiniz.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Sağlayan bir <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> güç durumu, bir kullanıcı askıya alır veya işletim sistemi sürdürür gibi veya AC güç durumu veya pil durumu değiştiğinde bir değişiklik olduğunda oluşan olay. <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> Özelliği <xref:System.Windows.Forms.SystemInformation> sınıfı olabilir sorgulamak için geçerli durum, kullanılan aşağıdaki kod örneğinde gösterildiği gibi.  
  
 [!code-csharp[PowerMode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 Yanında <xref:System.Windows.Forms.BatteryChargeStatus> numaralandırmalar, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> özelliği de pil kapasitesini belirlemek için numaralandırmalar içerir (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) ve yüzde ücret pil (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).  
  
 Kullanabileceğiniz <xref:System.Windows.Forms.Application.SetSuspendState%2A> yöntemi <xref:System.Windows.Forms.Application> bir bilgisayarı hazırda beklemeye veya askıya alma modu. Varsa `force` bağımsız değişkeni olarak ayarlanmış `false`, işletim sistemi askıya almak için izin istiyor tüm uygulamalar için bir olay yayın. Varsa `disableWakeEvent` bağımsız değişkeni olarak ayarlanmış `true`, tüm uyku modundan çıkarma olayları işletim sistemi devre dışı bırakır.  
  
 Aşağıdaki kod örneği, bir bilgisayarı hazırda bekleme moduna gösterilmiştir.  
  
 [!code-csharp[PowerMode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>  
 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>  
 <xref:System.Windows.Forms.Application.SetSuspendState%2A>  
 <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
