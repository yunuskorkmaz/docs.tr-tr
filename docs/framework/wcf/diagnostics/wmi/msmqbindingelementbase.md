---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: 9a9d48cc49b19f737236939c83a4e9421013f48f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486607"
---
# <a name="msmqbindingelementbase"></a>MsmqBindingElementBase
MsmqBindingElementBase  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 MsmqBindingElementBase sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 MsmqBindingElementBase sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="customdeadletterqueue"></a>customDeadLetterQueue  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Süresi dolan veya aktarımı veya teslim başarısız olmuş iletileri yerleştirildiği her uygulama için sahipsiz sıra konumunu içeren bir URI.  
  
### <a name="deadletterqueue"></a>deadLetterQueue  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Kullanılacak sahipsiz sıra türünü gösteren bir numaralandırma değeri.  
  
### <a name="durable"></a>dayanıklı  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Bu bağlama tarafından işlenen iletilerin kalıcı veya geçici olup olmadığını belirten bir değer.  
  
### <a name="exactlyonce"></a>exactlyOnce  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Bu bağlama tarafından işlenen iletilerin tam olarak bir kez alınan olup olmadığını gösteren bir Boole değeri.  
  
### <a name="maxretrycycles"></a>maxRetryCycles  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 İletileri teslim alma işlemini yapan uygulamanın için denemek için yeniden deneme döngüsü sayısı.  
  
### <a name="receiveerrorhandling"></a>receiveErrorHandling  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Zehirli ileti işleme yönelik ayarlar.  
  
### <a name="receiveretrycount"></a>receiveRetryCount  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Hemen yeniden deneme sayısı uygulama sırasından okunan bir ileti üzerinde çalışır.  
  
### <a name="retrycycledelay"></a>retryCycleDelay  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Yeniden deneme arasındaki gecikme süresini belirten bir değer hemen teslim edilemeyen bir ileti teslim çalışılırken geçiş yapar.  
  
### <a name="timetolive"></a>TimeToLive  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Süresi dolmadan önce bu bağlama tarafından işlenen ne kadar süreyle iletileri gösterir zaman aralığını sırada olabilir.  
  
### <a name="usemsmqtracing"></a>useMsmqTracing  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Bu bağlama tarafından işlenen iletileri olup olmadığını gösteren bir Boole değeri izlenen.  
  
### <a name="usesourcejournal"></a>useSourceJournal  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Bu bağlama tarafından işlenen iletilerin kopyalarını kaynak günlük sırasındaki depolanması gerekip gerekmediğini gösteren bir Boole değeri.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.MsmqBindingBase>
