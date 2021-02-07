---
description: 'Daha fazla bilgi edinin: StrongNameKeyGenEx Işlevi'
title: StrongNameKeyGenEx İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
ms.openlocfilehash: b6c103d16cac1b4668e4b478a0947970b5b44a0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686836"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="a7a7d-103">StrongNameKeyGenEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="a7a7d-103">StrongNameKeyGenEx Function</span></span>

<span data-ttu-id="a7a7d-104">Tanımlayıcı ad kullanımı için belirtilen anahtar boyutuyla yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-104">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="a7a7d-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-105">This function has been deprecated.</span></span> <span data-ttu-id="a7a7d-106">Bunun yerine [ICLRStrongName:: StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-106">Use the [ICLRStrongName::StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7a7d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7a7d-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7a7d-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7a7d-108">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="a7a7d-109">'ndaki İstenen anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-109">[in] The requested key container name.</span></span> <span data-ttu-id="a7a7d-110">`wszKeyContainer` geçici bir ad oluşturmak için boş olmayan bir dize veya null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-110">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a7a7d-111">'ndaki Anahtarın kaydedilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-111">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="a7a7d-112">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="a7a7d-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="a7a7d-113">0x00000000- `wszKeyContainer` geçici anahtar kapsayıcısı adı oluşturmak için null olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-113">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="a7a7d-114">0x00000001 ( `SN_LEAVE_KEY` )-anahtarın kayıtlı olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-114">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="a7a7d-115">'ndaki Anahtarın bit cinsinden istenen boyutu.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-115">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="a7a7d-116">dışı Döndürülen ortak/özel anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-116">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="a7a7d-117">dışı Bayt cinsinden boyutu `ppbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="a7a7d-117">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7a7d-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a7a7d-118">Return Value</span></span>  

 <span data-ttu-id="a7a7d-119">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="a7a7d-119">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7a7d-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7a7d-120">Remarks</span></span>  

 <span data-ttu-id="a7a7d-121">1,0 ve 1,1 .NET Framework sürümleri, bir `dwKeySize` derlemeyi güçlü bir adla imzalamak için 1024 bit gerektirir; sürüm 2,0, 2048 bit anahtarlar için destekler.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-121">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="a7a7d-122">Anahtar alındıktan sonra, ayrılan belleği serbest bırakmak için [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-122">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="a7a7d-123">`StrongNameKeyGenEx`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-123">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7a7d-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7a7d-124">Requirements</span></span>  

 <span data-ttu-id="a7a7d-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7a7d-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7a7d-126">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="a7a7d-126">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a7a7d-127">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a7a7d-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a7a7d-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7a7d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a7d-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-129">See also</span></span>

- [<span data-ttu-id="a7a7d-130">StrongNameKeyGenEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7a7d-130">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="a7a7d-131">StrongNameKeyGen Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7a7d-131">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="a7a7d-132">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7a7d-132">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
