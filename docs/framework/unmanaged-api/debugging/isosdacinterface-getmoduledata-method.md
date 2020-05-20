---
title: 'Iosdacınterface:: GetModuleData yöntemi'
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
ms.openlocfilehash: b302100eb6cbfa83896cd358762c496ea01f7509
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420987"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="45e2c-102">Iosdacınterface:: GetModuleData yöntemi</span><span class="sxs-lookup"><span data-stu-id="45e2c-102">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="45e2c-103">Verilen bir adreste yüklü olan modüle karşılık gelen verileri getirir.</span><span class="sxs-lookup"><span data-stu-id="45e2c-103">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="45e2c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="45e2c-104">Syntax</span></span>

```cpp
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a><span data-ttu-id="45e2c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="45e2c-105">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="45e2c-106">'ndaki Bilgi alınacak modülün adresi.</span><span class="sxs-lookup"><span data-stu-id="45e2c-106">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="45e2c-107">dışı Yüklü modülün bilgilerini tutacak olan [Dadcpmoduledata yapısı](dacpmoduledata-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="45e2c-107">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>

## <a name="remarks"></a><span data-ttu-id="45e2c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45e2c-108">Remarks</span></span>

<span data-ttu-id="45e2c-109">Belirtilen yöntem arabirimin bir parçasıdır `ISOSDacInterface` ve sanal yöntem tablosunun 14 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="45e2c-109">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 14th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="45e2c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45e2c-110">Requirements</span></span>

<span data-ttu-id="45e2c-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45e2c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="45e2c-112">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="45e2c-112">**Header:** None</span></span>  
<span data-ttu-id="45e2c-113">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="45e2c-113">**Library:** None</span></span>  
<span data-ttu-id="45e2c-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="45e2c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="45e2c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45e2c-115">See also</span></span>

- [<span data-ttu-id="45e2c-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="45e2c-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="45e2c-117">ISOSDacInterface Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45e2c-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
