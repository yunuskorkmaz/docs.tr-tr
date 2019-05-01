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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d9e7b52c9061a1a7b470f9d4abf735e605087dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000538"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="fffaf-102">GetHashFromBlob İşlevi</span><span class="sxs-lookup"><span data-stu-id="fffaf-102">GetHashFromBlob Function</span></span>

<span data-ttu-id="fffaf-103">Derleme karması belirtilen karma algoritması kullanılarak belirtilen bellek adresinde alır.</span><span class="sxs-lookup"><span data-stu-id="fffaf-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>

<span data-ttu-id="fffaf-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="fffaf-104">This function has been deprecated.</span></span> <span data-ttu-id="fffaf-105">Kullanım [Iclrstrongname::gethashfromblob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="fffaf-105">Use the [ICLRStrongName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="fffaf-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fffaf-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="fffaf-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fffaf-107">Parameters</span></span>

`pbBlob`\
<span data-ttu-id="fffaf-108">[in] Adres karma hale getirilecek bellek bloğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fffaf-108">[in] A pointer to the address of the memory block to be hashed.</span></span>

`cchBlob`\
<span data-ttu-id="fffaf-109">[in] Uzunluğu, bayt cinsinden bellek bloğu.</span><span class="sxs-lookup"><span data-stu-id="fffaf-109">[in] The length, in bytes, of the memory block.</span></span>

`piHashAlg`\
<span data-ttu-id="fffaf-110">[out içinde] Sabit karma algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fffaf-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="fffaf-111">Sıfır varsayılan algoritma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="fffaf-111">Use zero for the default algorithm.</span></span>

`pbHash`\
<span data-ttu-id="fffaf-112">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="fffaf-112">[out] The returned hash buffer.</span></span>

`cchHash`\
<span data-ttu-id="fffaf-113">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="fffaf-113">[in] The requested maximum size of `pbHash`.</span></span>

`pchHash`\
<span data-ttu-id="fffaf-114">[out] Döndürülen bayt cinsinden boyutu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="fffaf-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>

## <a name="requirements"></a><span data-ttu-id="fffaf-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fffaf-115">Requirements</span></span>

<span data-ttu-id="fffaf-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fffaf-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="fffaf-117">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="fffaf-117">**Header:** StrongName.h</span></span>

<span data-ttu-id="fffaf-118">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fffaf-118">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="fffaf-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fffaf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="fffaf-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fffaf-120">See also</span></span>

- [<span data-ttu-id="fffaf-121">GetHashFromBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fffaf-121">GetHashFromBlob Method</span></span>](../hosting/iclrstrongname-gethashfromblob-method.md)
- [<span data-ttu-id="fffaf-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fffaf-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)