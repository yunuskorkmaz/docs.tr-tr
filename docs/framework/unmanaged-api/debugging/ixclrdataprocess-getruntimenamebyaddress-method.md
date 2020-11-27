---
title: 'IXCLRDataProcess:: GetRuntimeNameByAddress yöntemi'
ms.date: 4/27/2020
api.name:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: tommcdon
ms.author: tommcdon
ms.openlocfilehash: 6648bdafe6e5cdd402bcfa02a148c57f0f1e209e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270493"
---
# <a name="ixclrdataprocessgetruntimenamebyaddress-method"></a><span data-ttu-id="b8a3a-102">IXCLRDataProcess:: GetRuntimeNameByAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="b8a3a-102">IXCLRDataProcess::GetRuntimeNameByAddress Method</span></span>

<span data-ttu-id="b8a3a-103">Verilen adres için bir ad alır.</span><span class="sxs-lookup"><span data-stu-id="b8a3a-103">Gets a name for the given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b8a3a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b8a3a-104">Syntax</span></span>

```cpp
HRESULT GetRuntimeNameByAddress(
    [in] CLRDATA_ADDRESS address,
    [in] ULONG32 flags,
    [in] ULONG32 bufLen,
    [out] ULONG32 *nameLen,
    [out, size_is(bufLen)] WCHAR nameBuf[],
    [out] CLRDATA_ADDRESS* displacement
);
```

## <a name="parameters"></a><span data-ttu-id="b8a3a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b8a3a-105">Parameters</span></span>

`address`\
<span data-ttu-id="b8a3a-106">'ndaki `CLRDATA_ADDRESS` Bir kod adresini temsil eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="b8a3a-106">[in] A `CLRDATA_ADDRESS` value that represents a code address.</span></span>

`flags`\
<span data-ttu-id="b8a3a-107">'ndaki ' 0 ' olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b8a3a-107">[in] Set to '0'.</span></span>

`bufLen`\
<span data-ttu-id="b8a3a-108">'ndaki Arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="b8a3a-108">[in] The length of the buffer.</span></span>

`namLen`\
<span data-ttu-id="b8a3a-109">dışı Döndürülen karakter sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b8a3a-109">[out] A pointer to the number of characters returned.</span></span>

`namBuf`\
<span data-ttu-id="b8a3a-110">[Out, size_is ( `bufLen` )] `bufLen` çalışma zamanı adını depolayan uzunluğun giriş arabelleği.</span><span class="sxs-lookup"><span data-stu-id="b8a3a-110">[out, size_is(`bufLen`)] The input buffer of length `bufLen` that stores the runtime name.</span></span>

`displacement`\
<span data-ttu-id="b8a3a-111">dışı `CLRDATA_ADDRESS` Döndürülen sembolün kod kaydırmasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b8a3a-111">[out] A `CLRDATA_ADDRESS` pointer to the code offset of the returned symbol.</span></span>

## <a name="remarks"></a><span data-ttu-id="b8a3a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8a3a-112">Remarks</span></span>

<span data-ttu-id="b8a3a-113">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataProcess` ve sanal yöntem tablosunun 16. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b8a3a-113">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 16th slot of the virtual-method table.</span></span>

> [!NOTE]
> <span data-ttu-id="b8a3a-114">Arabellek ad için yeterince büyük değilse, bu yöntem, `S_FALSE` gerekli arabellek uzunluğuna döndürür ve ayarlar `nameLen` .</span><span class="sxs-lookup"><span data-stu-id="b8a3a-114">If the buffer is not large enough for the name, this method returns `S_FALSE` and sets `nameLen` to the required buffer length.</span></span>

## <a name="requirements"></a><span data-ttu-id="b8a3a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b8a3a-115">Requirements</span></span>

<span data-ttu-id="b8a3a-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="b8a3a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md)</span></span>\
<span data-ttu-id="b8a3a-117">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="b8a3a-117">**Header:** None\</span></span>
<span data-ttu-id="b8a3a-118">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="b8a3a-118">**Library:** None\</span></span>
<span data-ttu-id="b8a3a-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b8a3a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b8a3a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8a3a-120">See also</span></span>

- [<span data-ttu-id="b8a3a-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b8a3a-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="b8a3a-122">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b8a3a-122">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
