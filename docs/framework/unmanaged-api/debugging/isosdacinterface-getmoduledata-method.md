---
title: ISOSDacInterface::GetModuleData yöntemi
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetModuleData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetModuleData Method
helpviewer.keywords:
- ISOSDacInterface::GetModuleData Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 128af261c429228c97d952f1f8d382f46306f711
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229322"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="14b5f-102">ISOSDacInterface::GetModuleData yöntemi</span><span class="sxs-lookup"><span data-stu-id="14b5f-102">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="14b5f-103">Belirli bir adreste yüklü modülü karşılık gelen verileri getirir.</span><span class="sxs-lookup"><span data-stu-id="14b5f-103">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="14b5f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14b5f-104">Syntax</span></span>

```
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a><span data-ttu-id="14b5f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="14b5f-105">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="14b5f-106">[in] Modül için daha fazla bilgi almak için adresi.</span><span class="sxs-lookup"><span data-stu-id="14b5f-106">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="14b5f-107">[out] [DacpModuleData yapısı](dacpmoduledata-structure.md) yüklenen bir modülün bilgilerini tutacak.</span><span class="sxs-lookup"><span data-stu-id="14b5f-107">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>

## <a name="remarks"></a><span data-ttu-id="14b5f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14b5f-108">Remarks</span></span>

<span data-ttu-id="14b5f-109">Sağlanan yöntem parçasıdır `ISOSDacInterface` arabirim ve sanal yöntem tablosunu 13 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="14b5f-109">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 13th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="14b5f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14b5f-110">Requirements</span></span>

<span data-ttu-id="14b5f-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14b5f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="14b5f-112">**Üst bilgi:** Yok.</span><span class="sxs-lookup"><span data-stu-id="14b5f-112">**Header:** None</span></span>  
<span data-ttu-id="14b5f-113">**Kitaplığı:** Yok.</span><span class="sxs-lookup"><span data-stu-id="14b5f-113">**Library:** None</span></span>  
<span data-ttu-id="14b5f-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="14b5f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="14b5f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14b5f-115">See also</span></span>

- [<span data-ttu-id="14b5f-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="14b5f-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="14b5f-117">ISOSDacInterface arabirimi</span><span class="sxs-lookup"><span data-stu-id="14b5f-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)