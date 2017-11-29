---
title: "GetHashFromBlob İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromBlob
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromBlob
helpviewer_keywords: GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 360036cd1578c2845f09f92c09d79e44618abe75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="c2bae-102">GetHashFromBlob İşlevi</span><span class="sxs-lookup"><span data-stu-id="c2bae-102">GetHashFromBlob Function</span></span>
<span data-ttu-id="c2bae-103">Derleme karmasını belirtilen karma algoritması kullanılarak belirtilen bellek adresinde alır.</span><span class="sxs-lookup"><span data-stu-id="c2bae-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="c2bae-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="c2bae-104">This function has been deprecated.</span></span> <span data-ttu-id="c2bae-105">Kullanım [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="c2bae-105">Use the [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2bae-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2bae-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="c2bae-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c2bae-107">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="c2bae-108">[in] Karma hale getirilmesi için bellek bloğu adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c2bae-108">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="c2bae-109">[in] Uzunluğu, bayt cinsinden bellek bloğu.</span><span class="sxs-lookup"><span data-stu-id="c2bae-109">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="c2bae-110">[içinde out] Karma algoritmasını belirtir sabiti.</span><span class="sxs-lookup"><span data-stu-id="c2bae-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="c2bae-111">Varsayılan algoritma için sıfır değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c2bae-111">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="c2bae-112">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="c2bae-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="c2bae-113">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="c2bae-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="c2bae-114">[out] Dönen bayt cinsinden boyutu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="c2bae-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2bae-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2bae-115">Requirements</span></span>  
 <span data-ttu-id="c2bae-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2bae-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2bae-117">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c2bae-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c2bae-118">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c2bae-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c2bae-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2bae-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2bae-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c2bae-120">See Also</span></span>  
 [<span data-ttu-id="c2bae-121">GetHashFromBlob yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2bae-121">GetHashFromBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)  
 [<span data-ttu-id="c2bae-122">Iclrstrongname arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2bae-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
