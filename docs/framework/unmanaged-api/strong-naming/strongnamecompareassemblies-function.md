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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a49252d00f75b4d0b6325aeae0aab22f8ada5e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000330"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="dddcc-102">StrongNameCompareAssemblies İşlevi</span><span class="sxs-lookup"><span data-stu-id="dddcc-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="dddcc-103">İki derlemenin yalnızca tanımlayıcı ad imzaları tarafından farklı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="dddcc-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="dddcc-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="dddcc-104">This function has been deprecated.</span></span> <span data-ttu-id="dddcc-105">Kullanım [Iclrstrongname::strongnamecompareassemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="dddcc-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dddcc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dddcc-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dddcc-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dddcc-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="dddcc-108">[in] İlk bütünleştirilmiş kod yolu.</span><span class="sxs-lookup"><span data-stu-id="dddcc-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="dddcc-109">[in] İkinci bütünleştirilmiş kod yolu.</span><span class="sxs-lookup"><span data-stu-id="dddcc-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="dddcc-110">[out] Aşağıdaki değerlerden biri:</span><span class="sxs-lookup"><span data-stu-id="dddcc-110">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="dddcc-111">`SN_CMP_DIFFERENT` (0) - derlemeleri farklı veri içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dddcc-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="dddcc-112">`SN_CMP_IDENTICAL` (1) - derlemeleri tam olarak aynı kendi imzaları ve sağlama toplamı dahil olmak üzere olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="dddcc-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="dddcc-113">`SN_CMP_SIGONLY` (2) - derlemeler yalnızca imza ve sağlama toplamı farklı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="dddcc-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dddcc-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dddcc-114">Return Value</span></span>  
 <span data-ttu-id="dddcc-115">`true` başarıyla tamamlandığında; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="dddcc-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dddcc-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dddcc-116">Requirements</span></span>  
 <span data-ttu-id="dddcc-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dddcc-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dddcc-118">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="dddcc-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="dddcc-119">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="dddcc-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dddcc-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dddcc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dddcc-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dddcc-121">Remarks</span></span>  
 <span data-ttu-id="dddcc-122">Bir derlemenin tanımlayıcı ad imzası, derlemenin metin adı, sürüm, kültür ve ortak anahtar belirteci oluşur.</span><span class="sxs-lookup"><span data-stu-id="dddcc-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="dddcc-123">Varsa `StrongNameCompareAssemblies` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.</span><span class="sxs-lookup"><span data-stu-id="dddcc-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dddcc-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dddcc-124">See also</span></span>

- [<span data-ttu-id="dddcc-125">StrongNameCompareAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dddcc-125">StrongNameCompareAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="dddcc-126">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dddcc-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
