---
description: 'Daha fazla bilgi edinin: GetHashFromBlob Işlevi'
title: GetHashFromBlob İşlevi
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
ms.openlocfilehash: dc5039e44440afa7a000bc61167faec0e5b6cc84
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736615"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="9abfa-103">GetHashFromBlob İşlevi</span><span class="sxs-lookup"><span data-stu-id="9abfa-103">GetHashFromBlob Function</span></span>

<span data-ttu-id="9abfa-104">Belirtilen karma algoritmasını kullanarak, belirtilen bellek adresindeki derlemenin karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="9abfa-104">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>

<span data-ttu-id="9abfa-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9abfa-105">This function has been deprecated.</span></span> <span data-ttu-id="9abfa-106">Bunun yerine [ICLRStrongName:: GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9abfa-106">Use the [ICLRStrongName::GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="9abfa-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9abfa-107">Syntax</span></span>

```cpp
HRESULT GetHashFromBlob (
    [in]  BYTE    *pbBlob,
    [in]  DWORD   cchBlob,
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE    *pbHash,
    [in]  DWORD   cchHash,
    [out] DWORD   *pchHash
);
```

## <a name="parameters"></a><span data-ttu-id="9abfa-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9abfa-108">Parameters</span></span>

`pbBlob`\
<span data-ttu-id="9abfa-109">'ndaki Karma hale getirilen bellek bloğunun adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9abfa-109">[in] A pointer to the address of the memory block to be hashed.</span></span>

`cchBlob`\
<span data-ttu-id="9abfa-110">'ndaki Bellek bloğunun bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="9abfa-110">[in] The length, in bytes, of the memory block.</span></span>

`piHashAlg`\
<span data-ttu-id="9abfa-111">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="9abfa-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="9abfa-112">Varsayılan algoritma için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="9abfa-112">Use zero for the default algorithm.</span></span>

`pbHash`\
<span data-ttu-id="9abfa-113">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="9abfa-113">[out] The returned hash buffer.</span></span>

`cchHash`\
<span data-ttu-id="9abfa-114">'ndaki İstenen en büyük boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="9abfa-114">[in] The requested maximum size of `pbHash`.</span></span>

`pchHash`\
<span data-ttu-id="9abfa-115">dışı Döndürülen bayt cinsinden boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="9abfa-115">[out] The size, in bytes, of the returned `pbHash`.</span></span>

## <a name="requirements"></a><span data-ttu-id="9abfa-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9abfa-116">Requirements</span></span>

<span data-ttu-id="9abfa-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9abfa-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="9abfa-118">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="9abfa-118">**Header:** StrongName.h</span></span>

<span data-ttu-id="9abfa-119">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9abfa-119">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="9abfa-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9abfa-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9abfa-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9abfa-121">See also</span></span>

- [<span data-ttu-id="9abfa-122">GetHashFromBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9abfa-122">GetHashFromBlob Method</span></span>](../hosting/iclrstrongname-gethashfromblob-method.md)
- [<span data-ttu-id="9abfa-123">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9abfa-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
