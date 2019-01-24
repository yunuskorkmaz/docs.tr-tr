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
ms.openlocfilehash: 6bfa846aa66345e23e085ca148c7e3f492c529f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576349"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="e4828-102">GetHashFromBlob İşlevi</span><span class="sxs-lookup"><span data-stu-id="e4828-102">GetHashFromBlob Function</span></span>
<span data-ttu-id="e4828-103">Derleme karması belirtilen karma algoritması kullanılarak belirtilen bellek adresinde alır.</span><span class="sxs-lookup"><span data-stu-id="e4828-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="e4828-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="e4828-104">This function has been deprecated.</span></span> <span data-ttu-id="e4828-105">Kullanım [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="e4828-105">Use the [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4828-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4828-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4828-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4828-107">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="e4828-108">[in] Adres karma hale getirilecek bellek bloğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e4828-108">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="e4828-109">[in] Uzunluğu, bayt cinsinden bellek bloğu.</span><span class="sxs-lookup"><span data-stu-id="e4828-109">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="e4828-110">[out içinde] Sabit karma algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4828-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="e4828-111">Sıfır varsayılan algoritma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4828-111">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="e4828-112">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="e4828-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="e4828-113">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="e4828-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="e4828-114">[out] Döndürülen bayt cinsinden boyutu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="e4828-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4828-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4828-115">Requirements</span></span>  
 <span data-ttu-id="e4828-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4828-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4828-117">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e4828-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e4828-118">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e4828-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e4828-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4828-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4828-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4828-120">See also</span></span>
- [<span data-ttu-id="e4828-121">GetHashFromBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4828-121">GetHashFromBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)
- [<span data-ttu-id="e4828-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4828-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
