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
ms.openlocfilehash: adde52dddb63b83dcd7ff10703a43928d9601c92
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140624"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="c891a-102">StrongNameCompareAssemblies İşlevi</span><span class="sxs-lookup"><span data-stu-id="c891a-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="c891a-103">İki derlemenin yalnızca kendi tanımlayıcı ad imzalarına göre farklı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="c891a-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="c891a-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="c891a-104">This function has been deprecated.</span></span> <span data-ttu-id="c891a-105">Bunun yerine [ICLRStrongName:: StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c891a-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c891a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c891a-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c891a-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c891a-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="c891a-108">'ndaki İlk derlemenin yolu.</span><span class="sxs-lookup"><span data-stu-id="c891a-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="c891a-109">'ndaki İkinci derlemenin yolu.</span><span class="sxs-lookup"><span data-stu-id="c891a-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="c891a-110">dışı Aşağıdaki değerlerden biri:</span><span class="sxs-lookup"><span data-stu-id="c891a-110">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="c891a-111">`SN_CMP_DIFFERENT` (0)-derlemelerin farklı veriler içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c891a-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="c891a-112">`SN_CMP_IDENTICAL` (1)-derlemelerin imzaları ve sağlama toplamı dahil olmak üzere tam olarak aynı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c891a-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="c891a-113">`SN_CMP_SIGONLY` (2)-derlemelerin yalnızca imzaya ve sağlama toplamına göre farklı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c891a-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c891a-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c891a-114">Return Value</span></span>  
 <span data-ttu-id="c891a-115">başarılı tamamlamada `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="c891a-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c891a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c891a-116">Requirements</span></span>  
 <span data-ttu-id="c891a-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c891a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c891a-118">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="c891a-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c891a-119">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c891a-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c891a-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c891a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c891a-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c891a-121">Remarks</span></span>  
 <span data-ttu-id="c891a-122">Bir derlemenin tanımlayıcı ad imzası, derlemenin metin adı, sürüm, kültür ve ortak anahtar belirtecinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="c891a-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="c891a-123">`StrongNameCompareAssemblies` işlevi başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="c891a-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c891a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c891a-124">See also</span></span>

- [<span data-ttu-id="c891a-125">StrongNameCompareAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c891a-125">StrongNameCompareAssemblies Method</span></span>](../hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="c891a-126">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c891a-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
