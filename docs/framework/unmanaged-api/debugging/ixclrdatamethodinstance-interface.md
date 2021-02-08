---
description: 'Daha fazla bilgi edinin: IXCLRDataMethodInstance Interface'
title: IXCLRDataMethodInstance Arabirimi
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance Interface
helpviewer.keywords:
- IXCLRDataMethodInstance Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4e9ad57988420ff14b297c693c31c0dc5b3b181c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800792"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="1b152-103">IXCLRDataMethodInstance Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b152-103">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="1b152-104">Bir yöntem örneği hakkındaki bilgileri sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b152-104">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="1b152-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1b152-105">Methods</span></span>

| <span data-ttu-id="1b152-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1b152-106">Method</span></span>                                                                                                                  | <span data-ttu-id="1b152-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b152-107">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="1b152-108">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="1b152-108">GetILAddressMap</span></span>](ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="1b152-109">Eşleme bilgilerini ele almak için Il 'yi alır.</span><span class="sxs-lookup"><span data-stu-id="1b152-109">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="1b152-110">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="1b152-110">GetRepresentativeEntryAddress</span></span>](ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="1b152-111">Bir yöntem için tüm olası giriş noktalarının yerel derlenmesi için en temsili giriş noktası adresini alır.</span><span class="sxs-lookup"><span data-stu-id="1b152-111">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |

## <a name="remarks"></a><span data-ttu-id="1b152-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b152-112">Remarks</span></span>

<span data-ttu-id="1b152-113">Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="1b152-113">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="1b152-114">Ancak, `IUnknown` `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` normal com mekanizmalarından elde edilebilir GUID ile TÜRETILEN bir com arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="1b152-114">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="1b152-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b152-115">Requirements</span></span>

<span data-ttu-id="1b152-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b152-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1b152-117">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="1b152-117">**Header:** None</span></span>  
<span data-ttu-id="1b152-118">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="1b152-118">**Library:** None</span></span>  
<span data-ttu-id="1b152-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1b152-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1b152-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b152-120">See also</span></span>

- [<span data-ttu-id="1b152-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1b152-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="1b152-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1b152-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
