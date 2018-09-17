---
title: ICLRStrongName::GetHashFromAssemblyFile Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8d9e7d593c2a8a9cce798724b2705dee21a740e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45692729"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="61953-102">ICLRStrongName::GetHashFromAssemblyFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61953-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="61953-103">Belirtilen karma algoritması kullanılarak, belirtilen derleme dosyasının bir karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="61953-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61953-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61953-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61953-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61953-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="61953-106">[in] Karma hale getirilecek dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="61953-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="61953-107">[out içinde] Sabit karma algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="61953-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="61953-108">Sıfır varsayılan karma algoritması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="61953-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="61953-109">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="61953-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="61953-110">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="61953-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="61953-111">[out] Bayt cinsinden boyutu döndürülen `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="61953-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61953-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="61953-112">Return Value</span></span>  
 <span data-ttu-id="61953-113">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="61953-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61953-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61953-114">Requirements</span></span>  
 <span data-ttu-id="61953-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61953-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61953-116">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="61953-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="61953-117">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="61953-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61953-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61953-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61953-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61953-119">See Also</span></span>  
 [<span data-ttu-id="61953-120">GetHashFromAssemblyFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61953-120">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="61953-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61953-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
