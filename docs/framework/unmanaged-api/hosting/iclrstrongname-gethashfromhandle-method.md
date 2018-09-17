---
title: ICLRStrongName::GetHashFromHandle Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20c5f6bbb58b85f42ec00e356eccc5fb41ce813c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743612"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="f7afc-102">ICLRStrongName::GetHashFromHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7afc-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="f7afc-103">Belirtilen karma algoritması kullanılarak belirtilen tanıtıcıya sahip bir dosya içeriğini bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f7afc-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7afc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7afc-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7afc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f7afc-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="f7afc-106">[in] Karma hale getirilecek dosya tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="f7afc-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="f7afc-107">[out içinde] Sabit karma algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f7afc-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="f7afc-108">Sıfır varsayılan algoritma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="f7afc-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="f7afc-109">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="f7afc-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="f7afc-110">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="f7afc-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="f7afc-111">[out] Döndürülen bayt cinsinden boyutu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="f7afc-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7afc-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f7afc-112">Return Value</span></span>  
 <span data-ttu-id="f7afc-113">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="f7afc-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7afc-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7afc-114">Requirements</span></span>  
 <span data-ttu-id="f7afc-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7afc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7afc-116">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f7afc-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f7afc-117">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f7afc-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7afc-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7afc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7afc-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f7afc-119">See Also</span></span>  
 [<span data-ttu-id="f7afc-120">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f7afc-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
