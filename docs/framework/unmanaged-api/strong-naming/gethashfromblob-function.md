---
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
ms.openlocfilehash: d1027aea1d800bda1654b223fec992aa70efd4b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140717"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="83cd2-102">GetHashFromBlob İşlevi</span><span class="sxs-lookup"><span data-stu-id="83cd2-102">GetHashFromBlob Function</span></span>

<span data-ttu-id="83cd2-103">Belirtilen karma algoritmasını kullanarak, belirtilen bellek adresindeki derlemenin karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="83cd2-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>

<span data-ttu-id="83cd2-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="83cd2-104">This function has been deprecated.</span></span> <span data-ttu-id="83cd2-105">Bunun yerine [ICLRStrongName:: GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="83cd2-105">Use the [ICLRStrongName::GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="83cd2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83cd2-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="83cd2-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83cd2-107">Parameters</span></span>

`pbBlob`\
<span data-ttu-id="83cd2-108">'ndaki Karma hale getirilen bellek bloğunun adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="83cd2-108">[in] A pointer to the address of the memory block to be hashed.</span></span>

`cchBlob`\
<span data-ttu-id="83cd2-109">'ndaki Bellek bloğunun bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="83cd2-109">[in] The length, in bytes, of the memory block.</span></span>

`piHashAlg`\
<span data-ttu-id="83cd2-110">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="83cd2-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="83cd2-111">Varsayılan algoritma için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="83cd2-111">Use zero for the default algorithm.</span></span>

`pbHash`\
<span data-ttu-id="83cd2-112">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="83cd2-112">[out] The returned hash buffer.</span></span>

`cchHash`\
<span data-ttu-id="83cd2-113">'ndaki İstenen en büyük boyut `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="83cd2-113">[in] The requested maximum size of `pbHash`.</span></span>

`pchHash`\
<span data-ttu-id="83cd2-114">dışı Döndürülen `pbHash`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="83cd2-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>

## <a name="requirements"></a><span data-ttu-id="83cd2-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83cd2-115">Requirements</span></span>

<span data-ttu-id="83cd2-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83cd2-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="83cd2-117">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="83cd2-117">**Header:** StrongName.h</span></span>

<span data-ttu-id="83cd2-118">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="83cd2-118">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="83cd2-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83cd2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="83cd2-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83cd2-120">See also</span></span>

- [<span data-ttu-id="83cd2-121">GetHashFromBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83cd2-121">GetHashFromBlob Method</span></span>](../hosting/iclrstrongname-gethashfromblob-method.md)
- [<span data-ttu-id="83cd2-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83cd2-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
