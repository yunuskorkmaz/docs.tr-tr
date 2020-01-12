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
ms.openlocfilehash: c7f04364cc52bd38d7d2659d1d188c5fd783ad01
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899757"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="b10d2-102">ICLRStrongName::StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b10d2-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="b10d2-103">Belirtilen adresteki yürütülebilir dosyanın ikili gösterimiyle belirtilen arabelleği doldurur.</span><span class="sxs-lookup"><span data-stu-id="b10d2-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b10d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b10d2-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b10d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b10d2-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b10d2-106">'ndaki Yüklenecek yürütülebilir dosyanın geçerli yolu.</span><span class="sxs-lookup"><span data-stu-id="b10d2-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="b10d2-107">'ndaki Yürütülebilir dosyanın yükleneceği arabellek.</span><span class="sxs-lookup"><span data-stu-id="b10d2-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="b10d2-108">[in, out] `pbBlob`istenen en büyük boyut (bayt cinsinden).</span><span class="sxs-lookup"><span data-stu-id="b10d2-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="b10d2-109">Dönüş sonrasında, `pbBlob`bayt cinsinden gerçek boyut.</span><span class="sxs-lookup"><span data-stu-id="b10d2-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b10d2-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b10d2-110">Return Value</span></span>  
 <span data-ttu-id="b10d2-111">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="b10d2-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b10d2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b10d2-112">Requirements</span></span>  
 <span data-ttu-id="b10d2-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b10d2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b10d2-114">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="b10d2-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b10d2-115">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="b10d2-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b10d2-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b10d2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b10d2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b10d2-117">See also</span></span>

- [<span data-ttu-id="b10d2-118">StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b10d2-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="b10d2-119">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b10d2-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
