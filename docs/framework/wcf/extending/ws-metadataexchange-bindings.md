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
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="1c0d4-103">WS-MetadataExchange Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="1c0d4-103">WS-MetadataExchange Bindings</span></span>

<span data-ttu-id="1c0d4-104">Bu konu, çeşitli aktarımlar için varsayılan meta veri değişimi bağlamalarının nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="1c0d4-104">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="1c0d4-105">Varsayılan bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1c0d4-105">The Default Bindings</span></span>  
  
|<span data-ttu-id="1c0d4-106">Varsayılan bağlama adı</span><span class="sxs-lookup"><span data-stu-id="1c0d4-106">Default Binding Name</span></span>|<span data-ttu-id="1c0d4-107">Bağlama nasıl oluşturulur?</span><span class="sxs-lookup"><span data-stu-id="1c0d4-107">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="1c0d4-108">mexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="1c0d4-108">mexHttpBinding</span></span>|<span data-ttu-id="1c0d4-109"><xref:System.ServiceModel.WSHttpBinding>Aktarım düzeyi güvenliği devre dışı olan bir.</span><span class="sxs-lookup"><span data-stu-id="1c0d4-109">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="1c0d4-110">mexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="1c0d4-110">mexHttpsBinding</span></span>|<span data-ttu-id="1c0d4-111"><xref:System.ServiceModel.WSHttpBinding>Aktarım düzeyi güvenliği destekleyen bir.</span><span class="sxs-lookup"><span data-stu-id="1c0d4-111">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="1c0d4-112">mexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="1c0d4-112">mexNamedPipeBinding</span></span>|<span data-ttu-id="1c0d4-113"><xref:System.ServiceModel.Channels.CustomBinding> <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> Varsayılan değerleri kullanarak bir ile.</span><span class="sxs-lookup"><span data-stu-id="1c0d4-113">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="1c0d4-114">mexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="1c0d4-114">mexTcpBinding</span></span>|<span data-ttu-id="1c0d4-115"><xref:System.ServiceModel.Channels.CustomBinding> <xref:System.ServiceModel.Channels.TcpTransportBindingElement> Varsayılan değerleri kullanan bir.</span><span class="sxs-lookup"><span data-stu-id="1c0d4-115">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
