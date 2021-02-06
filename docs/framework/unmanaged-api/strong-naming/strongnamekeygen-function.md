---
description: 'Daha fazla bilgi edinin: StrongNameKeyGen Işlevi'
title: StrongNameKeyGen İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
ms.openlocfilehash: c5f4cfcfa9030ae856acf5fd59ab34a2b8338670
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636276"
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="e149f-103">StrongNameKeyGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="e149f-103">StrongNameKeyGen Function</span></span>

<span data-ttu-id="e149f-104">Tanımlayıcı ad kullanımı için yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e149f-104">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="e149f-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="e149f-105">This function has been deprecated.</span></span> <span data-ttu-id="e149f-106">Bunun yerine [ICLRStrongName:: StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e149f-106">Use the [ICLRStrongName::StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e149f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e149f-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e149f-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e149f-108">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="e149f-109">'ndaki İstenen anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="e149f-109">[in] The requested key container name.</span></span> <span data-ttu-id="e149f-110">`wszKeyContainer` geçici bir ad oluşturmak için boş olmayan bir dize veya null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e149f-110">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e149f-111">'ndaki Anahtarın kaydedilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e149f-111">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="e149f-112">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="e149f-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="e149f-113">0x00000000- `wszKeyContainer` geçici anahtar kapsayıcısı adı oluşturmak için null olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e149f-113">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="e149f-114">0x00000001 ( `SN_LEAVE_KEY` )-anahtarın kayıtlı olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e149f-114">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="e149f-115">dışı Döndürülen ortak/özel anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="e149f-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="e149f-116">dışı Bayt cinsinden boyutu `ppbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="e149f-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e149f-117">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e149f-117">Return Value</span></span>  

 <span data-ttu-id="e149f-118">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="e149f-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e149f-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e149f-119">Remarks</span></span>  

 <span data-ttu-id="e149f-120">`StrongNameKeyGen`İşlevi 1024 bitlik bir anahtar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e149f-120">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="e149f-121">Anahtar alındıktan sonra, ayrılan belleği serbest bırakmak için [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e149f-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="e149f-122">`StrongNameKeyGen`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="e149f-122">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e149f-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e149f-123">Requirements</span></span>  

 <span data-ttu-id="e149f-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e149f-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e149f-125">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="e149f-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e149f-126">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e149f-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e149f-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e149f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e149f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e149f-128">See also</span></span>

- [<span data-ttu-id="e149f-129">StrongNameKeyGen Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e149f-129">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="e149f-130">StrongNameKeyGenEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e149f-130">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="e149f-131">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e149f-131">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
