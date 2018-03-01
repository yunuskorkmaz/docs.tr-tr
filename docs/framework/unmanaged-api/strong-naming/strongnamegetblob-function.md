---
title: "StrongNameGetBlob İşlevi"
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
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b1948a0d8a8536ebe9b0531eecaf3df446252b0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="ade65-102">StrongNameGetBlob İşlevi</span><span class="sxs-lookup"><span data-stu-id="ade65-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="ade65-103">Belirtilen arabellek yürütülebilir dosyanın belirtilen adresteki ikili gösterimidir doldurur.</span><span class="sxs-lookup"><span data-stu-id="ade65-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="ade65-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="ade65-104">This function has been deprecated.</span></span> <span data-ttu-id="ade65-105">Kullanım [Iclrstrongname::strongnamegetblob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="ade65-105">Use the [ICLRStrongName::StrongNameGetBLob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ade65-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ade65-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ade65-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ade65-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="ade65-108">[in] Yüklenecek yürütülebilir dosyanın geçerli bir yol.</span><span class="sxs-lookup"><span data-stu-id="ade65-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="ade65-109">[in] Arabelleğe hangi yürütülebilir dosyası yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="ade65-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="ade65-110">[içinde out] Bayt cinsinden en büyük boyutu, istenen `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="ade65-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="ade65-111">Return, bayt cinsinden gerçek boyutu bağlı, `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="ade65-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ade65-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ade65-112">Return Value</span></span>  
 <span data-ttu-id="ade65-113">`true`başarılı tamamlanma; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="ade65-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ade65-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ade65-114">Remarks</span></span>  
 <span data-ttu-id="ade65-115">Varsa `StrongNameGetBlob` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.</span><span class="sxs-lookup"><span data-stu-id="ade65-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ade65-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ade65-116">Requirements</span></span>  
 <span data-ttu-id="ade65-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ade65-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ade65-118">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="ade65-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ade65-119">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ade65-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ade65-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ade65-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade65-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ade65-121">See Also</span></span>  
 [<span data-ttu-id="ade65-122">StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ade65-122">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="ade65-123">StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ade65-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="ade65-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ade65-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
