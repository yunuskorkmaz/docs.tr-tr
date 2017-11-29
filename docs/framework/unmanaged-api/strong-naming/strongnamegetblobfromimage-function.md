---
title: "StrongNameGetBlobFromImage İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameGetBlobFromImage
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameGetBlobFromImage
helpviewer_keywords: StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 423f874796320d1fbcda2ab642c71b7072642569
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="34585-102">StrongNameGetBlobFromImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="34585-102">StrongNameGetBlobFromImage Function</span></span>
<span data-ttu-id="34585-103">Belirtilen bellek adresinde derleme görüntü ikili bir gösterimini alır.</span><span class="sxs-lookup"><span data-stu-id="34585-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="34585-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="34585-104">This function has been deprecated.</span></span> <span data-ttu-id="34585-105">Kullanım [Iclrstrongname::strongnamegetblobfromımage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="34585-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34585-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34585-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34585-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34585-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="34585-108">[in] Eşlenen derleme bildirimi bellek adresi.</span><span class="sxs-lookup"><span data-stu-id="34585-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="34585-109">[in] Yansımayı bayt cinsinden boyutu `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="34585-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="34585-110">[in] Görüntü ikili gösterimini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="34585-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="34585-111">[içinde out] Bayt cinsinden en büyük boyutu, istenen `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="34585-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="34585-112">Return, bayt cinsinden gerçek boyutu bağlı, `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="34585-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34585-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="34585-113">Return Value</span></span>  
 <span data-ttu-id="34585-114">`true`başarılı tamamlanma; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="34585-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34585-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34585-115">Remarks</span></span>  
 <span data-ttu-id="34585-116">Varsa `StrongNameGetBlobFromImage` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.</span><span class="sxs-lookup"><span data-stu-id="34585-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34585-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34585-117">Requirements</span></span>  
 <span data-ttu-id="34585-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34585-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34585-119">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="34585-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="34585-120">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="34585-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="34585-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34585-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34585-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34585-122">See Also</span></span>  
 [<span data-ttu-id="34585-123">Strongnamegetblobfromımage yöntemi</span><span class="sxs-lookup"><span data-stu-id="34585-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="34585-124">StrongNameGetBlob yöntemi</span><span class="sxs-lookup"><span data-stu-id="34585-124">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="34585-125">Iclrstrongname arabirimi</span><span class="sxs-lookup"><span data-stu-id="34585-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
