---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 3c69b73cc05a56a7556630de0f83675590442293
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274159"
---
# <a name="connectionorientedtransportbindingelement"></a>ConnectionOrientedTransportBindingElement

ConnectionOrientedTransportBindingElement  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class ConnectionOrientedTransportBindingElement : TransportBindingElement  
{  
  datetime ChannelInitializationTimeout;  
  sint32 ConnectionBufferSize;  
  string HostNameComparisonMode;  
  sint32 MaxBufferSize;  
  datetime MaxOutputDelay;  
  sint32 MaxPendingAccepts;  
  sint32 MaxPendingConnections;  
  string TransferMode;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 ConnectionOrientedTransportBindingElement sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 ConnectionOrientedTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="channelinitializationtimeout"></a>ChannelInitializationTimeout  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Zaman aşımından önce kanal başlatmasının ne kadar süreyle tamamlanmasını belirten TimeSpan.  
  
### <a name="connectionbuffersize"></a>ConnectionBufferSize  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 İstemci veya hizmetten alınan bir seri hale getirilmiş ileti öbeğini iletmek için kullanılan arabelleğin boyutu.  
  
### <a name="hostnamecomparisonmode"></a>HostNameComparisonMode  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 URI üzerinde eşleştirilirken, ana bilgisayar adının hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer.  
  
### <a name="maxbuffersize"></a>MaxBufferSize  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Kullanılacak arabelleğin en büyük boyutu.  
  
### <a name="maxoutputdelay"></a>MaxOutputDelay  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 İleti öbeğinin veya bir tam iletinin, gönderilmeden önce bellekte ara belleğe kalabileceği en uzun zaman aralığı.  
  
### <a name="maxpendingaccepts"></a>MaxPendingAccepts  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Hizmette gelen bağlantıları işlemek için kullanılabilen, bekleyen zaman uyumsuz kabul iş parçacığı sayısı üst sınırı.  
  
### <a name="maxpendingconnections"></a>MaxPendingConnections  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Beklemedeki bağlantı sayısı üst sınırı.  
  
### <a name="transfermode"></a>TransferMode  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 İletilerin arabelleğe alınıp alınmayacağını veya bağlantı yönelimli aktarımla birlikte akışa alınıp alınmayacağını belirten bir değer.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
