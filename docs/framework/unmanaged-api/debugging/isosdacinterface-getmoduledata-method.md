---
description: ': Isosdacınterface:: GetModuleData yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: c01f55d55d5ee9082dee4b3adb3022bb17807aa2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790392"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="192ff-103">Iosdacınterface:: GetModuleData yöntemi</span><span class="sxs-lookup"><span data-stu-id="192ff-103">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="192ff-104">Verilen bir adreste yüklü olan modüle karşılık gelen verileri getirir.</span><span class="sxs-lookup"><span data-stu-id="192ff-104">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="192ff-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="192ff-105">Syntax</span></span>

```cpp
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a><span data-ttu-id="192ff-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="192ff-106">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="192ff-107">'ndaki Bilgi alınacak modülün adresi.</span><span class="sxs-lookup"><span data-stu-id="192ff-107">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="192ff-108">dışı Yüklü modülün bilgilerini tutacak olan [Dadcpmoduledata yapısı](dacpmoduledata-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="192ff-108">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>

## <a name="remarks"></a><span data-ttu-id="192ff-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="192ff-109">Remarks</span></span>

<span data-ttu-id="192ff-110">Belirtilen yöntem arabirimin bir parçasıdır `ISOSDacInterface` ve sanal yöntem tablosunun 14 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="192ff-110">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 14th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="192ff-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="192ff-111">Requirements</span></span>

<span data-ttu-id="192ff-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="192ff-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="192ff-113">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="192ff-113">**Header:** None</span></span>  
<span data-ttu-id="192ff-114">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="192ff-114">**Library:** None</span></span>  
<span data-ttu-id="192ff-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="192ff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="192ff-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="192ff-116">See also</span></span>

- [<span data-ttu-id="192ff-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="192ff-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="192ff-118">ISOSDacInterface Arabirimi</span><span class="sxs-lookup"><span data-stu-id="192ff-118">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
