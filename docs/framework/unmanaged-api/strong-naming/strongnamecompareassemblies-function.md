---
title: StrongNameCompareAssemblies İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameCompareAssemblies
helpviewer_keywords:
- StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type:
- apiref
ms.openlocfilehash: e7292635ea0344f1c77c8d44908a9a811e464ff9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732313"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="024ef-102">StrongNameCompareAssemblies İşlevi</span><span class="sxs-lookup"><span data-stu-id="024ef-102">StrongNameCompareAssemblies Function</span></span>

<span data-ttu-id="024ef-103">İki derlemenin yalnızca kendi tanımlayıcı ad imzalarına göre farklı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="024ef-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="024ef-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="024ef-104">This function has been deprecated.</span></span> <span data-ttu-id="024ef-105">Bunun yerine [ICLRStrongName:: StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="024ef-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="024ef-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="024ef-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="024ef-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="024ef-107">Parameters</span></span>  

 `wszAssembly1`  
 <span data-ttu-id="024ef-108">'ndaki İlk derlemenin yolu.</span><span class="sxs-lookup"><span data-stu-id="024ef-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="024ef-109">'ndaki İkinci derlemenin yolu.</span><span class="sxs-lookup"><span data-stu-id="024ef-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="024ef-110">dışı Aşağıdaki değerlerden biri:</span><span class="sxs-lookup"><span data-stu-id="024ef-110">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="024ef-111">`SN_CMP_DIFFERENT` (0)-derlemelerin farklı veriler içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="024ef-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="024ef-112">`SN_CMP_IDENTICAL` (1)-derlemelerin imzaları ve sağlama toplamı dahil olmak üzere tam olarak aynı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="024ef-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="024ef-113">`SN_CMP_SIGONLY` (2)-derlemelerin yalnızca imzaya ve sağlama toplamına göre farklı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="024ef-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="024ef-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="024ef-114">Return Value</span></span>  

 <span data-ttu-id="024ef-115">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="024ef-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="024ef-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="024ef-116">Requirements</span></span>  

 <span data-ttu-id="024ef-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="024ef-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="024ef-118">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="024ef-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="024ef-119">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="024ef-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="024ef-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="024ef-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="024ef-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="024ef-121">Remarks</span></span>  

 <span data-ttu-id="024ef-122">Bir derlemenin tanımlayıcı ad imzası, derlemenin metin adı, sürüm, kültür ve ortak anahtar belirtecinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="024ef-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="024ef-123">`StrongNameCompareAssemblies`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="024ef-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="024ef-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="024ef-124">See also</span></span>

- [<span data-ttu-id="024ef-125">StrongNameCompareAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="024ef-125">StrongNameCompareAssemblies Method</span></span>](../hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="024ef-126">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="024ef-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
