---
title: Güç yönetimi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
ms.openlocfilehash: 9ac39df43a08f62e50116c61c4bdeda4cd1c8281
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746859"
---
# <a name="power-management-in-windows-forms"></a>Windows Forms'ta Güç Yönetimi
Windows Forms uygulamalarınız Windows işletim sistemindeki güç yönetimi özelliklerinden yararlanabilir. Uygulamalarınız bir bilgisayarın güç durumunu izleyebilir ve bir durum değişikliği gerçekleştiğinde işlem gerçekleştirebilir. Örneğin, uygulamanız taşınabilir bir bilgisayarda çalışıyorsa, bilgisayarın pil ücreti belirli bir düzeyde kaldığında uygulamanızdaki belirli özellikleri devre dışı bırakmak isteyebilirsiniz.  
  
 .NET Framework, bir kullanıcının işletim sistemini askıya aldığı veya kaldığı zaman ya da AC güç durumu veya pil durumu değiştiğinde, güç durumunda gerçekleşen bir <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> olayı sağlar. Aşağıdaki kod örneğinde gösterildiği gibi, <xref:System.Windows.Forms.SystemInformation> sınıfının <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> özelliği geçerli durumu sorgulamak için kullanılabilir.  
  
 [!code-csharp[PowerMode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 <xref:System.Windows.Forms.BatteryChargeStatus> Numaralandırmaların yanı sıra, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> özelliği pil kapasitesi (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) ve pil ücreti yüzdesi (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>) belirlemek için numaralandırmalar da içerir.  
  
 Bir bilgisayarı hazırda bekleme veya askıya alma moduna almak için <xref:System.Windows.Forms.Application> <xref:System.Windows.Forms.Application.SetSuspendState%2A> yöntemini kullanabilirsiniz. `force` bağımsız değişkeni `false`olarak ayarlanırsa, işletim sistemi askıya almak için izin isteyen tüm uygulamalara bir olay yayınlar. `disableWakeEvent` bağımsız değişkeni `true`olarak ayarlanırsa, işletim sistemi tüm uyanma olaylarını devre dışı bırakır.  
  
 Aşağıdaki kod örneği, bir bilgisayarın hazırda beklemeye nasıl yerleştirileceğini gösterir.  
  
 [!code-csharp[PowerMode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>
- <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>
- <xref:System.Windows.Forms.Application.SetSuspendState%2A>
- <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
