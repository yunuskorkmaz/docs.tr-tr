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
ms.openlocfilehash: 3a84221f94bad76d69f0dc67fe695ada3f3862f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732248"
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="fd5bc-102">StrongNameGetBlobFromImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="fd5bc-102">StrongNameGetBlobFromImage Function</span></span>

<span data-ttu-id="fd5bc-103">Belirtilen bellek adresindeki derleme görüntüsünün ikili gösterimini alır.</span><span class="sxs-lookup"><span data-stu-id="fd5bc-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="fd5bc-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="fd5bc-104">This function has been deprecated.</span></span> <span data-ttu-id="fd5bc-105">Bunun yerine [ICLRStrongName:: StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="fd5bc-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd5bc-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fd5bc-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd5bc-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd5bc-107">Parameters</span></span>  

 `pbBase`  
 <span data-ttu-id="fd5bc-108">'ndaki Eşlenen derleme bildiriminin bellek adresi.</span><span class="sxs-lookup"><span data-stu-id="fd5bc-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="fd5bc-109">'ndaki İçindeki görüntünün bayt cinsinden boyutu `pbBase` .</span><span class="sxs-lookup"><span data-stu-id="fd5bc-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="fd5bc-110">'ndaki Görüntünün ikili gösterimini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="fd5bc-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="fd5bc-111">[in, out] İstenen en büyük boyut (bayt) `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="fd5bc-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="fd5bc-112">Dönüş sonrasında, bayt cinsinden gerçek boyut `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="fd5bc-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd5bc-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fd5bc-113">Return Value</span></span>  

 <span data-ttu-id="fd5bc-114">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="fd5bc-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd5bc-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd5bc-115">Remarks</span></span>  

 <span data-ttu-id="fd5bc-116">`StrongNameGetBlobFromImage`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="fd5bc-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd5bc-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd5bc-117">Requirements</span></span>  

 <span data-ttu-id="fd5bc-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd5bc-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd5bc-119">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="fd5bc-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="fd5bc-120">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fd5bc-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fd5bc-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd5bc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd5bc-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd5bc-122">See also</span></span>

- [<span data-ttu-id="fd5bc-123">StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd5bc-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="fd5bc-124">StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd5bc-124">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="fd5bc-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd5bc-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
