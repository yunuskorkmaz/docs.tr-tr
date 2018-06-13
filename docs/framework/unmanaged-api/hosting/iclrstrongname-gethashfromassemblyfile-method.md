---
title: ICLRStrongName::GetHashFromAssemblyFile Metodu
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
ms.openlocfilehash: 95fbab459355c237157d43cee0211e42f6d26c62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432631"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="74c5f-102">ICLRStrongName::GetHashFromAssemblyFile Metodu</span><span class="sxs-lookup"><span data-stu-id="74c5f-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="74c5f-103">Belirtilen karma algoritması kullanılarak belirtilen derleme dosyası karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="74c5f-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74c5f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74c5f-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74c5f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74c5f-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="74c5f-106">[in] Karma hale getirilmesi için dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="74c5f-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="74c5f-107">[içinde out] Karma algoritmasını belirtir sabiti.</span><span class="sxs-lookup"><span data-stu-id="74c5f-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="74c5f-108">Varsayılan karma algoritma için sıfır değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="74c5f-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="74c5f-109">[out] Döndürülen karma arabellek.</span><span class="sxs-lookup"><span data-stu-id="74c5f-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="74c5f-110">[in] İstenen en büyük boyutunu `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="74c5f-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="74c5f-111">[out] Bayt cinsinden boyutu döndürülen `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="74c5f-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74c5f-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="74c5f-112">Return Value</span></span>  
 <span data-ttu-id="74c5f-113">`S_OK` Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="74c5f-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74c5f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74c5f-114">Requirements</span></span>  
 <span data-ttu-id="74c5f-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74c5f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74c5f-116">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="74c5f-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="74c5f-117">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="74c5f-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74c5f-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74c5f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74c5f-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74c5f-119">See Also</span></span>  
 [<span data-ttu-id="74c5f-120">GetHashFromAssemblyFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74c5f-120">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="74c5f-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74c5f-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
