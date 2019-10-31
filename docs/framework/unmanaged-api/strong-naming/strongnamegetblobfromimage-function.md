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
ms.openlocfilehash: 41226cd909900bd2da7bdcf9b9a49567d3042b01
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094887"
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="89643-102">StrongNameGetBlobFromImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="89643-102">StrongNameGetBlobFromImage Function</span></span>
<span data-ttu-id="89643-103">Belirtilen bellek adresindeki derleme görüntüsünün ikili gösterimini alır.</span><span class="sxs-lookup"><span data-stu-id="89643-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="89643-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="89643-104">This function has been deprecated.</span></span> <span data-ttu-id="89643-105">Bunun yerine [ICLRStrongName:: StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="89643-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89643-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89643-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89643-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="89643-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="89643-108">'ndaki Eşlenen derleme bildiriminin bellek adresi.</span><span class="sxs-lookup"><span data-stu-id="89643-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="89643-109">'ndaki `pbBase`konumundaki görüntünün bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="89643-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="89643-110">'ndaki Görüntünün ikili gösterimini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="89643-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="89643-111">[in, out] `pbBlob`istenen en büyük boyut (bayt cinsinden).</span><span class="sxs-lookup"><span data-stu-id="89643-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="89643-112">Dönüş sonrasında, `pbBlob`bayt cinsinden gerçek boyut.</span><span class="sxs-lookup"><span data-stu-id="89643-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89643-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="89643-113">Return Value</span></span>  
 <span data-ttu-id="89643-114">başarılı tamamlamada `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="89643-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89643-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89643-115">Remarks</span></span>  
 <span data-ttu-id="89643-116">`StrongNameGetBlobFromImage` işlevi başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="89643-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89643-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89643-117">Requirements</span></span>  
 <span data-ttu-id="89643-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89643-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89643-119">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="89643-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="89643-120">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="89643-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="89643-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89643-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89643-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89643-122">See also</span></span>

- [<span data-ttu-id="89643-123">StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="89643-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="89643-124">StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="89643-124">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="89643-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89643-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
