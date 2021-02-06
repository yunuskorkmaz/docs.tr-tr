---
description: 'Daha fazla bilgi edinin: WS-MetadataExchange bağlamaları'
title: WS-MetadataExchange Bağlamaları
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 3bcea573ad436a85285fab5657e58defa9113d9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643949"
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
