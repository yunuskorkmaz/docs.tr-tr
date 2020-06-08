---
title: ICLRStrongName::StrongNameKeyGen Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
ms.openlocfilehash: 69ba58cc8c5235a15749281b3107481be9528f84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503984"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="a3986-102">ICLRStrongName::StrongNameKeyGen Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3986-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="a3986-103">Tanımlayıcı ad kullanımı için yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a3986-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3986-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a3986-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3986-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3986-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="a3986-106">'ndaki İstenen anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="a3986-106">[in] The requested key container name.</span></span> <span data-ttu-id="a3986-107">`wszKeyContainer`geçici bir ad oluşturmak için boş olmayan bir dize ya da null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a3986-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a3986-108">'ndaki Anahtarın kaydedilip edilmeyeceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="a3986-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="a3986-109">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="a3986-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="a3986-110">0x00000000- `wszKeyContainer` geçici anahtar kapsayıcısı adı oluşturmak için null olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a3986-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="a3986-111">0x00000001 ( `SN_LEAVE_KEY` )-anahtarın kayıtlı olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a3986-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="a3986-112">dışı Döndürülen ortak/özel anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="a3986-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="a3986-113">dışı Bayt cinsinden boyutu `ppbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="a3986-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3986-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a3986-114">Return Value</span></span>  
 <span data-ttu-id="a3986-115">`S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="a3986-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3986-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3986-116">Remarks</span></span>  
 <span data-ttu-id="a3986-117">[ICLRStrongName:: StrongNameKeyGen](iclrstrongname-strongnamekeygen-method.md) yöntemi 1024 bitlik bir anahtar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a3986-117">The [ICLRStrongName::StrongNameKeyGen](iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="a3986-118">Anahtar alındıktan sonra, ayrılan belleği serbest bırakmak için [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) metodunu çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a3986-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3986-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3986-119">Requirements</span></span>  
 <span data-ttu-id="a3986-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3986-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3986-121">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="a3986-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a3986-122">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a3986-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3986-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3986-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3986-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3986-124">See also</span></span>

- [<span data-ttu-id="a3986-125">StrongNameKeyGenEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3986-125">StrongNameKeyGenEx Method</span></span>](iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="a3986-126">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3986-126">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
