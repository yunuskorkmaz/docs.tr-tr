---
title: ConnectionGroup Sınıfı
description: ServicePoint bağlamdaki bağlantıları gruplandıran ve .NET 'teki ağ kaynaklarına yönelik bağlamı korumak için kullanılan ConnectionGroup sınıfı hakkında bilgi edinin.
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ConnectionGroup
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 25c08217-fdeb-44b9-9cd6-1b4955d6e602
ms.openlocfilehash: 7121713b26880f2490b40d59d92d431a567519b3
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989816"
---
# <a name="connectiongroup-class"></a><span data-ttu-id="38275-103">ConnectionGroup Sınıfı</span><span class="sxs-lookup"><span data-stu-id="38275-103">ConnectionGroup Class</span></span>

<span data-ttu-id="38275-104">`ConnectionGroup`Sınıfı, bağlamdaki bağlantıların bir listesini gruplandırır <xref:System.Net.ServicePoint> ve ağ kaynaklarının bağlamını korumak için kullanılır (örneğin, proxy 'ler ve ayrı istemciler).</span><span class="sxs-lookup"><span data-stu-id="38275-104">The `ConnectionGroup` class groups a list of connections within the <xref:System.Net.ServicePoint> context and is used to maintain context for network resources (for example, proxies and separate clients).</span></span>

## <a name="syntax"></a><span data-ttu-id="38275-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="38275-105">Syntax</span></span>
  
```csharp  
internal class ConnectionGroup
```

> [!WARNING]
> <span data-ttu-id="38275-106">`ConnectionGroup`Sınıfı dahili ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="38275-106">The `ConnectionGroup` class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="38275-107">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="38275-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="38275-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38275-108">Requirements</span></span>

<span data-ttu-id="38275-109">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="38275-109">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="38275-110">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="38275-110">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="38275-111">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="38275-111">**.NET Framework versions:** Available since 2.0.</span></span>
