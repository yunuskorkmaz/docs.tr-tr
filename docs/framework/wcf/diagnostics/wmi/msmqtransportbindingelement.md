---
title: MsmqTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0c2c5d54050216c91a318a407341c4ffb9cb687
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
