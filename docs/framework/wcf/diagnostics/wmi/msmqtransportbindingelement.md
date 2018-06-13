---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 643ab0f30c771f79df8ef7dd885013d5186fba59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485914"
---
# <a name="msmqtransportbindingelement"></a>MsmqTransportBindingElement
MsmqTransportBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 Hem MsmqTransportBindingElement sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 Hem MsmqTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="maxpoolsize"></a>MaxPoolSize  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 İç MSMQ İleti nesneleri içeren havuzu en büyük boyutu.  
  
### <a name="queuetransferprotocol"></a>QueueTransferProtocol  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Bu bağlamayı kullanan kuyruğa alınan iletişim kanalı aktarım gösteren bir numaralandırma değeri.  
  
### <a name="useactivedirectory"></a>UseActiveDirectory  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Active Directory'yi kullanarak sıra adreslerini dönüştürülüp dönüştürülmeyeceğini gösteren bir Boole değeri döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
