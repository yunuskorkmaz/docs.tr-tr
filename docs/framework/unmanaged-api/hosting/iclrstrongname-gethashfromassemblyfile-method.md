---
title: ICLRStrongName::GetHashFromAssemblyFile Metodu
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6dcb0ca16c2ffdd8a928cec9cca44b628de34885
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="4d4e3-102">ICLRStrongName::GetHashFromAssemblyFile Metodu</span><span class="sxs-lookup"><span data-stu-id="4d4e3-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="4d4e3-103">Belirtilen karma algoritması kullanılarak belirtilen derleme dosyası karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="4d4e3-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d4e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d4e3-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d4e3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4d4e3-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="4d4e3-106">[in] Karma hale getirilmesi için dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="4d4e3-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="4d4e3-107">[içinde out] Karma algoritmasını belirtir sabiti.</span><span class="sxs-lookup"><span data-stu-id="4d4e3-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="4d4e3-108">Varsayılan karma algoritma için sıfır değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4d4e3-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="4d4e3-109">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="4d4e3-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="4d4e3-110">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="4d4e3-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="4d4e3-111">[out] Bayt cinsinden boyutu döndürülen `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="4d4e3-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d4e3-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4d4e3-112">Return Value</span></span>  
 <span data-ttu-id="4d4e3-113">`S_OK`Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="4d4e3-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d4e3-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d4e3-114">Requirements</span></span>  
 <span data-ttu-id="4d4e3-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d4e3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d4e3-116">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="4d4e3-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4d4e3-117">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4d4e3-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d4e3-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d4e3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d4e3-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d4e3-119">See Also</span></span>  
 [<span data-ttu-id="4d4e3-120">GetHashFromAssemblyFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d4e3-120">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="4d4e3-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d4e3-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
