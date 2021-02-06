---
description: 'Daha fazla bilgi edinin: StrongNameGetBlobFromImage Işlevi'
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
ms.openlocfilehash: c68d6914d47fbb711c49c1e8432cae1bf33e771f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636359"
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="ba774-103">StrongNameGetBlobFromImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="ba774-103">StrongNameGetBlobFromImage Function</span></span>

<span data-ttu-id="ba774-104">Belirtilen bellek adresindeki derleme görüntüsünün ikili gösterimini alır.</span><span class="sxs-lookup"><span data-stu-id="ba774-104">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="ba774-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="ba774-105">This function has been deprecated.</span></span> <span data-ttu-id="ba774-106">Bunun yerine [ICLRStrongName:: StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ba774-106">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba774-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba774-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba774-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba774-108">Parameters</span></span>  

 `pbBase`  
 <span data-ttu-id="ba774-109">'ndaki Eşlenen derleme bildiriminin bellek adresi.</span><span class="sxs-lookup"><span data-stu-id="ba774-109">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="ba774-110">'ndaki İçindeki görüntünün bayt cinsinden boyutu `pbBase` .</span><span class="sxs-lookup"><span data-stu-id="ba774-110">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="ba774-111">'ndaki Görüntünün ikili gösterimini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="ba774-111">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="ba774-112">[in, out] İstenen en büyük boyut (bayt) `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="ba774-112">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="ba774-113">Dönüş sonrasında, bayt cinsinden gerçek boyut `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="ba774-113">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba774-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ba774-114">Return Value</span></span>  

 <span data-ttu-id="ba774-115">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="ba774-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba774-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba774-116">Remarks</span></span>  

 <span data-ttu-id="ba774-117">`StrongNameGetBlobFromImage`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="ba774-117">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba774-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba774-118">Requirements</span></span>  

 <span data-ttu-id="ba774-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba774-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba774-120">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="ba774-120">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ba774-121">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ba774-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ba774-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba774-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba774-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba774-123">See also</span></span>

- [<span data-ttu-id="ba774-124">StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba774-124">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="ba774-125">StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba774-125">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="ba774-126">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba774-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
