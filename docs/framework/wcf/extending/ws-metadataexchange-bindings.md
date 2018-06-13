---
title: WS-MetadataExchange Bağlamaları
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 384e5bb05ba4263f245f6901b84e2388ea19bd73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488630"
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="87906-102">WS-MetadataExchange Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="87906-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="87906-103">Bu konu, çeşitli taşımaları için varsayılan meta veri exchange bağlamaları nasıl oluşturulur açıklar.</span><span class="sxs-lookup"><span data-stu-id="87906-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="87906-104">Varsayılan bağlamaları</span><span class="sxs-lookup"><span data-stu-id="87906-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="87906-105">Varsayılan bağlama adı</span><span class="sxs-lookup"><span data-stu-id="87906-105">Default Binding Name</span></span>|<span data-ttu-id="87906-106">Bağlama nasıl oluşturulur</span><span class="sxs-lookup"><span data-stu-id="87906-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="87906-107">MexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="87906-107">MexHttpBinding</span></span>|<span data-ttu-id="87906-108">A <xref:System.ServiceModel.WSHttpBinding> ile aktarım düzeyinde güvenlik devre dışı.</span><span class="sxs-lookup"><span data-stu-id="87906-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="87906-109">MexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="87906-109">MexHttpsBinding</span></span>|<span data-ttu-id="87906-110">A <xref:System.ServiceModel.WSHttpBinding> aktarım düzeyinde güvenlik destekler.</span><span class="sxs-lookup"><span data-stu-id="87906-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="87906-111">MexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="87906-111">MexNamedPipeBinding</span></span>|<span data-ttu-id="87906-112">A <xref:System.ServiceModel.Channels.CustomBinding> ile bir <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> varsayılan değerler kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="87906-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="87906-113">MexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="87906-113">MexTcpBinding</span></span>|<span data-ttu-id="87906-114">A <xref:System.ServiceModel.Channels.CustomBinding> ile bir <xref:System.ServiceModel.Channels.TcpTransportBindingElement> varsayılan değerler kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="87906-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
