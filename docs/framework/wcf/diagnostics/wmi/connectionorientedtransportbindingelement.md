---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 5ec2ae0db7239ff0c376ab4a8f050cc4f1df4f71
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683982"
---
# <a name="connectionorientedtransportbindingelement"></a>ConnectionOrientedTransportBindingElement
ConnectionOrientedTransportBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 ConnectionOrientedTransportBindingElement sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 ConnectionOrientedTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="channelinitializationtimeout"></a>ChannelInitializationTimeout  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Zaman aşımından önce tamamlamak ne kadar kanal başlatma belirten bir TimeSpan değeri vardır.  
  
### <a name="connectionbuffersize"></a>ConnectionBufferSize  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Bir parça istemci veya hizmet serileştirilmiş ileti iletmek için kullanılan arabellek boyutu.  
  
### <a name="hostnamecomparisonmode"></a>HostNameComparisonMode  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirten bir değer.  
  
### <a name="maxbuffersize"></a>maxBufferSize  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Kullanılacak arabelleğin en büyük boyutu.  
  
### <a name="maxoutputdelay"></a>MaxOutputDelay  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Gönderilen en fazla bir ileti veya tam bir ileti bir öbek kalabileceği edilmeden önce bellekte arabelleğe zaman aralığı.  
  
### <a name="maxpendingaccepts"></a>maxPendingAccepts  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 En fazla sayısını bekleyen zaman uyumsuz hizmet gelen bağlantıları işlemek için kullanılan iş parçacıklarının kabul edin.  
  
### <a name="maxpendingconnections"></a>maxPendingConnections  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Bekleyen bağlantılar maksimum sayısı.  
  
### <a name="transfermode"></a>transferMode  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 İletilerin ara belleğe veya bağlantıya dayalı taşınıp belirten bir değeri.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
