---
title: StrongNameGetBlob İşlevi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e23232b55a841672ee193b980c310995ba688e00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049368"
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="c05e0-102">StrongNameGetBlob İşlevi</span><span class="sxs-lookup"><span data-stu-id="c05e0-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="c05e0-103">Belirtilen arabellek, yürütülebilir dosyanın belirtilen adreste ikili gösterimini ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="c05e0-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="c05e0-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="c05e0-104">This function has been deprecated.</span></span> <span data-ttu-id="c05e0-105">Kullanım [Iclrstrongname::strongnamegetblob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="c05e0-105">Use the [ICLRStrongName::StrongNameGetBLob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c05e0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c05e0-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c05e0-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c05e0-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="c05e0-108">[in] Yüklenen yürütülebilir dosyanın geçerli bir yol.</span><span class="sxs-lookup"><span data-stu-id="c05e0-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="c05e0-109">[in] Arabelleğe yürütülebilir dosyayı yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="c05e0-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="c05e0-110">[out içinde] Bayt cinsinden en büyük boyutu, istenen `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="c05e0-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="c05e0-111">İade, bayt cinsinden gerçek boyutu bağlı, `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="c05e0-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c05e0-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c05e0-112">Return Value</span></span>  
 <span data-ttu-id="c05e0-113">`true` başarıyla tamamlandığında; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="c05e0-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c05e0-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c05e0-114">Remarks</span></span>  
 <span data-ttu-id="c05e0-115">Varsa `StrongNameGetBlob` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.</span><span class="sxs-lookup"><span data-stu-id="c05e0-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c05e0-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c05e0-116">Requirements</span></span>  
 <span data-ttu-id="c05e0-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c05e0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c05e0-118">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c05e0-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c05e0-119">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c05e0-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c05e0-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c05e0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c05e0-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c05e0-121">See also</span></span>

- [<span data-ttu-id="c05e0-122">StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c05e0-122">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="c05e0-123">StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c05e0-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="c05e0-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c05e0-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
