---
title: İzleme Türü Özeti
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8f54f71ef63338708a29fac5557c7c7e8f257f58
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856004"
---
# <a name="trace-type-summary"></a>İzleme Türü Özeti
[Kaynak düzeyleri](https://go.microsoft.com/fwlink/?LinkID=94943) çeşitli izleme düzeylerini tanımlar: Kritik, hata, uyarı, bilgi ve ayrıntılı bilgilerin yanı sıra, izleme sınırının ve etkinlik aktarım `ActivityTracing` olaylarının çıktısına geçiş yapmak için bayrağın açıklaması sağlanır.  
  
 Ayrıca, ' den <xref:System.Diagnostics>yayılan Izleme türleri için [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) ' i gözden geçirebilirsiniz.  
  
 Aşağıdaki tabloda en önemli olanlar listelenmektedir.  
  
|İzleme türü|Açıklama|  
|----------------|-----------------|  
|Kritik|Önemli hata veya uygulama kilitlenmesi.|  
|Hata|Kurtarılabilir hata.|  
|Uyarı|Bilgi iletisi.|  
|Bilgiler|Kritik olmayan sorun.|  
|Ayrıntılı|Hata ayıklama izleme.|  
|Başlat|Mantıksal bir işlem birimi başlatılıyor.|  
|Askıya alma|Mantıksal bir işlem birimini askıya alma.|  
|Devam etme|Sürdürme mantıksal bir işlem birimi.|  
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
