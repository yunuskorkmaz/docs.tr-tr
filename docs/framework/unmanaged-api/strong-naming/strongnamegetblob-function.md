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
ms.openlocfilehash: e99346ecca651346b46c220a5e427cbc7f4c4697
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095010"
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="9efbf-102">StrongNameGetBlob İşlevi</span><span class="sxs-lookup"><span data-stu-id="9efbf-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="9efbf-103">Belirtilen adresteki yürütülebilir dosyanın ikili gösterimiyle belirtilen arabelleği doldurur.</span><span class="sxs-lookup"><span data-stu-id="9efbf-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="9efbf-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9efbf-104">This function has been deprecated.</span></span> <span data-ttu-id="9efbf-105">Bunun yerine [ICLRStrongName:: StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9efbf-105">Use the [ICLRStrongName::StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9efbf-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9efbf-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9efbf-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9efbf-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="9efbf-108">'ndaki Yüklenecek yürütülebilir dosyanın geçerli yolu.</span><span class="sxs-lookup"><span data-stu-id="9efbf-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="9efbf-109">'ndaki Yürütülebilir dosyanın yükleneceği arabellek.</span><span class="sxs-lookup"><span data-stu-id="9efbf-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="9efbf-110">[in, out] `pbBlob`istenen en büyük boyut (bayt cinsinden).</span><span class="sxs-lookup"><span data-stu-id="9efbf-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="9efbf-111">Dönüş sonrasında, `pbBlob`bayt cinsinden gerçek boyut.</span><span class="sxs-lookup"><span data-stu-id="9efbf-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9efbf-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9efbf-112">Return Value</span></span>  
 <span data-ttu-id="9efbf-113">başarılı tamamlamada `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="9efbf-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9efbf-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9efbf-114">Remarks</span></span>  
 <span data-ttu-id="9efbf-115">`StrongNameGetBlob` işlevi başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="9efbf-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9efbf-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9efbf-116">Requirements</span></span>  
 <span data-ttu-id="9efbf-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9efbf-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9efbf-118">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="9efbf-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9efbf-119">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9efbf-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9efbf-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9efbf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9efbf-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9efbf-121">See also</span></span>

- [<span data-ttu-id="9efbf-122">StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9efbf-122">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="9efbf-123">StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9efbf-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="9efbf-124">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9efbf-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
