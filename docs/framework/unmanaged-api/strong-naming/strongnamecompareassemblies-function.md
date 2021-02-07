---
description: 'Daha fazla bilgi edinin: StrongNameCompareAssemblies Işlevi'
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
ms.openlocfilehash: e59bb96a89dc1e1cf8b809c3e0d538aaffe83b8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736569"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="92281-103">StrongNameCompareAssemblies İşlevi</span><span class="sxs-lookup"><span data-stu-id="92281-103">StrongNameCompareAssemblies Function</span></span>

<span data-ttu-id="92281-104">İki derlemenin yalnızca kendi tanımlayıcı ad imzalarına göre farklı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="92281-104">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="92281-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="92281-105">This function has been deprecated.</span></span> <span data-ttu-id="92281-106">Bunun yerine [ICLRStrongName:: StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="92281-106">Use the [ICLRStrongName::StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92281-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92281-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92281-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92281-108">Parameters</span></span>  

 `wszAssembly1`  
 <span data-ttu-id="92281-109">'ndaki İlk derlemenin yolu.</span><span class="sxs-lookup"><span data-stu-id="92281-109">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="92281-110">'ndaki İkinci derlemenin yolu.</span><span class="sxs-lookup"><span data-stu-id="92281-110">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="92281-111">dışı Aşağıdaki değerlerden biri:</span><span class="sxs-lookup"><span data-stu-id="92281-111">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="92281-112">`SN_CMP_DIFFERENT` (0)-derlemelerin farklı veriler içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="92281-112">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="92281-113">`SN_CMP_IDENTICAL` (1)-derlemelerin imzaları ve sağlama toplamı dahil olmak üzere tam olarak aynı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="92281-113">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="92281-114">`SN_CMP_SIGONLY` (2)-derlemelerin yalnızca imzaya ve sağlama toplamına göre farklı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="92281-114">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92281-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="92281-115">Return Value</span></span>  

 <span data-ttu-id="92281-116">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="92281-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92281-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92281-117">Requirements</span></span>  

 <span data-ttu-id="92281-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92281-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92281-119">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="92281-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="92281-120">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="92281-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="92281-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92281-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92281-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92281-122">Remarks</span></span>  

 <span data-ttu-id="92281-123">Bir derlemenin tanımlayıcı ad imzası, derlemenin metin adı, sürüm, kültür ve ortak anahtar belirtecinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="92281-123">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="92281-124">`StrongNameCompareAssemblies`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="92281-124">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92281-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92281-125">See also</span></span>

- [<span data-ttu-id="92281-126">StrongNameCompareAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92281-126">StrongNameCompareAssemblies Method</span></span>](../hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="92281-127">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92281-127">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
