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
ms.openlocfilehash: cd256250021436e611142de11c3625a21aeec814
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764746"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="0a4b1-102">ISOSDacInterface::GetMethodDescPtrFromIP yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a4b1-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="0a4b1-103">Belirtilen yerel yönerge adresini içeren yöntemi karşılık gelen MethodDesc işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="0a4b1-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0a4b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a4b1-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="0a4b1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a4b1-105">Parameters</span></span>

`ip`\
<span data-ttu-id="0a4b1-106">[in] Çalışma zamanında yöntemi içinden bir adres.</span><span class="sxs-lookup"><span data-stu-id="0a4b1-106">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="0a4b1-107">[out] Adresini `MethodDesc` belirli yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0a4b1-107">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a4b1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a4b1-108">Remarks</span></span>

<span data-ttu-id="0a4b1-109">Sağlanan yöntem parçasıdır [ `ISOSDacInterface` arabirimi](isosdacinterface-interface.md) ve sanal yöntem tablosunu 21 yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="0a4b1-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 21st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="0a4b1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a4b1-110">Requirements</span></span>

<span data-ttu-id="0a4b1-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a4b1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0a4b1-112">**Üst bilgi:** Yok.</span><span class="sxs-lookup"><span data-stu-id="0a4b1-112">**Header:** None</span></span>  
<span data-ttu-id="0a4b1-113">**Kitaplığı:** None</span><span class="sxs-lookup"><span data-stu-id="0a4b1-113">**Library:** None</span></span>  
<span data-ttu-id="0a4b1-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0a4b1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0a4b1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a4b1-115">See also</span></span>

- [<span data-ttu-id="0a4b1-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0a4b1-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="0a4b1-117">ISOSDacInterface arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a4b1-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
