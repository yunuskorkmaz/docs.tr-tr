---
description: 'Daha fazla bilgi edinin: StrongNameGetBlob Işlevi'
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
ms.openlocfilehash: 72f7ce50ce6170a23e5b24b68f911ff58bebe3bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736446"
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="73817-103">StrongNameGetBlob İşlevi</span><span class="sxs-lookup"><span data-stu-id="73817-103">StrongNameGetBlob Function</span></span>

<span data-ttu-id="73817-104">Belirtilen adresteki yürütülebilir dosyanın ikili gösterimiyle belirtilen arabelleği doldurur.</span><span class="sxs-lookup"><span data-stu-id="73817-104">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="73817-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="73817-105">This function has been deprecated.</span></span> <span data-ttu-id="73817-106">Bunun yerine [ICLRStrongName:: StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="73817-106">Use the [ICLRStrongName::StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73817-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73817-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73817-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="73817-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="73817-109">'ndaki Yüklenecek yürütülebilir dosyanın geçerli yolu.</span><span class="sxs-lookup"><span data-stu-id="73817-109">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="73817-110">'ndaki Yürütülebilir dosyanın yükleneceği arabellek.</span><span class="sxs-lookup"><span data-stu-id="73817-110">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="73817-111">[in, out] İstenen en büyük boyut (bayt) `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="73817-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="73817-112">Dönüş sonrasında, bayt cinsinden gerçek boyut `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="73817-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73817-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="73817-113">Return Value</span></span>  

 <span data-ttu-id="73817-114">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="73817-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73817-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73817-115">Remarks</span></span>  

 <span data-ttu-id="73817-116">`StrongNameGetBlob`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="73817-116">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73817-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73817-117">Requirements</span></span>  

 <span data-ttu-id="73817-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73817-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73817-119">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="73817-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="73817-120">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="73817-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="73817-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73817-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73817-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73817-122">See also</span></span>

- [<span data-ttu-id="73817-123">StrongNameGetBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="73817-123">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="73817-124">StrongNameGetBlobFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="73817-124">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="73817-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="73817-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
