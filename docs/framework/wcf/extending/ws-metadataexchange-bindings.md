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
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="9cd08-102">WS-MetadataExchange Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="9cd08-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="9cd08-103">Bu konuda çeşitli taşımaları için varsayılan meta veri değişimi bağlamaları nasıl oluşturulduğu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9cd08-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="9cd08-104">Varsayılan bağlamaları</span><span class="sxs-lookup"><span data-stu-id="9cd08-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="9cd08-105">Varsayılan bağlama adı</span><span class="sxs-lookup"><span data-stu-id="9cd08-105">Default Binding Name</span></span>|<span data-ttu-id="9cd08-106">Bağlama nasıl oluşturulur</span><span class="sxs-lookup"><span data-stu-id="9cd08-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="9cd08-107">mexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="9cd08-107">mexHttpBinding</span></span>|<span data-ttu-id="9cd08-108">A <xref:System.ServiceModel.WSHttpBinding> aktarım düzeyi güvenlik devre dışı.</span><span class="sxs-lookup"><span data-stu-id="9cd08-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="9cd08-109">mexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="9cd08-109">mexHttpsBinding</span></span>|<span data-ttu-id="9cd08-110">A <xref:System.ServiceModel.WSHttpBinding> , aktarım düzeyi güvenlik destekler.</span><span class="sxs-lookup"><span data-stu-id="9cd08-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="9cd08-111">mexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="9cd08-111">mexNamedPipeBinding</span></span>|<span data-ttu-id="9cd08-112">A <xref:System.ServiceModel.Channels.CustomBinding> ile bir <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> varsayılan değerler kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="9cd08-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="9cd08-113">mexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="9cd08-113">mexTcpBinding</span></span>|<span data-ttu-id="9cd08-114">A <xref:System.ServiceModel.Channels.CustomBinding> ile bir <xref:System.ServiceModel.Channels.TcpTransportBindingElement> varsayılan değerler kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="9cd08-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
