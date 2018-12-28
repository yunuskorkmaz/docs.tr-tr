---
title: WS-MetadataExchange Bağlamaları
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 03e6e6d5ee7e69b397acd0f51b8037f02c1804ec
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2018
ms.locfileid: "53767354"
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="ffacd-102">WS-MetadataExchange Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="ffacd-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="ffacd-103">Bu konuda çeşitli taşımaları için varsayılan meta veri değişimi bağlamaları nasıl oluşturulduğu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ffacd-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="ffacd-104">Varsayılan bağlamaları</span><span class="sxs-lookup"><span data-stu-id="ffacd-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="ffacd-105">Varsayılan bağlama adı</span><span class="sxs-lookup"><span data-stu-id="ffacd-105">Default Binding Name</span></span>|<span data-ttu-id="ffacd-106">Bağlama nasıl oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ffacd-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="ffacd-107">mexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="ffacd-107">mexHttpBinding</span></span>|<span data-ttu-id="ffacd-108">A <xref:System.ServiceModel.WSHttpBinding> aktarım düzeyi güvenlik devre dışı.</span><span class="sxs-lookup"><span data-stu-id="ffacd-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="ffacd-109">mexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="ffacd-109">mexHttpsBinding</span></span>|<span data-ttu-id="ffacd-110">A <xref:System.ServiceModel.WSHttpBinding> , aktarım düzeyi güvenlik destekler.</span><span class="sxs-lookup"><span data-stu-id="ffacd-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="ffacd-111">mexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="ffacd-111">mexNamedPipeBinding</span></span>|<span data-ttu-id="ffacd-112">A <xref:System.ServiceModel.Channels.CustomBinding> ile bir <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> varsayılan değerler kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="ffacd-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="ffacd-113">mexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="ffacd-113">mexTcpBinding</span></span>|<span data-ttu-id="ffacd-114">A <xref:System.ServiceModel.Channels.CustomBinding> ile bir <xref:System.ServiceModel.Channels.TcpTransportBindingElement> varsayılan değerler kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="ffacd-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
