---
title: ICLRStrongName::StrongNameGetBlob Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type:
- apiref
ms.openlocfilehash: f93d3f0322de89b2e9ce596329c06b58db9fdcdc
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760309"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="43f0b-102">ICLRStrongName::StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43f0b-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="43f0b-103">Belirtilen adresteki yürütülebilir dosyanın ikili gösterimiyle belirtilen arabelleği doldurur.</span><span class="sxs-lookup"><span data-stu-id="43f0b-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43f0b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="43f0b-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43f0b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="43f0b-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="43f0b-106">'ndaki Yüklenecek yürütülebilir dosyanın geçerli yolu.</span><span class="sxs-lookup"><span data-stu-id="43f0b-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="43f0b-107">'ndaki Yürütülebilir dosyanın yükleneceği arabellek.</span><span class="sxs-lookup"><span data-stu-id="43f0b-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="43f0b-108">[in, out] İstenen en büyük boyut (bayt) `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="43f0b-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="43f0b-109">Dönüş sonrasında, bayt cinsinden gerçek boyut `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="43f0b-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43f0b-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="43f0b-110">Return Value</span></span>  
 <span data-ttu-id="43f0b-111">`S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="43f0b-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43f0b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43f0b-112">Requirements</span></span>  
 <span data-ttu-id="43f0b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43f0b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43f0b-114">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="43f0b-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="43f0b-115">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="43f0b-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43f0b-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43f0b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f0b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43f0b-117">See also</span></span>

- [<span data-ttu-id="43f0b-118">StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43f0b-118">StrongNameGetBlobFromImage Method</span></span>](iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="43f0b-119">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43f0b-119">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
