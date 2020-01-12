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
ms.openlocfilehash: e437ee2ab04d3b1126ec2911553e87586e74e54e
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899624"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="04039-102">ICLRStrongName::StrongNameKeyGen Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04039-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="04039-103">Tanımlayıcı ad kullanımı için yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="04039-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04039-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04039-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04039-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04039-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="04039-106">'ndaki İstenen anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="04039-106">[in] The requested key container name.</span></span> <span data-ttu-id="04039-107">`wszKeyContainer`, geçici bir ad oluşturmak için boş olmayan bir dize ya da null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="04039-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="04039-108">'ndaki Anahtarın kaydedilip edilmeyeceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="04039-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="04039-109">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="04039-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="04039-110">0x00000000-`wszKeyContainer` bir geçici anahtar kapsayıcısı adı oluşturmak için null olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="04039-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="04039-111">0x00000001 (`SN_LEAVE_KEY`)-anahtarın kayıtlı olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="04039-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="04039-112">dışı Döndürülen ortak/özel anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="04039-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="04039-113">dışı `ppbKeyBlob`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="04039-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04039-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="04039-114">Return Value</span></span>  
 <span data-ttu-id="04039-115">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="04039-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04039-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04039-116">Remarks</span></span>  
 <span data-ttu-id="04039-117">[ICLRStrongName:: StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) yöntemi 1024 bitlik bir anahtar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="04039-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="04039-118">Anahtar alındıktan sonra, ayrılan belleği serbest bırakmak için [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodunu çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="04039-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04039-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04039-119">Requirements</span></span>  
 <span data-ttu-id="04039-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04039-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04039-121">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="04039-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="04039-122">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="04039-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04039-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04039-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04039-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04039-124">See also</span></span>

- [<span data-ttu-id="04039-125">StrongNameKeyGenEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04039-125">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="04039-126">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04039-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
