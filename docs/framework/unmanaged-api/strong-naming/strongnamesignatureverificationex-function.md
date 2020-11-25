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
ms.openlocfilehash: 27417c379411e242c48d6d9b0c99de833f7ede8a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719274"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="03d96-102">StrongNameSignatureVerificationEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="03d96-102">StrongNameSignatureVerificationEx Function</span></span>

<span data-ttu-id="03d96-103">Belirtilen yoldaki Derleme bildiriminin tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="03d96-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="03d96-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="03d96-104">This function has been deprecated.</span></span> <span data-ttu-id="03d96-105">Bunun yerine [ICLRStrongName:: Strongnamesignaturedoğrulamaları Icationex](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="03d96-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03d96-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="03d96-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03d96-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="03d96-107">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="03d96-108">'ndaki Doğrulanacak derleme için taşınabilir yürütülebilir (. exe veya. dll) dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="03d96-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="03d96-109">[in] `true` doğrulama gerçekleştirmek için, kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="03d96-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="03d96-110">[out] `true` tanımlayıcı ad imzası doğrulandıysa; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="03d96-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="03d96-111">`pfWasVerified` , `false` kayıt defteri ayarları nedeniyle doğrulama başarılı olduysa olarak da ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="03d96-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03d96-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="03d96-112">Return Value</span></span>  

 <span data-ttu-id="03d96-113">`true` doğrulama başarılı olduysa, Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="03d96-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03d96-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03d96-114">Remarks</span></span>  

 <span data-ttu-id="03d96-115">`StrongNameSignatureVerificationEx`[Strongnamesignaturedoğrulama](strongnamesignatureverification-function.md) işlevine benzer bir yetenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="03d96-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="03d96-116">Ancak, ikinci giriş parametresi ve için çıkış parametresi `StrongNameSignatureVerificationEx` `BOOLEAN` yerine türüdür `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="03d96-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03d96-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03d96-117">Requirements</span></span>  

 <span data-ttu-id="03d96-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03d96-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03d96-119">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="03d96-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="03d96-120">**Kitaplık:** mscoree.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="03d96-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="03d96-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03d96-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03d96-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03d96-122">See also</span></span>

- [<span data-ttu-id="03d96-123">StrongNameSignatureVerificationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03d96-123">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="03d96-124">StrongNameSignatureVerification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03d96-124">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="03d96-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03d96-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
