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
ms.openlocfilehash: a7686a84759f8ac40a123d2c9a7b8f1b9b8096cb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672606"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="2c756-102">ICLRStrongName::GetHashFromAssemblyFileW Metodu</span><span class="sxs-lookup"><span data-stu-id="2c756-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="2c756-103">Unicode dizesi tarafından belirtilen dosyanın içeriğini üzerinden bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2c756-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c756-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c756-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c756-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c756-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="2c756-106">[in] Karma hale getirilecek dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="2c756-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="2c756-107">Bu parametre, bir Unicode dize olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c756-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="2c756-108">[out içinde] Sabit karma algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c756-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="2c756-109">Sıfır varsayılan karma algoritması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="2c756-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="2c756-110">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="2c756-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="2c756-111">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="2c756-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="2c756-112">[out] Bayt cinsinden boyutu döndürülen `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="2c756-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c756-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2c756-113">Return Value</span></span>  
 <span data-ttu-id="2c756-114">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="2c756-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c756-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c756-115">Requirements</span></span>  
 <span data-ttu-id="2c756-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c756-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c756-117">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2c756-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2c756-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2c756-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c756-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c756-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c756-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2c756-120">See Also</span></span>  
 [<span data-ttu-id="2c756-121">GetHashFromAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c756-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="2c756-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c756-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
