---
description: ': ICLRStrongName:: StrongNameKeyGenEx yöntemi hakkında daha fazla bilgi edinin'
title: ICLRStrongName::StrongNameKeyGenEx Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type:
- apiref
ms.openlocfilehash: 3ea2bef5cc6a45066d010fc925f8866e8129faaa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799570"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="8dfcb-103">ICLRStrongName::StrongNameKeyGenEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8dfcb-103">ICLRStrongName::StrongNameKeyGenEx Method</span></span>

<span data-ttu-id="8dfcb-104">Tanımlayıcı ad kullanımı için belirtilen anahtar boyutuyla yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8dfcb-104">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dfcb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8dfcb-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8dfcb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8dfcb-106">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="8dfcb-107">'ndaki İstenen anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="8dfcb-107">[in] The requested key container name.</span></span> <span data-ttu-id="8dfcb-108">`wszKeyContainer` geçici bir ad oluşturmak için boş olmayan bir dize ya da null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8dfcb-108">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8dfcb-109">'ndaki Anahtarın kaydedilip edilmeyeceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="8dfcb-109">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="8dfcb-110">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="8dfcb-110">The following values are supported:</span></span>  
  
- <span data-ttu-id="8dfcb-111">0x00000000- `wszKeyContainer` geçici anahtar kapsayıcısı adı oluşturmak için null olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8dfcb-111">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="8dfcb-112">0x00000001 ( `SN_LEAVE_KEY` )-anahtarın kayıtlı olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8dfcb-112">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="8dfcb-113">'ndaki Anahtarın bit cinsinden istenen boyutu.</span><span class="sxs-lookup"><span data-stu-id="8dfcb-113">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="8dfcb-114">dışı Döndürülen ortak/özel anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="8dfcb-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="8dfcb-115">dışı Bayt cinsinden boyutu `ppbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="8dfcb-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8dfcb-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8dfcb-116">Return Value</span></span>  

 <span data-ttu-id="8dfcb-117">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="8dfcb-117">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8dfcb-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8dfcb-118">Remarks</span></span>  

 <span data-ttu-id="8dfcb-119">1,0 ve 1,1 .NET Framework sürümleri, bir `dwKeySize` derlemeyi güçlü bir adla imzalamak için 1024 bit gerektirir; sürüm 2,0, 2048 bit anahtarlar için destekler.</span><span class="sxs-lookup"><span data-stu-id="8dfcb-119">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="8dfcb-120">Anahtar alındıktan sonra, ayrılan belleği serbest bırakmak için [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) metodunu çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8dfcb-120">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dfcb-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8dfcb-121">Requirements</span></span>  

 <span data-ttu-id="8dfcb-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8dfcb-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dfcb-123">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="8dfcb-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8dfcb-124">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8dfcb-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8dfcb-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8dfcb-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dfcb-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8dfcb-126">See also</span></span>

- [<span data-ttu-id="8dfcb-127">StrongNameKeyGen Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8dfcb-127">StrongNameKeyGen Method</span></span>](iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="8dfcb-128">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8dfcb-128">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
