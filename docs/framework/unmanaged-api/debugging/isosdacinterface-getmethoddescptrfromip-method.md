---
title: 'Iosdacınterface:: Getmethoddescptrfromıp yöntemi'
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: c3de9e5ffe23a13c126343c6f74f042bf1239609
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421013"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="83eec-102">Iosdacınterface:: Getmethoddescptrfromıp yöntemi</span><span class="sxs-lookup"><span data-stu-id="83eec-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="83eec-103">Verilen yerel yönerge adresini içeren yöntemi karşılık gelen MethodDesc işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="83eec-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="83eec-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="83eec-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="83eec-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83eec-105">Parameters</span></span>

`ip`\
<span data-ttu-id="83eec-106">'ndaki Çalışma zamanında yöntemi içindeki bir adres.</span><span class="sxs-lookup"><span data-stu-id="83eec-106">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="83eec-107">dışı `MethodDesc`Belirli yöntemin adresi.</span><span class="sxs-lookup"><span data-stu-id="83eec-107">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="83eec-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83eec-108">Remarks</span></span>

<span data-ttu-id="83eec-109">Belirtilen yöntem [ `ISOSDacInterface` arabirimin](isosdacinterface-interface.md) bir parçasıdır ve sanal yöntem tablosunun 22 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="83eec-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 22nd slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="83eec-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83eec-110">Requirements</span></span>

<span data-ttu-id="83eec-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83eec-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="83eec-112">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="83eec-112">**Header:** None</span></span>  
<span data-ttu-id="83eec-113">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="83eec-113">**Library:** None</span></span>  
<span data-ttu-id="83eec-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="83eec-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="83eec-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83eec-115">See also</span></span>

- [<span data-ttu-id="83eec-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="83eec-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="83eec-117">ISOSDacInterface Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83eec-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
