---
title: ISOSDacInterface::GetMethodDescPtrFromIP yöntemi
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
ms.openlocfilehash: 82c4531ac16e8b4bf7ac45bc01eb7128b9507ab5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358541"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="ba200-102">ISOSDacInterface::GetMethodDescPtrFromIP yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba200-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="ba200-103">Belirtilen yerel yönerge adresini içeren yöntemi karşılık gelen MethodDesc işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="ba200-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ba200-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba200-104">Syntax</span></span>

```
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="ba200-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba200-105">Parameters</span></span>

`ip`\
<span data-ttu-id="ba200-106">[in] Çalışma zamanında yöntemi içinden bir adres.</span><span class="sxs-lookup"><span data-stu-id="ba200-106">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="ba200-107">[out] Adresini `MethodDesc` belirli yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ba200-107">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba200-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba200-108">Remarks</span></span>

<span data-ttu-id="ba200-109">Sağlanan yöntem parçasıdır [ `ISOSDacInterface` arabirimi](isosdacinterface-interface.md) ve sanal yöntem tablosunu 21 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="ba200-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 21st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="ba200-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba200-110">Requirements</span></span>

<span data-ttu-id="ba200-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba200-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ba200-112">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="ba200-112">**Header:** None</span></span>  
<span data-ttu-id="ba200-113">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="ba200-113">**Library:** None</span></span>  
<span data-ttu-id="ba200-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ba200-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ba200-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba200-115">See also</span></span>

- [<span data-ttu-id="ba200-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ba200-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="ba200-117">ISOSDacInterface arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba200-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)