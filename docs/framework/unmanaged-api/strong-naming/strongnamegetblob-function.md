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
ms.openlocfilehash: 2d5b3d1d39b5d4c5b7d4db073b3ffaf1c6b88373
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799107"
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="9ca90-102">StrongNameGetBlob İşlevi</span><span class="sxs-lookup"><span data-stu-id="9ca90-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="9ca90-103">Belirtilen adresteki yürütülebilir dosyanın ikili gösterimiyle belirtilen arabelleği doldurur.</span><span class="sxs-lookup"><span data-stu-id="9ca90-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="9ca90-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9ca90-104">This function has been deprecated.</span></span> <span data-ttu-id="9ca90-105">Bunun yerine [ICLRStrongName:: StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ca90-105">Use the [ICLRStrongName::StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ca90-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ca90-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ca90-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9ca90-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="9ca90-108">'ndaki Yüklenecek yürütülebilir dosyanın geçerli yolu.</span><span class="sxs-lookup"><span data-stu-id="9ca90-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="9ca90-109">'ndaki Yürütülebilir dosyanın yükleneceği arabellek.</span><span class="sxs-lookup"><span data-stu-id="9ca90-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="9ca90-110">[in, out] İstenen en büyük boyut ( `pbBlob`bayt).</span><span class="sxs-lookup"><span data-stu-id="9ca90-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="9ca90-111">Dönüş sonrasında, bayt `pbBlob`cinsinden gerçek boyut.</span><span class="sxs-lookup"><span data-stu-id="9ca90-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ca90-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9ca90-112">Return Value</span></span>  
 <span data-ttu-id="9ca90-113">`true`başarıyla tamamlandığında; Aksi takdirde `false`,.</span><span class="sxs-lookup"><span data-stu-id="9ca90-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ca90-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ca90-114">Remarks</span></span>  
 <span data-ttu-id="9ca90-115">İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo işlevini çağırın.](strongnameerrorinfo-function.md) `StrongNameGetBlob`</span><span class="sxs-lookup"><span data-stu-id="9ca90-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ca90-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9ca90-116">Requirements</span></span>  
 <span data-ttu-id="9ca90-117">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ca90-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ca90-118">**Üst bilgi** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="9ca90-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9ca90-119">**Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9ca90-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9ca90-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ca90-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca90-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ca90-121">See also</span></span>

- [<span data-ttu-id="9ca90-122">StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ca90-122">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="9ca90-123">StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ca90-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="9ca90-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9ca90-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
