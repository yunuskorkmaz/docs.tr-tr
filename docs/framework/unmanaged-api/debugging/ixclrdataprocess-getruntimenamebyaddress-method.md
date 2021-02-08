---
description: 'Daha fazla bilgi edinin: IXCLRDataProcess:: GetRuntimeNameByAddress yöntemi'
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
ms.openlocfilehash: 62d9ae73c216748cc8eb02aedd41cf19f475d071
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800662"
---
# <a name="ixclrdataprocessgetruntimenamebyaddress-method"></a><span data-ttu-id="218f1-103">IXCLRDataProcess:: GetRuntimeNameByAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="218f1-103">IXCLRDataProcess::GetRuntimeNameByAddress Method</span></span>

<span data-ttu-id="218f1-104">Verilen adres için bir ad alır.</span><span class="sxs-lookup"><span data-stu-id="218f1-104">Gets a name for the given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="218f1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="218f1-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="218f1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="218f1-106">Parameters</span></span>

`address`\
<span data-ttu-id="218f1-107">'ndaki `CLRDATA_ADDRESS` Bir kod adresini temsil eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="218f1-107">[in] A `CLRDATA_ADDRESS` value that represents a code address.</span></span>

`flags`\
<span data-ttu-id="218f1-108">'ndaki ' 0 ' olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="218f1-108">[in] Set to '0'.</span></span>

`bufLen`\
<span data-ttu-id="218f1-109">'ndaki Arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="218f1-109">[in] The length of the buffer.</span></span>

`namLen`\
<span data-ttu-id="218f1-110">dışı Döndürülen karakter sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="218f1-110">[out] A pointer to the number of characters returned.</span></span>

`namBuf`\
<span data-ttu-id="218f1-111">[Out, size_is ( `bufLen` )] `bufLen` çalışma zamanı adını depolayan uzunluğun giriş arabelleği.</span><span class="sxs-lookup"><span data-stu-id="218f1-111">[out, size_is(`bufLen`)] The input buffer of length `bufLen` that stores the runtime name.</span></span>

`displacement`\
<span data-ttu-id="218f1-112">dışı `CLRDATA_ADDRESS` Döndürülen sembolün kod kaydırmasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="218f1-112">[out] A `CLRDATA_ADDRESS` pointer to the code offset of the returned symbol.</span></span>

## <a name="remarks"></a><span data-ttu-id="218f1-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="218f1-113">Remarks</span></span>

<span data-ttu-id="218f1-114">Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataProcess` ve sanal yöntem tablosunun 16. yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="218f1-114">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 16th slot of the virtual-method table.</span></span>

> [!NOTE]
> <span data-ttu-id="218f1-115">Arabellek ad için yeterince büyük değilse, bu yöntem, `S_FALSE` gerekli arabellek uzunluğuna döndürür ve ayarlar `nameLen` .</span><span class="sxs-lookup"><span data-stu-id="218f1-115">If the buffer is not large enough for the name, this method returns `S_FALSE` and sets `nameLen` to the required buffer length.</span></span>

## <a name="requirements"></a><span data-ttu-id="218f1-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="218f1-116">Requirements</span></span>

<span data-ttu-id="218f1-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="218f1-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md)</span></span>\
<span data-ttu-id="218f1-118">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="218f1-118">**Header:** None\</span></span>
<span data-ttu-id="218f1-119">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="218f1-119">**Library:** None\</span></span>
<span data-ttu-id="218f1-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="218f1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="218f1-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="218f1-121">See also</span></span>

- [<span data-ttu-id="218f1-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="218f1-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="218f1-123">IXCLRDataProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="218f1-123">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
