---
title: "WS-MetadataExchange Bağlamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7267fa8e71a7bbe202bce9897ea09079307be50
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ws-metadataexchange-bindings"></a>WS-MetadataExchange Bağlamaları
Bu konu, çeşitli taşımaları için varsayılan meta veri exchange bağlamaları nasıl oluşturulur açıklar.  
  
## <a name="the-default-bindings"></a>Varsayılan bağlamaları  
  
|Varsayılan bağlama adı|Bağlama nasıl oluşturulur|  
|--------------------------|------------------------------------|  
|MexHttpBinding|A <xref:System.ServiceModel.WSHttpBinding> ile aktarım düzeyinde güvenlik devre dışı.|  
|MexHttpsBinding|A <xref:System.ServiceModel.WSHttpBinding> aktarım düzeyinde güvenlik destekler.|  
|MexNamedPipeBinding|A <xref:System.ServiceModel.Channels.CustomBinding> ile bir <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> varsayılan değerler kullanılıyor.|  
|MexTcpBinding|A <xref:System.ServiceModel.Channels.CustomBinding> ile bir <xref:System.ServiceModel.Channels.TcpTransportBindingElement> varsayılan değerler kullanılıyor.|
