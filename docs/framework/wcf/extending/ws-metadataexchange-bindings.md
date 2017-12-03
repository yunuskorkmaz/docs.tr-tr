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
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="225dd-102">WS-MetadataExchange Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="225dd-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="225dd-103">Bu konu, çeşitli taşımaları için varsayılan meta veri exchange bağlamaları nasıl oluşturulur açıklar.</span><span class="sxs-lookup"><span data-stu-id="225dd-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="225dd-104">Varsayılan bağlamaları</span><span class="sxs-lookup"><span data-stu-id="225dd-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="225dd-105">Varsayılan bağlama adı</span><span class="sxs-lookup"><span data-stu-id="225dd-105">Default Binding Name</span></span>|<span data-ttu-id="225dd-106">Bağlama nasıl oluşturulur</span><span class="sxs-lookup"><span data-stu-id="225dd-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="225dd-107">MexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="225dd-107">MexHttpBinding</span></span>|<span data-ttu-id="225dd-108">A <xref:System.ServiceModel.WSHttpBinding> ile aktarım düzeyinde güvenlik devre dışı.</span><span class="sxs-lookup"><span data-stu-id="225dd-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="225dd-109">MexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="225dd-109">MexHttpsBinding</span></span>|<span data-ttu-id="225dd-110">A <xref:System.ServiceModel.WSHttpBinding> aktarım düzeyinde güvenlik destekler.</span><span class="sxs-lookup"><span data-stu-id="225dd-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="225dd-111">MexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="225dd-111">MexNamedPipeBinding</span></span>|<span data-ttu-id="225dd-112">A <xref:System.ServiceModel.Channels.CustomBinding> ile bir <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> varsayılan değerler kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="225dd-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="225dd-113">MexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="225dd-113">MexTcpBinding</span></span>|<span data-ttu-id="225dd-114">A <xref:System.ServiceModel.Channels.CustomBinding> ile bir <xref:System.ServiceModel.Channels.TcpTransportBindingElement> varsayılan değerler kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="225dd-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
