---
description: ': ICLRStrongName:: StrongNameCompareAssemblies Yöntemi hakkında daha fazla bilgi'
title: ICLRStrongName::StrongNameCompareAssemblies Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
ms.openlocfilehash: ab02312073f9caf5059ecf7b4eeddaef864bd7b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799661"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="1a86d-103">ICLRStrongName::StrongNameCompareAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a86d-103">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>

<span data-ttu-id="1a86d-104">İki derlemenin yalnızca kendi tanımlayıcı ad imzalarına göre farklı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="1a86d-104">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a86d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a86d-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a86d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a86d-106">Parameters</span></span>  

 `wszAssembly1`  
 <span data-ttu-id="1a86d-107">'ndaki İlk derlemenin yolu.</span><span class="sxs-lookup"><span data-stu-id="1a86d-107">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="1a86d-108">'ndaki İkinci derlemenin yolu.</span><span class="sxs-lookup"><span data-stu-id="1a86d-108">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="1a86d-109">dışı Aşağıdaki değerlerden biri:</span><span class="sxs-lookup"><span data-stu-id="1a86d-109">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="1a86d-110">`SN_CMP_DIFFERENT` (0)-derlemelerin farklı veriler içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1a86d-110">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="1a86d-111">`SN_CMP_IDENTICAL` (1)-derlemelerin imzaları ve sağlama toplamı dahil olmak üzere tam olarak aynı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1a86d-111">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="1a86d-112">`SN_CMP_SIGONLY` (2)-derlemelerin yalnızca imzaya ve sağlama toplamına göre farklı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1a86d-112">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a86d-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1a86d-113">Return Value</span></span>  

 <span data-ttu-id="1a86d-114">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="1a86d-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a86d-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a86d-115">Requirements</span></span>  

 <span data-ttu-id="1a86d-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a86d-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a86d-117">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="1a86d-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1a86d-118">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="1a86d-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a86d-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a86d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a86d-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a86d-120">Remarks</span></span>  

 <span data-ttu-id="1a86d-121">Bir derlemenin tanımlayıcı ad imzası, derlemenin metin adı, sürüm, kültür ve ortak anahtar belirtecinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="1a86d-121">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a86d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a86d-122">See also</span></span>

- [<span data-ttu-id="1a86d-123">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a86d-123">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
