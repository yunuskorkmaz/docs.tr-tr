---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: 1df4b32feda246a536183a42ac11b113bc4bb259
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768403"
---
# <a name="msmqbindingelementbase"></a>MsmqBindingElementBase
MsmqBindingElementBase  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 MsmqBindingElementBase sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 MsmqBindingElementBase sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="customdeadletterqueue"></a>customDeadLetterQueue  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Aktarım veya teslim başarısız olan veya süresi dolmuş olan iletileri yerleştirildiği her uygulama için geçerliliğini yitirmiş kuyruk konumunu içeren bir URI.  
  
### <a name="deadletterqueue"></a>deadLetterQueue  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Kullanılacak geçerliliğini yitirmiş kuyruk türü belirten bir numaralandırma değeri.  
  
### <a name="durable"></a>dayanıklı  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Bu bağlama tarafından işlenen iletilerin sürekli veya geçici olup olmadığını belirten bir değer.  
  
### <a name="exactlyonce"></a>exactlyOnce  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Bu bağlama tarafından işlenen iletilerin tam olarak bir kez alınıp olup olmadığını gösteren bir Boole değeri.  
  
### <a name="maxretrycycles"></a>maxRetryCycles  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Alıcı uygulamasına iletileri teslim girişiminde yeniden deneme döngüsü sayısı.  
  
### <a name="receiveerrorhandling"></a>receiveErrorHandling  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Zehirli ileti işleme için ayarlar.  
  
### <a name="receiveretrycount"></a>receiveRetryCount  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Hemen yeniden deneme sayısı, uygulama kuyruktan okuyan bir ileti üzerinde çalışır.  
  
### <a name="retrycycledelay"></a>retryCycleDelay  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Anında teslim edilemeyen bir iletiyi teslim etmeye çalışırken deneme arasındaki gecikmeyi belirten bir değer dolaşır.  
  
### <a name="timetolive"></a>TimeToLive  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Süresi dolmadan önce bu bağlama tarafından işlenen iletilerin belirten zaman aralığını kuyrukta olabilir.  
  
### <a name="usemsmqtracing"></a>useMsmqTracing  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 İletileri bu bağlama tarafından işlenen olup olmadığını gösteren bir Boole değeri izlenip izlenmemesini gerektiğini.  
  
### <a name="usesourcejournal"></a>useSourceJournal  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Bu bağlama tarafından işlenen iletilerin kopyalarını kaynak günlük sırasındaki depolanıp depolanmayacağını gösteren bir Boole değeri.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.MsmqBindingBase>
