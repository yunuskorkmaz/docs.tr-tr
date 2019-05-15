---
title: Windows Forms'ta Güç Yönetimi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
ms.openlocfilehash: 36c152a9e388fe61b1c82a8783bf74bbe6c8f123
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592512"
---
# <a name="power-management-in-windows-forms"></a>Windows Forms'ta Güç Yönetimi
Windows Forms uygulamalarınızı güç yönetimi özellikleri Windows işletim sisteminde yararlanabilirsiniz. Uygulamalarınızı bir bilgisayarın güç durumunu izleyebilir ve bir durum değişikliği oluştuğunda harekete. Örneğin, uygulamanızın taşınabilir bir bilgisayar üzerinde çalışıyorsa, bilgisayarın pil şarjı altında belirli bir düzeyde düştüğünde, uygulamanızın belirli özelliklerini devre dışı bırakmak isteyebilirsiniz.  
  
 .NET Framework sağlar bir <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> güç durumu, bir kullanıcının ne zaman askıya alır veya işletim sistemi sürdürür gibi veya AC güç durumu veya pil durumu değiştiğinde bir değişiklik olduğunda oluşan olay. <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> Özelliği <xref:System.Windows.Forms.SystemInformation> sınıfı olabilir aşağıdaki kod örneğinde gösterildiği gibi kullanılan sorgulamak için geçerli durumu.  
  
 [!code-csharp[PowerMode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 Yanında <xref:System.Windows.Forms.BatteryChargeStatus> numaralandırmalar <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> özelliği de pil kapasitesi belirlemek için sabit listeleri içerir (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) ve pil yüzdesi ücret (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).  
  
 Kullanabileceğiniz <xref:System.Windows.Forms.Application.SetSuspendState%2A> yöntemi <xref:System.Windows.Forms.Application> bir bilgisayar, hazırda beklemeye veya modu askıya alma. Varsa `force` bağımsız değişkeni ayarlanır `false`, işletim sistemi askıya alma izni isteyen tüm uygulamalar için etkinliği yayınlamak. Varsa `disableWakeEvent` bağımsız değişkeni ayarlanır `true`, işletim sistemi tüm Uyandırma olaylarını devre dışı bırakır.  
  
 Aşağıdaki kod örneği, bir bilgisayarı hazırda bekleme moduna gösterilmiştir.  
  
 [!code-csharp[PowerMode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>
- <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>
- <xref:System.Windows.Forms.Application.SetSuspendState%2A>
- <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
