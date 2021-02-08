---
description: 'Daha fazla bilgi edinin: Izleme türü Özeti'
title: İzleme Türü Özeti
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: ebfe9de16766494a6aebe0a8d2501954855dc4df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803223"
---
# <a name="trace-type-summary"></a>İzleme Türü Özeti

[Kaynak düzeyleri](xref:System.Diagnostics.SourceLevels) çeşitli izleme düzeylerini tanımlar: kritik, hata, uyarı, bilgi ve ayrıntılı, Ayrıca, `ActivityTracing` izleme sınırının ve etkinlik aktarım olaylarının çıktısına geçiş yapmak için bayrağın bir açıklamasını sağlar.  
  
 Ayrıca, ' <xref:System.Diagnostics.TraceEventType> den yayınlanbilen izleme türlerini gözden geçirebilirsiniz <xref:System.Diagnostics> .  
  
 Aşağıdaki tabloda en önemli olanlar listelenmektedir.  
  
|İzleme türü|Açıklama|  
|----------------|-----------------|  
|Kritik|Önemli hata veya uygulama kilitlenmesi.|  
|Hata|Kurtarılabilir hata.|  
|Uyarı|Bilgi iletisi.|  
|Bilgi|Kritik olmayan sorun.|  
|Ayrıntılı|Hata ayıklama izleme.|  
|Başlangıç|Mantıksal bir işlem birimi başlatılıyor.|  
|Askıya Alma|Mantıksal bir işlem birimini askıya alma.|  
|Sürdür|Sürdürme mantıksal bir işlem birimi.|  
|Durdur|Mantıksal bir işleme birimi durduruluyor.|  
|Aktarma|Bağıntı kimliğini değiştirme.|  
  
 Etkinlik, yukarıdaki izleme türlerinin birleşimi olarak tanımlanır.  
  
 Aşağıda, yerel (izleme kaynağı) kapsamında ideal bir etkinliği tanımlayan bir normal ifade verilmiştir,  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 Bu, bir etkinliğin aşağıdaki koşulları karşılaması gerektiği anlamına gelir.  
  
- Başlatma ve durdurma izlemelerinin sırasıyla başlaması ve durdurulması gerekir  
  
- Bir askıya alma veya yeniden başlatma izlemesinin hemen öncesinde bir aktarım izlemesi olmalıdır  
  
- Bu tür izlemeler varsa askıya al ve Duraklat izlemeleri arasında izleme içermemelidir  
  
- Önceki koşullar gözlemlendiği sürece bir veya daha fazla kritik/hata/uyarı/bilgi/ayrıntılı/aktarım izlerinden oluşabilir  
  
 Aşağıda genel kapsamda ideal bir etkinliği tanımlayan bir normal ifade verilmiştir,  
  
`R+`  
  
 yerel kapsamdaki bir etkinliğin normal ifadesi olan R. Bu,  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
