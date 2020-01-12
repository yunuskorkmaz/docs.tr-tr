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
ms.openlocfilehash: b09677a45c5d515aacb2cac709599140039a9dd8
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899551"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="ee483-102">ICLRStrongName::StrongNameKeyGenEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ee483-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="ee483-103">Tanımlayıcı ad kullanımı için belirtilen anahtar boyutuyla yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ee483-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee483-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee483-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee483-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ee483-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="ee483-106">'ndaki İstenen anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="ee483-106">[in] The requested key container name.</span></span> <span data-ttu-id="ee483-107">`wszKeyContainer`, geçici bir ad oluşturmak için boş olmayan bir dize ya da null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ee483-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ee483-108">'ndaki Anahtarın kaydedilip edilmeyeceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ee483-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="ee483-109">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="ee483-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="ee483-110">0x00000000-`wszKeyContainer` bir geçici anahtar kapsayıcısı adı oluşturmak için null olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee483-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="ee483-111">0x00000001 (`SN_LEAVE_KEY`)-anahtarın kayıtlı olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ee483-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="ee483-112">'ndaki Anahtarın bit cinsinden istenen boyutu.</span><span class="sxs-lookup"><span data-stu-id="ee483-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="ee483-113">dışı Döndürülen ortak/özel anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="ee483-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="ee483-114">dışı `ppbKeyBlob`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ee483-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee483-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ee483-115">Return Value</span></span>  
 <span data-ttu-id="ee483-116">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="ee483-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee483-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee483-117">Remarks</span></span>  
 <span data-ttu-id="ee483-118">1,0 ve 1,1 .NET Framework sürümleri, bir derlemeyi güçlü bir adla imzalamak için 1024 bit `dwKeySize` gerektirir; sürüm 2,0, 2048 bit anahtarlar için destekler.</span><span class="sxs-lookup"><span data-stu-id="ee483-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="ee483-119">Anahtar alındıktan sonra, ayrılan belleği serbest bırakmak için [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodunu çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ee483-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee483-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee483-120">Requirements</span></span>  
 <span data-ttu-id="ee483-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee483-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee483-122">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="ee483-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ee483-123">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ee483-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee483-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee483-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee483-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee483-125">See also</span></span>

- [<span data-ttu-id="ee483-126">StrongNameKeyGen Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ee483-126">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="ee483-127">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee483-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
