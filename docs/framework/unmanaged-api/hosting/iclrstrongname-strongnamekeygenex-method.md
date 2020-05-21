---
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
ms.openlocfilehash: fb18b7b5ac73a1f270af6fae95a23e04b17ca5f1
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763078"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="d1b7f-102">ICLRStrongName::StrongNameKeyGenEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1b7f-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="d1b7f-103">Tanımlayıcı ad kullanımı için belirtilen anahtar boyutuyla yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d1b7f-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1b7f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d1b7f-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1b7f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1b7f-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="d1b7f-106">'ndaki İstenen anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="d1b7f-106">[in] The requested key container name.</span></span> <span data-ttu-id="d1b7f-107">`wszKeyContainer`geçici bir ad oluşturmak için boş olmayan bir dize ya da null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d1b7f-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d1b7f-108">'ndaki Anahtarın kaydedilip edilmeyeceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d1b7f-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="d1b7f-109">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d1b7f-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="d1b7f-110">0x00000000- `wszKeyContainer` geçici anahtar kapsayıcısı adı oluşturmak için null olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d1b7f-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="d1b7f-111">0x00000001 ( `SN_LEAVE_KEY` )-anahtarın kayıtlı olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d1b7f-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="d1b7f-112">'ndaki Anahtarın bit cinsinden istenen boyutu.</span><span class="sxs-lookup"><span data-stu-id="d1b7f-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="d1b7f-113">dışı Döndürülen ortak/özel anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="d1b7f-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="d1b7f-114">dışı Bayt cinsinden boyutu `ppbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="d1b7f-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1b7f-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d1b7f-115">Return Value</span></span>  
 <span data-ttu-id="d1b7f-116">`S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="d1b7f-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1b7f-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1b7f-117">Remarks</span></span>  
 <span data-ttu-id="d1b7f-118">1,0 ve 1,1 .NET Framework sürümleri, bir `dwKeySize` derlemeyi güçlü bir adla imzalamak için 1024 bit gerektirir; sürüm 2,0, 2048 bit anahtarlar için destekler.</span><span class="sxs-lookup"><span data-stu-id="d1b7f-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="d1b7f-119">Anahtar alındıktan sonra, ayrılan belleği serbest bırakmak için [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) metodunu çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d1b7f-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1b7f-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1b7f-120">Requirements</span></span>  
 <span data-ttu-id="d1b7f-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1b7f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1b7f-122">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="d1b7f-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d1b7f-123">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d1b7f-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1b7f-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1b7f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1b7f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1b7f-125">See also</span></span>

- [<span data-ttu-id="d1b7f-126">StrongNameKeyGen Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1b7f-126">StrongNameKeyGen Method</span></span>](iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="d1b7f-127">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1b7f-127">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
