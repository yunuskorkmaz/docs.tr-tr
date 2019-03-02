---
title: IXCLRDataMethodInstance arabirimi
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
ms.openlocfilehash: 03be79e6300afa6d25a005b0a21b8c2bf15d27be
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202281"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="80448-102">IXCLRDataMethodInstance arabirimi</span><span class="sxs-lookup"><span data-stu-id="80448-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="80448-103">Metot örneği hakkında bilgi sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="80448-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="80448-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="80448-104">Methods</span></span>

| <span data-ttu-id="80448-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="80448-105">Method</span></span>                                                                                                                  | <span data-ttu-id="80448-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80448-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="80448-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="80448-107">GetILAddressMap</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="80448-108">IL adresi eşleme bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="80448-108">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="80448-109">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="80448-109">GetRepresentativeEntryAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="80448-110">Bir yöntem için tüm olası girdi noktalarını native derlemesi için en iyi temsil giriş noktası adresi alır.</span><span class="sxs-lookup"><span data-stu-id="80448-110">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |


## <a name="remarks"></a><span data-ttu-id="80448-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80448-111">Remarks</span></span>

<span data-ttu-id="80448-112">Bu arabirim, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="80448-112">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="80448-113">Ancak, bu, türetilen bir COM arabirimidir `IUnknown` GUID'e sahip `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` normal COM mekanizmalar aracılığıyla edinilebilir.</span><span class="sxs-lookup"><span data-stu-id="80448-113">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="80448-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80448-114">Requirements</span></span>

<span data-ttu-id="80448-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80448-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="80448-116">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="80448-116">**Header:** None</span></span>  
<span data-ttu-id="80448-117">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="80448-117">**Library:** None</span></span>  
<span data-ttu-id="80448-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="80448-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="80448-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80448-119">See also</span></span>

- [<span data-ttu-id="80448-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="80448-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="80448-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="80448-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
