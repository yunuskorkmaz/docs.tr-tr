---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 3b1055e6e2329fd213ae973ad32cdf8014d30a04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="connectionorientedtransportbindingelement"></a>ConnectionOrientedTransportBindingElement
ConnectionOrientedTransportBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 ConnectionOrientedTransportBindingElement sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 ConnectionOrientedTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="channelinitializationtimeout"></a>ChannelInitializationTimeout  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Zaman aşımından önce tamamlamak ne kadar süreyle kanal başlatma belirten timespan sahiptir.  
  
### <a name="connectionbuffersize"></a>ConnectionBufferSize  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 İstemci veya hizmet hattan serileştirilmiş iletide öbeğini iletmek için kullanılan arabelleğin boyutu.  
  
### <a name="hostnamecomparisonmode"></a>hostNameComparisonMode  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer.  
  
### <a name="maxbuffersize"></a>maxBufferSize  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Kullanılacak arabelleğin en büyük boyutu.  
  
### <a name="maxoutputdelay"></a>maxOutputDelay  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 En fazla bellek önce arabelleğe bir ileti veya tam bir ileti öbeğini kalabileceği zaman aralığını gönderilen.  
  
### <a name="maxpendingaccepts"></a>maxPendingAccepts  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 En fazla bekleyen zaman uyumsuz hizmet gelen bağlantıları işlemek için kullanılan iş parçacıklarını kabul edin.  
  
### <a name="maxpendingconnections"></a>maxPendingConnections  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Beklemedeki bağlantı maksimum sayısı.  
  
### <a name="transfermode"></a>transferMode  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 İletilerin ara belleğe veya ile bağlantı yönelimli aktarma akışı olup olmadığını belirten bir değer.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
