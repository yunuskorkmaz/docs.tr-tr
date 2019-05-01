---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 706cec5c414197ebabda7939728b95be32582e0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963312"
---
# <a name="msmqtransportbindingelement"></a>MsmqTransportBindingElement
MsmqTransportBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 Hem MsmqTransportBindingElement sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 Hem MsmqTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="maxpoolsize"></a>MaxPoolSize  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 İç MSMQ message nesneleri içeren bir havuz en büyük boyutu.  
  
### <a name="queuetransferprotocol"></a>queueTransferProtocol  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Bu bağlamanın kullandığı sıraya konmuş iletişim kanal taşımasını bildiren bir numaralandırma değeri.  
  
### <a name="useactivedirectory"></a>UseActiveDirectory  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Kuyruk adreslerinin Active Directory kullanılarak dönüştürülüp dönüştürülmeyeceğini gösteren bir Boole değeri döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
