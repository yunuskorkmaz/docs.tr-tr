---
title: StrongNameGetBlobFromImage İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b136e1fa480e53bcacfd9ea832d1dc4d1bd69f74
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162788"
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="685c6-102">StrongNameGetBlobFromImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="685c6-102">StrongNameGetBlobFromImage Function</span></span>
<span data-ttu-id="685c6-103">Belirtilen bellek adresinde derleme yansıma ikili gösterimini alır.</span><span class="sxs-lookup"><span data-stu-id="685c6-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="685c6-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="685c6-104">This function has been deprecated.</span></span> <span data-ttu-id="685c6-105">Kullanım [Iclrstrongname::strongnamegetblobfromımage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="685c6-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="685c6-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="685c6-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="685c6-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="685c6-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="685c6-108">[in] Eşlenen derleme bildirimi bellek adresi.</span><span class="sxs-lookup"><span data-stu-id="685c6-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="685c6-109">[in] Bayt cinsinden görüntü boyutu `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="685c6-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="685c6-110">[in] Görüntü ikili gösterimini içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="685c6-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="685c6-111">[out içinde] Bayt cinsinden en büyük boyutu, istenen `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="685c6-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="685c6-112">İade, bayt cinsinden gerçek boyutu bağlı, `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="685c6-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="685c6-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="685c6-113">Return Value</span></span>  
 `true` <span data-ttu-id="685c6-114">başarıyla tamamlandığında; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="685c6-114">on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="685c6-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="685c6-115">Remarks</span></span>  
 <span data-ttu-id="685c6-116">Varsa `StrongNameGetBlobFromImage` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.</span><span class="sxs-lookup"><span data-stu-id="685c6-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="685c6-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="685c6-117">Requirements</span></span>  
 <span data-ttu-id="685c6-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="685c6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="685c6-119">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="685c6-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="685c6-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="685c6-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="685c6-121">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="685c6-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="685c6-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="685c6-122">See also</span></span>

- [<span data-ttu-id="685c6-123">StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="685c6-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="685c6-124">StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="685c6-124">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="685c6-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="685c6-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
