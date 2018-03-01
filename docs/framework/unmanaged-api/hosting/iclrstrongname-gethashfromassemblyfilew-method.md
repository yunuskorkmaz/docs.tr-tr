---
title: ICLRStrongName::GetHashFromAssemblyFileW Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b10d74cd54afc3c93578710d4a2e339a1f8761f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="a54a8-102">ICLRStrongName::GetHashFromAssemblyFileW Metodu</span><span class="sxs-lookup"><span data-stu-id="a54a8-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="a54a8-103">Bir UNICODE dizesi tarafından belirtilen dosyanın içeriğini üzerinden bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a54a8-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a54a8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a54a8-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a54a8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a54a8-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="a54a8-106">[in] Karma hale getirilmesi için dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="a54a8-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="a54a8-107">Bu parametre bir UNICODE dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a54a8-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="a54a8-108">[içinde out] Karma algoritmasını belirtir sabiti.</span><span class="sxs-lookup"><span data-stu-id="a54a8-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="a54a8-109">Varsayılan karma algoritma için sıfır değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a54a8-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="a54a8-110">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="a54a8-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="a54a8-111">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="a54a8-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="a54a8-112">[out] Bayt cinsinden boyutu döndürülen `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="a54a8-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a54a8-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a54a8-113">Return Value</span></span>  
 <span data-ttu-id="a54a8-114">`S_OK`Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="a54a8-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a54a8-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a54a8-115">Requirements</span></span>  
 <span data-ttu-id="a54a8-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a54a8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a54a8-117">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a54a8-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a54a8-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a54a8-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a54a8-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a54a8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a54a8-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a54a8-120">See Also</span></span>  
 [<span data-ttu-id="a54a8-121">GetHashFromAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a54a8-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="a54a8-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a54a8-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
