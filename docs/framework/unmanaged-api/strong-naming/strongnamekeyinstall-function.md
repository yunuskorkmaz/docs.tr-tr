---
title: "StrongNameKeyInstall İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9a8dbc84f375b7bbbad47971936650d81c5c63df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="37f8c-102">StrongNameKeyInstall İşlevi</span><span class="sxs-lookup"><span data-stu-id="37f8c-102">StrongNameKeyInstall Function</span></span>
<span data-ttu-id="37f8c-103">Bir ortak/özel anahtar çifti bir kapsayıcıya alır.</span><span class="sxs-lookup"><span data-stu-id="37f8c-103">Imports a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="37f8c-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="37f8c-104">This function has been deprecated.</span></span> <span data-ttu-id="37f8c-105">Kullanım [Iclrstrongname::strongnamekeyınstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="37f8c-105">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37f8c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37f8c-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37f8c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="37f8c-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="37f8c-108">[in] Anahtar kapsayıcı adı.</span><span class="sxs-lookup"><span data-stu-id="37f8c-108">[in] The name of the key container.</span></span> <span data-ttu-id="37f8c-109">`wszKeyContainer`boş olmayan bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="37f8c-109">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="37f8c-110">[in] İkili anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="37f8c-110">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="37f8c-111">[in] Bayt olarak boyutu, `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="37f8c-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37f8c-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="37f8c-112">Return Value</span></span>  
 <span data-ttu-id="37f8c-113">`true`başarılı tamamlanma; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="37f8c-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37f8c-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="37f8c-114">Remarks</span></span>  
 <span data-ttu-id="37f8c-115">Kullanım [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) anahtar kapsayıcısını silmek için işlev.</span><span class="sxs-lookup"><span data-stu-id="37f8c-115">Use the [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) function to delete the key container.</span></span>  
  
 <span data-ttu-id="37f8c-116">Varsa `StrongNameKeyInstall` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.</span><span class="sxs-lookup"><span data-stu-id="37f8c-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37f8c-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37f8c-117">Requirements</span></span>  
 <span data-ttu-id="37f8c-118">**Platformlar:** WindSee [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37f8c-118">**Platforms:** WindSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37f8c-119">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="37f8c-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="37f8c-120">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="37f8c-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="37f8c-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37f8c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37f8c-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37f8c-122">See Also</span></span>  
 [<span data-ttu-id="37f8c-123">StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37f8c-123">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="37f8c-124">StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37f8c-124">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="37f8c-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37f8c-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
