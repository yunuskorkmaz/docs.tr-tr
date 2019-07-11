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
ms.openlocfilehash: 97b297def9fba329ff6d9573f7b2e7cc811273f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764712"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="092fd-102">ISOSDacInterface::GetModuleData yöntemi</span><span class="sxs-lookup"><span data-stu-id="092fd-102">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="092fd-103">Belirli bir adreste yüklü modülü karşılık gelen verileri getirir.</span><span class="sxs-lookup"><span data-stu-id="092fd-103">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="092fd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="092fd-104">Syntax</span></span>

```cpp
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a><span data-ttu-id="092fd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="092fd-105">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="092fd-106">[in] Modül için daha fazla bilgi almak için adresi.</span><span class="sxs-lookup"><span data-stu-id="092fd-106">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="092fd-107">[out] [DacpModuleData yapısı](dacpmoduledata-structure.md) yüklenen bir modülün bilgilerini tutacak.</span><span class="sxs-lookup"><span data-stu-id="092fd-107">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>

## <a name="remarks"></a><span data-ttu-id="092fd-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="092fd-108">Remarks</span></span>

<span data-ttu-id="092fd-109">Sağlanan yöntem parçasıdır `ISOSDacInterface` arabirim ve sanal yöntem tablosunu 13 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="092fd-109">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 13th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="092fd-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="092fd-110">Requirements</span></span>

<span data-ttu-id="092fd-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="092fd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="092fd-112">**Üst bilgi:** Yok.</span><span class="sxs-lookup"><span data-stu-id="092fd-112">**Header:** None</span></span>  
<span data-ttu-id="092fd-113">**Kitaplığı:** Yok.</span><span class="sxs-lookup"><span data-stu-id="092fd-113">**Library:** None</span></span>  
<span data-ttu-id="092fd-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="092fd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="092fd-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="092fd-115">See also</span></span>

- [<span data-ttu-id="092fd-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="092fd-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="092fd-117">ISOSDacInterface arabirimi</span><span class="sxs-lookup"><span data-stu-id="092fd-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
