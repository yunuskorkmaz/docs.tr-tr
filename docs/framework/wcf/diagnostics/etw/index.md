---
title: ETW ile Çözümleme İzleme
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: dd745730ca186b9489c547f790c546e95bf96372
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798081"
---
# <a name="analytic-tracing-with-etw"></a>ETW ile Çözümleme İzleme
Windows Communication Foundation (WCF) analitik izleme, bir WCF hizmetinin yürütülmesi sırasında tanılama bilgilerini yakalamak için bir yol sunar. WCF analitik izleme olayları, bir üretim ortamında WCF hizmetleri sorunlarını gidermeye olanak tanımak için WCF yığınındaki anahtar noktalarında dağıtılır. WCF Hizmetleri için analitik izleme, bu olaylar Windows için olay izleme (ETW) oturumuna çok [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] verimli bir şekilde yayıldığından, WCF hizmetlerini barındıran bir ürün sunucusunun performansı üzerinde en az etkisi vardır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Analitik İzlemeye Genel Bakış](analytic-tracing-overview.md)  
 WCF analitik izlemenin ' de [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]nasıl çalıştığını açıklar.  
  
 [Analitik İzlemeyi Dinamik Olarak Etkinleştirme](dynamically-enabling-analytic-tracing.md)  
 ETW kullanarak izlemenin dinamik olarak nasıl etkinleştirileceğini veya devre dışı bırakılacağını açıklar.  
  
 [İleti Akışı İzlemeyi Yapılandırma](configuring-message-flow-tracing.md)  
 İleti akışı izlemenin nasıl yapılandırılacağını açıklar.  
  
 [Analitik İzleme Etkinliği Başvurusu](analytic-trace-event-reference.md)  
 Olay düzeyleri, olay iletileri ve anahtar kelimeleri ile olay kimliklerinin bir tablosunu gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Hizmetleri ve Windows için Olay İzleme](../../samples/wcf-services-and-event-tracing-for-windows.md)
- [Windows'da Olay İzleme ile Olayları İzleme](../../../windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
