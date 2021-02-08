---
description: 'Daha fazla bilgi edinin: Strongnamesignaturedoğrulamaları Icationfromımage Işlevi'
title: StrongNameSignatureVerificationFromImage İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type:
- apiref
ms.openlocfilehash: 9dca8d0b221dfe8959be2de9b8347b95d3802a0e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794500"
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="12f91-103">StrongNameSignatureVerificationFromImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="12f91-103">StrongNameSignatureVerificationFromImage Function</span></span>

<span data-ttu-id="12f91-104">Zaten bellekle eşlenmiş bir derlemenin ilişkili ortak anahtar için geçerli olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="12f91-104">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="12f91-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="12f91-105">This function has been deprecated.</span></span> <span data-ttu-id="12f91-106">Bunun yerine [ICLRStrongName:: Strongnamedoğrulamaları Icationfromımage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="12f91-106">Use the [ICLRStrongName::StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12f91-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12f91-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12f91-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12f91-108">Parameters</span></span>  

 `pbBase`  
 <span data-ttu-id="12f91-109">'ndaki Eşlenen derleme bildiriminin göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="12f91-109">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="12f91-110">'ndaki Eşlenen görüntünün bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="12f91-110">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="12f91-111">'ndaki Doğrulama davranışını etkileyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="12f91-111">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="12f91-112">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="12f91-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="12f91-113">`SN_INFLAG_FORCE_VER` (0x00000001)-kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile doğrulamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="12f91-113">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="12f91-114">`SN_INFLAG_INSTALL` (0x00000002)-Bu görüntüde gerçekleştirilen ilk doğrulamanın olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="12f91-114">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="12f91-115">`SN_INFLAG_ADMIN_ACCESS` (0x00000004)-önbelleğin yalnızca yönetici ayrıcalıklarına sahip olan kullanıcılar için erişime izin verolacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="12f91-115">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="12f91-116">`SN_INFLAG_USER_ACCESS` (0x00000008)-derlemenin yalnızca geçerli kullanıcı için erişilebilir olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="12f91-116">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="12f91-117">`SN_INFLAG_ALL_ACCESS` (0x00000010)-önbelleğin erişim kısıtlaması garantisi sunmayacak olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="12f91-117">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="12f91-118">`SN_INFLAG_RUNTIME` (0x80000000)-iç hata ayıklama için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="12f91-118">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="12f91-119">dışı Ek çıkış bilgileri için bayrak.</span><span class="sxs-lookup"><span data-stu-id="12f91-119">[out] A flag for additional output information.</span></span> <span data-ttu-id="12f91-120">Aşağıdaki değer desteklenir:</span><span class="sxs-lookup"><span data-stu-id="12f91-120">The following value is supported:</span></span>  
  
- <span data-ttu-id="12f91-121">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-Bu değer `false` , kayıt defteri ayarları nedeniyle doğrulamanın başarılı olduğunu belirtmek için olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="12f91-121">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12f91-122">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="12f91-122">Return Value</span></span>  

 <span data-ttu-id="12f91-123">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="12f91-123">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12f91-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12f91-124">Remarks</span></span>  

 <span data-ttu-id="12f91-125">`StrongNameSignatureVerificationFromImage`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="12f91-125">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12f91-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12f91-126">Requirements</span></span>  

 <span data-ttu-id="12f91-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12f91-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12f91-128">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="12f91-128">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="12f91-129">**Kitaplık:** mscoree.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="12f91-129">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="12f91-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12f91-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f91-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12f91-131">See also</span></span>

- [<span data-ttu-id="12f91-132">StrongNameSignatureVerificationFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12f91-132">StrongNameSignatureVerificationFromImage Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [<span data-ttu-id="12f91-133">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12f91-133">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
