---
title: "GetHashFromHandle İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromHandle
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromHandle
helpviewer_keywords: GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 45acc02645f45446e37935d7fe7a455f4105d8bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="67a52-102">GetHashFromHandle İşlevi</span><span class="sxs-lookup"><span data-stu-id="67a52-102">GetHashFromHandle Function</span></span>
<span data-ttu-id="67a52-103">Belirtilen karma algoritması kullanılarak belirtilen dosya tanıtıcısıyla dosyasının içeriği üzerinden bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="67a52-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="67a52-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="67a52-104">This function has been deprecated.</span></span> <span data-ttu-id="67a52-105">Kullanım [Iclrstrongname::gethashfromhandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="67a52-105">Use the [ICLRStrongName::GetHashFromHandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67a52-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67a52-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67a52-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67a52-107">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="67a52-108">[in] Karma hale getirilmesi için dosya tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="67a52-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="67a52-109">[içinde out] Karma algoritmasını belirtir sabiti.</span><span class="sxs-lookup"><span data-stu-id="67a52-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="67a52-110">Varsayılan algoritma için sıfır değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="67a52-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="67a52-111">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="67a52-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="67a52-112">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="67a52-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="67a52-113">[out] Dönen bayt cinsinden boyutu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="67a52-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67a52-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67a52-114">Requirements</span></span>  
 <span data-ttu-id="67a52-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67a52-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67a52-116">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="67a52-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="67a52-117">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="67a52-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="67a52-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67a52-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67a52-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67a52-119">See Also</span></span>  
 [<span data-ttu-id="67a52-120">GetHashFromHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67a52-120">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)  
 [<span data-ttu-id="67a52-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67a52-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
