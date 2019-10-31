---
title: StrongNameSignatureVerificationEx İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
ms.openlocfilehash: ca428d680df1710d8e74441d9945d4c3545b0482
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121140"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="8f77a-102">StrongNameSignatureVerificationEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="8f77a-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="8f77a-103">Belirtilen yoldaki Derleme bildiriminin tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="8f77a-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="8f77a-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="8f77a-104">This function has been deprecated.</span></span> <span data-ttu-id="8f77a-105">Bunun yerine [ICLRStrongName:: Strongnamesignaturedoğrulamaları Icationex](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="8f77a-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f77a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f77a-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f77a-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f77a-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="8f77a-108">'ndaki Doğrulanacak derleme için taşınabilir yürütülebilir (. exe veya. dll) dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="8f77a-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="8f77a-109">[in] kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile doğrulama gerçekleştirmek için `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="8f77a-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="8f77a-110">[out] tanımlayıcı ad imzası doğrulandıysa `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="8f77a-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="8f77a-111">Ayrıca, kayıt defteri ayarları nedeniyle doğrulama başarılı olduysa, `pfWasVerified` `false` olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="8f77a-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f77a-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8f77a-112">Return Value</span></span>  
 <span data-ttu-id="8f77a-113">doğrulama başarılı olduysa `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="8f77a-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f77a-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f77a-114">Remarks</span></span>  
 <span data-ttu-id="8f77a-115">`StrongNameSignatureVerificationEx` [Strongnamesignaturedoğrulama](strongnamesignatureverification-function.md) işlevine benzer bir yetenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f77a-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="8f77a-116">Ancak, `StrongNameSignatureVerificationEx` için ikinci giriş parametresi ve çıkış parametresi `DWORD`yerine `BOOLEAN` türüdür.</span><span class="sxs-lookup"><span data-stu-id="8f77a-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f77a-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f77a-117">Requirements</span></span>  
 <span data-ttu-id="8f77a-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f77a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f77a-119">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="8f77a-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="8f77a-120">**Kitaplık:** Mscoree. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8f77a-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="8f77a-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f77a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f77a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f77a-122">See also</span></span>

- [<span data-ttu-id="8f77a-123">StrongNameSignatureVerificationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f77a-123">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="8f77a-124">StrongNameSignatureVerification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f77a-124">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="8f77a-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f77a-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
