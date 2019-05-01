---
title: İzleme Türü Özeti
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 73777df2b58b14947c416ce409bcb42d439499ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925157"
---
# <a name="trace-type-summary"></a>İzleme Türü Özeti
[Kaynak düzeylerini](https://go.microsoft.com/fwlink/?LinkID=94943) çeşitli izleme düzeylerini tanımlar: Kritik, hata, uyarı, bilgi ve ayrıntı, sağlar açıklamasını `ActivityTracing` çıktısını değiştirir bayrak sınır ve etkinlik aktarım olayları izleme.  
  
 Ayrıca inceleyebilirsiniz [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) , gelen yayılan izlemeleri türde <xref:System.Diagnostics>.  
  
 Aşağıdaki tabloda, en önemli olanları listeler.  
  
|İzleme türü|Açıklama|  
|----------------|-----------------|  
|Kritik|Önemli hata veya uygulama kilitlenme.|  
|Hata|Kurtarılabilir bir hata oluştu.|  
|Uyarı|Bilgi iletisi.|  
|Bilgiler|Kritik olmayan sorun oluştu.|  
|Ayrıntılı|İzleme hata ayıklama.|  
|Başlat|Mantıksal birimi işleme başlatılıyor.|  
|Askıya alma|İşleme bir mantıksal birimin askıya alma.|  
|Devam etme|İşleme bir mantıksal birim sürdürme.|  
|Durdur|İşleme bir mantıksal birim durduruluyor.|  
|Aktarma|Bağıntı kimliği değiştiriliyor.|  
  
 Bir etkinlik, yukarıdaki izleme türleri bir birleşimi olarak tanımlanır.  
  
 Bir yerel (izleme kaynak) kapsamındaki ideal aktiviteye tanımlayan bir normal ifade verilmiştir,  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 Başka bir deyişle, etkinlik aşağıdaki koşulları karşılaması gerekir.  
  
- Başlamalı ve bir başlatma ve durdurma izlemeleri tarafından durdurur  
  
- Hemen bir askıya alma veya sürdürme izleme önceki bir aktarım izleme olmalıdır  
  
- Bu tür izleme varsa askıya alma ve sürdürme izlemeler arasında tüm izlemeleri olmamalıdır  
  
- Önceki koşullar gözlemlenen sürece her ve Kritik/hata/uyarı/bilgi/Verbose/aktarım izleme sayıda olabilir  
  
 Aşağıdaki genel kapsamda ideal aktiviteye tanımlayan bir düzenli ifadedir,  
  
```  
R+   
```  
  
 R ile yerel kapsama bir etkinlik için normal ifade edilen. Bu şekilde dönüşür,  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
