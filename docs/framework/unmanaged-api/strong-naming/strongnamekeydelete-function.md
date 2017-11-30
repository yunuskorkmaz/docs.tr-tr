---
title: "StrongNameKeyDelete İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameKeyDelete
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameKeyDelete
helpviewer_keywords: StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c7b3ccc9ec1b8cbc81de115f734e1d11e0e0ae0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="d1cd5-102">StrongNameKeyDelete İşlevi</span><span class="sxs-lookup"><span data-stu-id="d1cd5-102">StrongNameKeyDelete Function</span></span>
<span data-ttu-id="d1cd5-103">Belirtilen anahtar kapsayıcısı siler.</span><span class="sxs-lookup"><span data-stu-id="d1cd5-103">Deletes the specified key container.</span></span>  
  
 <span data-ttu-id="d1cd5-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="d1cd5-104">This function has been deprecated.</span></span> <span data-ttu-id="d1cd5-105">Kullanım [Iclrstrongname::strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="d1cd5-105">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1cd5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1cd5-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1cd5-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1cd5-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="d1cd5-108">[in] Silmek için anahtar kapsayıcı adı.</span><span class="sxs-lookup"><span data-stu-id="d1cd5-108">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1cd5-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d1cd5-109">Return Value</span></span>  
 <span data-ttu-id="d1cd5-110">`true`başarılı tamamlanma; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="d1cd5-110">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1cd5-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1cd5-111">Remarks</span></span>  
 <span data-ttu-id="d1cd5-112">Kullanım [Strongnamekeyınstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) importa için ortak/özel anahtar çiftini bir kapsayıcıya işlev.</span><span class="sxs-lookup"><span data-stu-id="d1cd5-112">Use the [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) function to importa a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="d1cd5-113">Varsa `StrongNameKeyDelete` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.</span><span class="sxs-lookup"><span data-stu-id="d1cd5-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1cd5-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1cd5-114">Requirements</span></span>  
 <span data-ttu-id="d1cd5-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1cd5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1cd5-116">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="d1cd5-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d1cd5-117">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d1cd5-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d1cd5-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1cd5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1cd5-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d1cd5-119">See Also</span></span>  
 [<span data-ttu-id="d1cd5-120">StrongNameKeyDelete yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1cd5-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="d1cd5-121">Strongnamekeyınstall yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1cd5-121">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="d1cd5-122">Iclrstrongname arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1cd5-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
