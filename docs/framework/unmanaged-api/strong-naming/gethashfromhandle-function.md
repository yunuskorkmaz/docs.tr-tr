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
ms.openlocfilehash: 1ccb6d3b50e70d69b706f63be8a783ad6d7f7cdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="3c462-102">GetHashFromHandle İşlevi</span><span class="sxs-lookup"><span data-stu-id="3c462-102">GetHashFromHandle Function</span></span>
<span data-ttu-id="3c462-103">Belirtilen karma algoritması kullanılarak belirtilen dosya tanıtıcısıyla dosyasının içeriği üzerinden bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3c462-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="3c462-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="3c462-104">This function has been deprecated.</span></span> <span data-ttu-id="3c462-105">Kullanım [Iclrstrongname::gethashfromhandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="3c462-105">Use the [ICLRStrongName::GetHashFromHandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c462-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c462-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c462-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c462-107">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="3c462-108">[in] Karma hale getirilmesi için dosya tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="3c462-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="3c462-109">[içinde out] Karma algoritmasını belirtir sabiti.</span><span class="sxs-lookup"><span data-stu-id="3c462-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="3c462-110">Varsayılan algoritma için sıfır değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3c462-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="3c462-111">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="3c462-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="3c462-112">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="3c462-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="3c462-113">[out] Dönen bayt cinsinden boyutu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="3c462-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c462-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c462-114">Requirements</span></span>  
 <span data-ttu-id="3c462-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c462-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c462-116">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="3c462-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3c462-117">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3c462-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3c462-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c462-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c462-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c462-119">See Also</span></span>  
 [<span data-ttu-id="3c462-120">GetHashFromHandle yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c462-120">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)  
 [<span data-ttu-id="3c462-121">Iclrstrongname arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c462-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
