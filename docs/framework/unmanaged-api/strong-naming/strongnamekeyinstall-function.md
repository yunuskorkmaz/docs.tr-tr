---
title: StrongNameKeyInstall İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b6760a6418533f5c8f6cec815d86b4cff68aab1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460087"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="f5d65-102">StrongNameKeyInstall İşlevi</span><span class="sxs-lookup"><span data-stu-id="f5d65-102">StrongNameKeyInstall Function</span></span>
<span data-ttu-id="f5d65-103">Bir ortak/özel anahtar çifti bir kapsayıcıya alır.</span><span class="sxs-lookup"><span data-stu-id="f5d65-103">Imports a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="f5d65-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="f5d65-104">This function has been deprecated.</span></span> <span data-ttu-id="f5d65-105">Kullanım [Iclrstrongname::strongnamekeyınstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="f5d65-105">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5d65-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5d65-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5d65-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5d65-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="f5d65-108">[in] Anahtar kapsayıcı adı.</span><span class="sxs-lookup"><span data-stu-id="f5d65-108">[in] The name of the key container.</span></span> <span data-ttu-id="f5d65-109">`wszKeyContainer` boş olmayan bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f5d65-109">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="f5d65-110">[in] İkili anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="f5d65-110">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="f5d65-111">[in] Bayt olarak boyutu, `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="f5d65-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5d65-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f5d65-112">Return Value</span></span>  
 <span data-ttu-id="f5d65-113">`true` başarılı tamamlanma; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="f5d65-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5d65-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5d65-114">Remarks</span></span>  
 <span data-ttu-id="f5d65-115">Kullanım [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) anahtar kapsayıcısını silmek için işlev.</span><span class="sxs-lookup"><span data-stu-id="f5d65-115">Use the [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) function to delete the key container.</span></span>  
  
 <span data-ttu-id="f5d65-116">Varsa `StrongNameKeyInstall` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.</span><span class="sxs-lookup"><span data-stu-id="f5d65-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5d65-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5d65-117">Requirements</span></span>  
 <span data-ttu-id="f5d65-118">**Platformlar:** WindSee [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5d65-118">**Platforms:** WindSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5d65-119">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="f5d65-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f5d65-120">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f5d65-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f5d65-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5d65-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5d65-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5d65-122">See Also</span></span>  
 [<span data-ttu-id="f5d65-123">StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5d65-123">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="f5d65-124">StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5d65-124">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="f5d65-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5d65-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
