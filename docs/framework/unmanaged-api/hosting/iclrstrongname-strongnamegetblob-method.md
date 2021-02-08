---
description: ': ICLRStrongName:: StrongNameGetBlob Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 2b63ebd9c48ad18eef60f83c68fe412a4bd0d94f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799635"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="b6441-103">ICLRStrongName::StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6441-103">ICLRStrongName::StrongNameGetBlob Method</span></span>

<span data-ttu-id="b6441-104">Belirtilen adresteki yürütülebilir dosyanın ikili gösterimiyle belirtilen arabelleği doldurur.</span><span class="sxs-lookup"><span data-stu-id="b6441-104">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6441-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6441-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6441-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6441-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="b6441-107">'ndaki Yüklenecek yürütülebilir dosyanın geçerli yolu.</span><span class="sxs-lookup"><span data-stu-id="b6441-107">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="b6441-108">'ndaki Yürütülebilir dosyanın yükleneceği arabellek.</span><span class="sxs-lookup"><span data-stu-id="b6441-108">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="b6441-109">[in, out] İstenen en büyük boyut (bayt) `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="b6441-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="b6441-110">Dönüş sonrasında, bayt cinsinden gerçek boyut `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="b6441-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6441-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b6441-111">Return Value</span></span>  

 <span data-ttu-id="b6441-112">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="b6441-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6441-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6441-113">Requirements</span></span>  

 <span data-ttu-id="b6441-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6441-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6441-115">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="b6441-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b6441-116">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b6441-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6441-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6441-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6441-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6441-118">See also</span></span>

- [<span data-ttu-id="b6441-119">StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6441-119">StrongNameGetBlobFromImage Method</span></span>](iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="b6441-120">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6441-120">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
