---
title: WS-MetadataExchange Bağlamaları
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 03e6e6d5ee7e69b397acd0f51b8037f02c1804ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795484"
---
# <a name="ws-metadataexchange-bindings"></a>WS-MetadataExchange Bağlamaları
Bu konuda çeşitli taşımaları için varsayılan meta veri değişimi bağlamaları nasıl oluşturulduğu açıklanmaktadır.  
  
## <a name="the-default-bindings"></a>Varsayılan bağlamaları  
  
|Varsayılan bağlama adı|Bağlama nasıl oluşturulur|  
|--------------------------|------------------------------------|  
|mexHttpBinding|A <xref:System.ServiceModel.WSHttpBinding> aktarım düzeyi güvenlik devre dışı.|  
|mexHttpsBinding|A <xref:System.ServiceModel.WSHttpBinding> , aktarım düzeyi güvenlik destekler.|  
|mexNamedPipeBinding|A <xref:System.ServiceModel.Channels.CustomBinding> ile bir <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> varsayılan değerler kullanılıyor.|  
|mexTcpBinding|A <xref:System.ServiceModel.Channels.CustomBinding> ile bir <xref:System.ServiceModel.Channels.TcpTransportBindingElement> varsayılan değerler kullanılıyor.|
