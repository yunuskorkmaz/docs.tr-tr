---
title: DacpGetModuleAddress::Request yöntemi
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1b69a3385743e948dd52dee75be2f975066c5f85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542606"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="9d59c-102">DacpGetModuleAddress::Request yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d59c-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="9d59c-103">Belirtilen çalışma zamanı yapısı yapısından doldurmak için bir istek gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="9d59c-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9d59c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d59c-104">Syntax</span></span>

```
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

### <a name="parameters"></a><span data-ttu-id="9d59c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d59c-105">Parameters</span></span>

<span data-ttu-id="9d59c-106">`pDataModule` [in] Çekirdek veri modülü için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9d59c-106">`pDataModule` [in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d59c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d59c-107">Remarks</span></span>

<span data-ttu-id="9d59c-108">Bu yapı, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="9d59c-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="9d59c-109">Kullanmak için uygulama taklit etmek için en kolay yolu şöyledir:</span><span class="sxs-lookup"><span data-stu-id="9d59c-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="9d59c-110">Arama öğesinden alınan değer döndürmek `Request` metodunda `IXCLRDataModule*` parametre şu parametrelerle: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="9d59c-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>


## <a name="requirements"></a><span data-ttu-id="9d59c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d59c-111">Requirements</span></span>

<span data-ttu-id="9d59c-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d59c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="9d59c-113">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="9d59c-113">**Header:** None</span></span>     
<span data-ttu-id="9d59c-114">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="9d59c-114">**Library:** None</span></span>  
<span data-ttu-id="9d59c-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9d59c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9d59c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d59c-116">See also</span></span>

- [<span data-ttu-id="9d59c-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9d59c-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="9d59c-118">DacpGetModuleAddress arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d59c-118">DacpGetModuleAddress Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md)
