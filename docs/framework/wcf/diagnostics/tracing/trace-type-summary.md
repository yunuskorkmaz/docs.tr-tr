---
title: İzleme Türü Özeti
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8ed6dceb19caa52f928f285064c60337e3f15a87
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674835"
---
# <a name="trace-type-summary"></a>İzleme Türü Özeti
[Kaynak Düzeyleri](xref:System.Diagnostics.SourceLevels) çeşitli izleme düzeyleri tanımlar: Kritik, Hata, Uyarı, Bilgi ve Verbose, yanı sıra izleme sınır ve etkinlik aktarım olayları çıktısını geçişbayrak, bir açıklama `ActivityTracing` sağlar.  
  
 Ayrıca, 'den <xref:System.Diagnostics.TraceEventType> <xref:System.Diagnostics>çıkarılabilen izleme türleri için de gözden geçirebilirsiniz.  
  
 Aşağıdaki tabloda en önemli olanları listeleyiş.  
  
|İzleme Türü|Açıklama|  
|----------------|-----------------|  
|Kritik|Önemli hata veya uygulama çökmesi.|  
|Hata|Kurtarılabilir hata.|  
|Uyarı|Bilgilendirme iletisi.|  
|Bilgi|Kritik olmayan bir sorun.|  
|Ayrıntılı|Hata ayıklama izi.|  
|Başlangıç|Mantıksal bir işlem biriminin başlatılması.|  
|Askıya Alma|Mantıksal bir işlem biriminin askıya alınması.|  
|Sürdür|Mantıksal bir işlem biriminin devamı.|  
|Durdur|Mantıksal bir işlem biriminin durdurulması.|  
|Aktarma|Korelasyon kimliğinin değiştirilmesi.|  
  
 Bir etkinlik yukarıdaki izleme türlerinin bir leşimi olarak tanımlanır.  
  
 Aşağıda, yerel (izleme kaynağı) kapsamda ideal bir etkinliği tanımlayan normal bir ifade,  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 Bu, bir etkinliğin aşağıdaki koşulları karşılaması gerektiği anlamına gelir.  
  
- Başlangıç ve Durdurma izlerine göre sırasıyla başlatmalı ve durdurmalı  
  
- Askıya Alma veya Devam takibinden hemen önce bir Aktarım izleme olmalıdır  
  
- Bu tür izler varsa Askıya Alma ve Devam İzleri arasında herhangi bir iz olmamalıdır  
  
- Önceki koşullar gözlendiği sürece kritik/Hata/Uyarı/Bilgi/Verbose/Transfer izlerinin herhangi bir ve çok sayıda olabilir  
  
 Aşağıda, genel kapsamda ideal bir etkinliği tanımlayan düzenli bir ifade  
  
`R+`  
  
 R yerel kapsamdabir etkinlik için düzenli ifade olmak. Bu, çevirir  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
