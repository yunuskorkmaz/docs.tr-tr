---
title: ISOSDacInterface arabirimi
ms.date: 02/01/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ccaf479fc4fb90007b4999e95ee03bdd0529321e
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827935"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="ab6c7-102">ISOSDacInterface arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab6c7-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="ab6c7-103">Verilere erişmek için yardımcı yöntemleri sağlar `SOS`.</span><span class="sxs-lookup"><span data-stu-id="ab6c7-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="ab6c7-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ab6c7-104">Methods</span></span>

| <span data-ttu-id="ab6c7-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ab6c7-105">Method</span></span>                                                                                                               | <span data-ttu-id="ab6c7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab6c7-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="ab6c7-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="ab6c7-107">GetMethodDescData</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="ab6c7-108">Verileri için belirli MethodDesc işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="ab6c7-108">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="ab6c7-109">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="ab6c7-109">GetMethodDescPtrFromIP</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="ab6c7-110">Belirtilen yerel yönerge adresini içeren yöntemi karşılık gelen MethodDesc işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="ab6c7-110">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="ab6c7-111">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="ab6c7-111">GetModuleData</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="ab6c7-112">Belirli bir adreste yüklü modülü karşılık gelen verileri getirir.</span><span class="sxs-lookup"><span data-stu-id="ab6c7-112">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="ab6c7-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab6c7-113">Remarks</span></span>

<span data-ttu-id="ab6c7-114">Bu arabirim, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="ab6c7-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="ab6c7-115">Ancak, bu, türetilen bir COM arabirimidir `IUnknown` GUID'e sahip `436f00f2-b42a-4b9f-870c-e73db66ae930` normal COM mekanizmalar aracılığıyla edinilebilir.</span><span class="sxs-lookup"><span data-stu-id="ab6c7-115">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="ab6c7-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab6c7-116">Requirements</span></span>

<span data-ttu-id="ab6c7-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab6c7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ab6c7-118">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="ab6c7-118">**Header:** None</span></span>  
<span data-ttu-id="ab6c7-119">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="ab6c7-119">**Library:** None</span></span>  
<span data-ttu-id="ab6c7-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ab6c7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ab6c7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab6c7-121">See also</span></span>

- [<span data-ttu-id="ab6c7-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ab6c7-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="ab6c7-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ab6c7-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
