---
title: IXCLRDataMethodInstance arabirimi
ms.date: 01/16/2019
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
ms.openlocfilehash: 5bf724bc76591ae59c073b5b9a788ca065f51dc0
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416133"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="c55db-102">IXCLRDataMethodInstance arabirimi</span><span class="sxs-lookup"><span data-stu-id="c55db-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="c55db-103">Metot örneği hakkında bilgi sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c55db-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="c55db-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c55db-104">Methods</span></span>

| <span data-ttu-id="c55db-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c55db-105">Method</span></span>                                                                                                                  | <span data-ttu-id="c55db-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c55db-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="c55db-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="c55db-107">GetILAddressMap</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="c55db-108">IL adresi eşleme bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="c55db-108">Gets the IL to address mapping information.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c55db-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c55db-109">Remarks</span></span>

<span data-ttu-id="c55db-110">Bu arabirim, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="c55db-110">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="c55db-111">Ancak, bu, türetilen bir COM arabirimidir `IUnknown` GUID'e sahip `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` normal COM mekanizmalar aracılığıyla edinilebilir.</span><span class="sxs-lookup"><span data-stu-id="c55db-111">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="c55db-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c55db-112">Requirements</span></span>

<span data-ttu-id="c55db-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c55db-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c55db-114">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="c55db-114">**Header:** None</span></span>  
<span data-ttu-id="c55db-115">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="c55db-115">**Library:** None</span></span>  
<span data-ttu-id="c55db-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c55db-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c55db-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c55db-117">See Also</span></span>

- [<span data-ttu-id="c55db-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c55db-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="c55db-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c55db-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
