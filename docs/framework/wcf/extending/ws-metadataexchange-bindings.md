---
title: WS-MetadataExchange Bağlamaları
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 94f0ba602cd1f58f5491a44a64e24be8ea52895b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293994"
---
# <a name="ws-metadataexchange-bindings"></a>WS-MetadataExchange Bağlamaları

Bu konu, çeşitli aktarımlar için varsayılan meta veri değişimi bağlamalarının nasıl oluşturulduğunu açıklar.  
  
## <a name="the-default-bindings"></a>Varsayılan bağlamalar  
  
|Varsayılan bağlama adı|Bağlama nasıl oluşturulur?|  
|--------------------------|------------------------------------|  
|mexHttpBinding|<xref:System.ServiceModel.WSHttpBinding>Aktarım düzeyi güvenliği devre dışı olan bir.|  
|mexHttpsBinding|<xref:System.ServiceModel.WSHttpBinding>Aktarım düzeyi güvenliği destekleyen bir.|  
|mexNamedPipeBinding|<xref:System.ServiceModel.Channels.CustomBinding> <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> Varsayılan değerleri kullanarak bir ile.|  
|mexTcpBinding|<xref:System.ServiceModel.Channels.CustomBinding> <xref:System.ServiceModel.Channels.TcpTransportBindingElement> Varsayılan değerleri kullanan bir.|
