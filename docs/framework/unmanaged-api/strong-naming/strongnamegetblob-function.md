---
title: "StrongNameGetBlob İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameGetBlob
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameGetBlob
helpviewer_keywords: StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0a88131e4a764c963d24a698935ebb12e0daa96c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="30836-102">StrongNameGetBlob İşlevi</span><span class="sxs-lookup"><span data-stu-id="30836-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="30836-103">Belirtilen arabellek yürütülebilir dosyanın belirtilen adresteki ikili gösterimidir doldurur.</span><span class="sxs-lookup"><span data-stu-id="30836-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="30836-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="30836-104">This function has been deprecated.</span></span> <span data-ttu-id="30836-105">Kullanım [Iclrstrongname::strongnamegetblob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="30836-105">Use the [ICLRStrongName::StrongNameGetBLob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30836-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30836-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30836-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30836-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="30836-108">[in] Yüklenecek yürütülebilir dosyanın geçerli bir yol.</span><span class="sxs-lookup"><span data-stu-id="30836-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="30836-109">[in] Arabelleğe hangi yürütülebilir dosyası yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="30836-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="30836-110">[içinde out] Bayt cinsinden en büyük boyutu, istenen `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="30836-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="30836-111">Return, bayt cinsinden gerçek boyutu bağlı, `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="30836-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30836-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="30836-112">Return Value</span></span>  
 <span data-ttu-id="30836-113">`true`başarılı tamamlanma; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="30836-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30836-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30836-114">Remarks</span></span>  
 <span data-ttu-id="30836-115">Varsa `StrongNameGetBlob` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.</span><span class="sxs-lookup"><span data-stu-id="30836-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30836-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30836-116">Requirements</span></span>  
 <span data-ttu-id="30836-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30836-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30836-118">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="30836-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="30836-119">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="30836-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="30836-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30836-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30836-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30836-121">See Also</span></span>  
 [<span data-ttu-id="30836-122">StrongNameGetBlob yöntemi</span><span class="sxs-lookup"><span data-stu-id="30836-122">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="30836-123">Strongnamegetblobfromımage yöntemi</span><span class="sxs-lookup"><span data-stu-id="30836-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="30836-124">Iclrstrongname arabirimi</span><span class="sxs-lookup"><span data-stu-id="30836-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
