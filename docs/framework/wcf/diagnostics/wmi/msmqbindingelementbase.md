---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: 48d26bfa9074fd605e3545579f0bdc2744dfc7d8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267870"
---
# <a name="msmqbindingelementbase"></a>MsmqBindingElementBase

MsmqBindingElementBase  
  
## <a name="syntax"></a>Syntax  
  
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

 MsmqBindingElementBase sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 MsmqBindingElementBase sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="customdeadletterqueue"></a>CustomDeadLetterQueue  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bu, zaman aşımına uğradı veya başarısız aktarım ya da teslimi olan iletilerin yerleştirildiği her uygulama için atılacak ileti sırasının konumunu içeren bir URI.  
  
### <a name="deadletterqueue"></a>Özelliğinde  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Kullanılacak atılacak ileti sırasının türünü gösteren bir numaralandırma değeri.  
  
### <a name="durable"></a>Dayanıklı  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Bu bağlama tarafından işlenen iletilerin dayanıklı veya geçici olup olmadığını belirten bir değer.  
  
### <a name="exactlyonce"></a>ExactlyOnce  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Bu bağlama tarafından işlenen iletilerin tam olarak bir kez alınıp alınmayacağını belirten bir Boole değeri.  
  
### <a name="maxretrycycles"></a>Maxretrydöngüleri  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 İleti alma uygulamasına iletileri teslim girişiminde bulunan en fazla yeniden deneme döngüsü sayısı.  
  
### <a name="receiveerrorhandling"></a>ReceiveErrorHandling  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Zarar iletisi işleme ayarları.  
  
### <a name="receiveretrycount"></a>ReceiveRetryCount  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Uygulama sırasından okunan bir ileti üzerinde anında yeniden deneme girişimlerinin en fazla sayısı.  
  
### <a name="retrycycledelay"></a>RetryCycleDelay  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Anında teslim edilmemiş bir iletiyi teslim etmeye çalışırken deneme döngüleri arasındaki gecikme süresini belirten bir değer.  
  
### <a name="timetolive"></a>TimeToLive  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Bu bağlama tarafından işlenen iletilerin, süresi dolmadan önce kuyrukta ne kadar süre içinde kalabileceğini belirten zaman aralığı.  
  
### <a name="usemsmqtracing"></a>UseMsmqTracing  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Bu bağlama tarafından işlenen iletilerin izlenip izlenmeyeceğini belirten bir Boole değeri.  
  
### <a name="usesourcejournal"></a>UseSourceJournal  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Bu bağlama tarafından işlenen iletilerin kopyalarının kaynak günlük kuyruğunda depolanması gerekip gerekmediğini belirten bir Boole değeri.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.MsmqBindingBase>
