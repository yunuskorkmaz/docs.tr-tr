---
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
ms.openlocfilehash: 4844701784a3e6a1008a5deb2bdff3b3ba47aa7e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691415"
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="72747-102">StrongNameKeyGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="72747-102">StrongNameKeyGen Function</span></span>

<span data-ttu-id="72747-103">Tanımlayıcı ad kullanımı için yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72747-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="72747-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="72747-104">This function has been deprecated.</span></span> <span data-ttu-id="72747-105">Bunun yerine [ICLRStrongName:: StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="72747-105">Use the [ICLRStrongName::StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72747-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="72747-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72747-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72747-107">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="72747-108">'ndaki İstenen anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="72747-108">[in] The requested key container name.</span></span> <span data-ttu-id="72747-109">`wszKeyContainer` geçici bir ad oluşturmak için boş olmayan bir dize veya null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="72747-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="72747-110">'ndaki Anahtarın kaydedilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="72747-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="72747-111">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="72747-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="72747-112">0x00000000- `wszKeyContainer` geçici anahtar kapsayıcısı adı oluşturmak için null olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72747-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="72747-113">0x00000001 ( `SN_LEAVE_KEY` )-anahtarın kayıtlı olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="72747-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="72747-114">dışı Döndürülen ortak/özel anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="72747-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="72747-115">dışı Bayt cinsinden boyutu `ppbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="72747-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72747-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="72747-116">Return Value</span></span>  

 <span data-ttu-id="72747-117">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="72747-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72747-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72747-118">Remarks</span></span>  

 <span data-ttu-id="72747-119">`StrongNameKeyGen`İşlevi 1024 bitlik bir anahtar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72747-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="72747-120">Anahtar alındıktan sonra, ayrılan belleği serbest bırakmak için [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="72747-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="72747-121">`StrongNameKeyGen`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="72747-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72747-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72747-122">Requirements</span></span>  

 <span data-ttu-id="72747-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72747-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72747-124">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="72747-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="72747-125">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="72747-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72747-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72747-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72747-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72747-127">See also</span></span>

- [<span data-ttu-id="72747-128">StrongNameKeyGen Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72747-128">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="72747-129">StrongNameKeyGenEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72747-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="72747-130">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72747-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
