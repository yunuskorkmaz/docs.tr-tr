---
title: IXCLRDataModule arabirimi
ms.date: 01/16/2019
api.name:
- IXCLRDataModule Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule Interface
helpviewer.keywords:
- IXCLRDataModule Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e306834166051ae48fd283d51f18d9458091578f
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416200"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="32aba-102">IXCLRDataModule arabirimi</span><span class="sxs-lookup"><span data-stu-id="32aba-102">IXCLRDataModule Interface</span></span>

<span data-ttu-id="32aba-103">Yüklenen bir modülün hakkında bilgi sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="32aba-103">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="32aba-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="32aba-104">Methods</span></span>

| <span data-ttu-id="32aba-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="32aba-105">Method</span></span>                                                                                                                                | <span data-ttu-id="32aba-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32aba-106">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="32aba-107">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="32aba-107">GetMethodDefinitionByToken</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="32aba-108">Belirli bir metaveri belirteci için karşılık gelen yöntem tanımını alır.</span><span class="sxs-lookup"><span data-stu-id="32aba-108">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="32aba-109">İstek</span><span class="sxs-lookup"><span data-stu-id="32aba-109">Request</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="32aba-110">Modülün verilerle verilen arabelleği doldurmak için istek sayısı.</span><span class="sxs-lookup"><span data-stu-id="32aba-110">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="32aba-111">GetVersionId</span><span class="sxs-lookup"><span data-stu-id="32aba-111">GetVersionId</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="32aba-112">Modülün sürüm kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="32aba-112">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="32aba-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32aba-113">Remarks</span></span>

<span data-ttu-id="32aba-114">Bu arabirim, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="32aba-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="32aba-115">Ancak, bu, türetilen bir COM arabirimidir `IUnknown` GUID'e sahip `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` normal COM mekanizmalar aracılığıyla edinilebilir.</span><span class="sxs-lookup"><span data-stu-id="32aba-115">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="32aba-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32aba-116">Requirements</span></span>

<span data-ttu-id="32aba-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32aba-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="32aba-118">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="32aba-118">**Header:** None</span></span>  
<span data-ttu-id="32aba-119">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="32aba-119">**Library:** None</span></span>  
<span data-ttu-id="32aba-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="32aba-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="32aba-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="32aba-121">See Also</span></span>

- [<span data-ttu-id="32aba-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="32aba-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="32aba-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="32aba-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
