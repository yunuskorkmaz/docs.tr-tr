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
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="e9b14-102">WS-MetadataExchange Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="e9b14-102">WS-MetadataExchange Bindings</span></span>

<span data-ttu-id="e9b14-103">Bu konu, çeşitli aktarımlar için varsayılan meta veri değişimi bağlamalarının nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="e9b14-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="e9b14-104">Varsayılan bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e9b14-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="e9b14-105">Varsayılan bağlama adı</span><span class="sxs-lookup"><span data-stu-id="e9b14-105">Default Binding Name</span></span>|<span data-ttu-id="e9b14-106">Bağlama nasıl oluşturulur?</span><span class="sxs-lookup"><span data-stu-id="e9b14-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="e9b14-107">mexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e9b14-107">mexHttpBinding</span></span>|<span data-ttu-id="e9b14-108"><xref:System.ServiceModel.WSHttpBinding>Aktarım düzeyi güvenliği devre dışı olan bir.</span><span class="sxs-lookup"><span data-stu-id="e9b14-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="e9b14-109">mexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="e9b14-109">mexHttpsBinding</span></span>|<span data-ttu-id="e9b14-110"><xref:System.ServiceModel.WSHttpBinding>Aktarım düzeyi güvenliği destekleyen bir.</span><span class="sxs-lookup"><span data-stu-id="e9b14-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="e9b14-111">mexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="e9b14-111">mexNamedPipeBinding</span></span>|<span data-ttu-id="e9b14-112"><xref:System.ServiceModel.Channels.CustomBinding> <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> Varsayılan değerleri kullanarak bir ile.</span><span class="sxs-lookup"><span data-stu-id="e9b14-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="e9b14-113">mexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="e9b14-113">mexTcpBinding</span></span>|<span data-ttu-id="e9b14-114"><xref:System.ServiceModel.Channels.CustomBinding> <xref:System.ServiceModel.Channels.TcpTransportBindingElement> Varsayılan değerleri kullanan bir.</span><span class="sxs-lookup"><span data-stu-id="e9b14-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
