---
description: 'Şu konuda daha fazla bilgi edinin: ısosdacınterface:: Getmethoddescptrfromıp yöntemi'
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
ms.openlocfilehash: 8d7c7071b7b3fc520faea71c8d7792317745cfde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790418"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="1a33f-103">Iosdacınterface:: Getmethoddescptrfromıp yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a33f-103">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="1a33f-104">Verilen yerel yönerge adresini içeren yöntemi karşılık gelen MethodDesc işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="1a33f-104">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1a33f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a33f-105">Syntax</span></span>

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="1a33f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a33f-106">Parameters</span></span>

`ip`\
<span data-ttu-id="1a33f-107">'ndaki Çalışma zamanında yöntemi içindeki bir adres.</span><span class="sxs-lookup"><span data-stu-id="1a33f-107">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="1a33f-108">dışı `MethodDesc` Belirli yöntemin adresi.</span><span class="sxs-lookup"><span data-stu-id="1a33f-108">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a33f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a33f-109">Remarks</span></span>

<span data-ttu-id="1a33f-110">Belirtilen yöntem [ `ISOSDacInterface` arabirimin](isosdacinterface-interface.md) bir parçasıdır ve sanal yöntem tablosunun 22 yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="1a33f-110">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 22nd slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="1a33f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a33f-111">Requirements</span></span>

<span data-ttu-id="1a33f-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a33f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1a33f-113">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="1a33f-113">**Header:** None</span></span>  
<span data-ttu-id="1a33f-114">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="1a33f-114">**Library:** None</span></span>  
<span data-ttu-id="1a33f-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1a33f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1a33f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a33f-116">See also</span></span>

- [<span data-ttu-id="1a33f-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1a33f-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="1a33f-118">ISOSDacInterface Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a33f-118">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
