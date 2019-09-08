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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08247c1ec5b868055e4836b3c0fb520a536374e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798920"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="11955-102">StrongNameSignatureVerificationEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="11955-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="11955-103">Belirtilen yoldaki Derleme bildiriminin tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="11955-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="11955-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="11955-104">This function has been deprecated.</span></span> <span data-ttu-id="11955-105">Bunun yerine [ICLRStrongName:: Strongnamesignaturedoğrulamaları Icationex](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="11955-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11955-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11955-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11955-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="11955-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="11955-108">'ndaki Doğrulanacak derleme için taşınabilir yürütülebilir (. exe veya. dll) dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="11955-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="11955-109">'ndaki doğrulama gerçekleştirmek için, kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile, aksi durumda, `false`. `true`</span><span class="sxs-lookup"><span data-stu-id="11955-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="11955-110">dışı tanımlayıcı ad imzası doğrulandıysa, `false`tersi durumda. `true`</span><span class="sxs-lookup"><span data-stu-id="11955-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="11955-111">`pfWasVerified`, kayıt defteri ayarları `false` nedeniyle doğrulama başarılı olduysa olarak da ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="11955-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11955-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="11955-112">Return Value</span></span>  
 <span data-ttu-id="11955-113">`true`doğrulama başarılı olduysa, Aksi takdirde `false`,.</span><span class="sxs-lookup"><span data-stu-id="11955-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11955-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11955-114">Remarks</span></span>  
 <span data-ttu-id="11955-115">`StrongNameSignatureVerificationEx`[Strongnamesignaturedoğrulama](strongnamesignatureverification-function.md) işlevine benzer bir yetenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="11955-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="11955-116">Ancak, ikinci giriş parametresi ve için `StrongNameSignatureVerificationEx` çıkış parametresi yerine `DWORD`türüdür `BOOLEAN` .</span><span class="sxs-lookup"><span data-stu-id="11955-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11955-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="11955-117">Requirements</span></span>  
 <span data-ttu-id="11955-118">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11955-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11955-119">**Üst bilgi** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="11955-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="11955-120">**Kitaplığı** Mscoree. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="11955-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="11955-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11955-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11955-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11955-122">See also</span></span>

- [<span data-ttu-id="11955-123">StrongNameSignatureVerificationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="11955-123">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="11955-124">StrongNameSignatureVerification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="11955-124">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="11955-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11955-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
