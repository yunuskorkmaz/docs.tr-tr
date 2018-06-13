---
title: StrongNameKeyDelete İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a35ec4e3c3110616ac20cd31db134371838deda0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461935"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="d25ad-102">StrongNameKeyDelete İşlevi</span><span class="sxs-lookup"><span data-stu-id="d25ad-102">StrongNameKeyDelete Function</span></span>
<span data-ttu-id="d25ad-103">Belirtilen anahtar kapsayıcısı siler.</span><span class="sxs-lookup"><span data-stu-id="d25ad-103">Deletes the specified key container.</span></span>  
  
 <span data-ttu-id="d25ad-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="d25ad-104">This function has been deprecated.</span></span> <span data-ttu-id="d25ad-105">Kullanım [Iclrstrongname::strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="d25ad-105">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d25ad-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d25ad-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d25ad-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d25ad-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="d25ad-108">[in] Silmek için anahtar kapsayıcı adı.</span><span class="sxs-lookup"><span data-stu-id="d25ad-108">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d25ad-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d25ad-109">Return Value</span></span>  
 <span data-ttu-id="d25ad-110">`true` başarılı tamamlanma; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="d25ad-110">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d25ad-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d25ad-111">Remarks</span></span>  
 <span data-ttu-id="d25ad-112">Kullanım [Strongnamekeyınstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) importa için ortak/özel anahtar çiftini bir kapsayıcıya işlev.</span><span class="sxs-lookup"><span data-stu-id="d25ad-112">Use the [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) function to importa a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="d25ad-113">Varsa `StrongNameKeyDelete` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.</span><span class="sxs-lookup"><span data-stu-id="d25ad-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d25ad-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d25ad-114">Requirements</span></span>  
 <span data-ttu-id="d25ad-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d25ad-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d25ad-116">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="d25ad-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d25ad-117">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d25ad-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d25ad-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d25ad-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d25ad-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d25ad-119">See Also</span></span>  
 [<span data-ttu-id="d25ad-120">StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d25ad-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="d25ad-121">StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d25ad-121">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="d25ad-122">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d25ad-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
