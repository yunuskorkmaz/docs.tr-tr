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
ms.openlocfilehash: 36e4f07f04968579be2e42efad666b0453cc4796
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434797"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="b013d-102">ICLRStrongName::GetHashFromAssemblyFileW Metodu</span><span class="sxs-lookup"><span data-stu-id="b013d-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="b013d-103">Bir UNICODE dizesi tarafından belirtilen dosyanın içeriğini üzerinden bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b013d-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b013d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b013d-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b013d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b013d-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b013d-106">[in] Karma hale getirilmesi için dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="b013d-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="b013d-107">Bu parametre bir UNICODE dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b013d-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="b013d-108">[içinde out] Karma algoritmasını belirtir sabiti.</span><span class="sxs-lookup"><span data-stu-id="b013d-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="b013d-109">Varsayılan karma algoritma için sıfır değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b013d-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="b013d-110">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="b013d-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="b013d-111">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="b013d-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="b013d-112">[out] Bayt cinsinden boyutu döndürülen `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="b013d-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b013d-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b013d-113">Return Value</span></span>  
 <span data-ttu-id="b013d-114">`S_OK` Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="b013d-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b013d-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b013d-115">Requirements</span></span>  
 <span data-ttu-id="b013d-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b013d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b013d-117">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b013d-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b013d-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b013d-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b013d-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b013d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b013d-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b013d-120">See Also</span></span>  
 [<span data-ttu-id="b013d-121">GetHashFromAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b013d-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="b013d-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b013d-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
