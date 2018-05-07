---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: 2f04e6794342d7bd0acd51481efcbeceb04fd459
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="reliablesessionbindingelement"></a>ReliableSessionBindingElement
ReliableSessionBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 ReliableSessionBindingElement sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 ReliableSessionBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="acknowledgementinterval"></a>acknowledgementInterval  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Bir hedef fabrikada oluşturulan güvenilir kanalda ileti kaynağına onay göndermeden önce bekleyeceği zaman aralığı.  
  
### <a name="flowcontrolenabled"></a>flowControlEnabled  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Akış denetimi etkin olup olmadığını belirten bir Boole değeri.  
  
### <a name="inactivitytimeout"></a>InactivityTimeout  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Herhangi bir ileti kanalı hatalı önce göndermemeyi diğer tarafın kanalı göndermemesini en uzun süreyi belirtir.  
  
### <a name="maxpendingchannels"></a>maxPendingChannels  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Kabul edilmesi için dinleyici bekleyebilirsiniz kanal maksimum sayısı.  
  
### <a name="maxretrycount"></a>MaxRetryCount  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Güvenilir bir kanal değil aldığı için bir bildirim arayarak bir ileti yeniden ilettiği için kaç deneme sayısı `Send` temel kanalda.  
  
### <a name="maxtransferwindowsize"></a>maxTransferWindowSize  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Güvenilir oturum maksimum aktarım pencere boyutu.  
  
### <a name="ordered"></a>sıralı  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 İletileri gönderildikleri sırayla gelmesi garanti edilip edilmeyeceğini belirten bir Boole değeri.  
  
### <a name="reliablemessagingversion"></a>reliableMessagingVersion  
 Veri türü: tamsayı  
  
 Erişim türüne: salt okunur  
  
 Güvenilir oturum sırasında kullanılan WS-ReliableMessaging protokol sürümünü belirten bir tamsayı.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
