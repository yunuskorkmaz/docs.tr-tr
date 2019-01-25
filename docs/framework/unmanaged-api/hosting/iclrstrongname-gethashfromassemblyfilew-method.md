---
title: ICLRStrongName::GetHashFromAssemblyFileW Metodu
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 819801cd9ecce9f3d71f4454f4c65e8f3f8391a0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714769"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="cf52f-102">ICLRStrongName::GetHashFromAssemblyFileW Metodu</span><span class="sxs-lookup"><span data-stu-id="cf52f-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="cf52f-103">Unicode dizesi tarafından belirtilen dosyanın içeriğini üzerinden bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cf52f-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf52f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf52f-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf52f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf52f-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="cf52f-106">[in] Karma hale getirilecek dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="cf52f-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="cf52f-107">Bu parametre, bir Unicode dize olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf52f-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="cf52f-108">[out içinde] Sabit karma algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf52f-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="cf52f-109">Sıfır varsayılan karma algoritması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="cf52f-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="cf52f-110">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="cf52f-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="cf52f-111">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="cf52f-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="cf52f-112">[out] Bayt cinsinden boyutu döndürülen `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="cf52f-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf52f-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cf52f-113">Return Value</span></span>  
 <span data-ttu-id="cf52f-114">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="cf52f-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf52f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf52f-115">Requirements</span></span>  
 <span data-ttu-id="cf52f-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf52f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf52f-117">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="cf52f-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cf52f-118">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cf52f-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf52f-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf52f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf52f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf52f-120">See also</span></span>
- [<span data-ttu-id="cf52f-121">GetHashFromAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf52f-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="cf52f-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf52f-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
