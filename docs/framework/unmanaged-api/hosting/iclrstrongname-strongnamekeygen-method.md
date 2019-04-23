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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abeb731ecd66e4412f904b085abcfc7b5b3a3c4b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169786"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="87d28-102">ICLRStrongName::StrongNameKeyGen Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87d28-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="87d28-103">Tanımlayıcı ad kullanmak için yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87d28-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87d28-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87d28-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87d28-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87d28-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="87d28-106">[in] İstenen anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="87d28-106">[in] The requested key container name.</span></span> <span data-ttu-id="87d28-107">`wszKeyContainer` ya da boş dize veya geçici bir ad oluşturmak için null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="87d28-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="87d28-108">[in] Kaydedilen anahtar bırakın belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="87d28-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="87d28-109">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="87d28-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="87d28-110">kullanılan 0x00000000 - `wszKeyContainer` geçici bir anahtar kapsayıcısı adını oluşturmak için null.</span><span class="sxs-lookup"><span data-stu-id="87d28-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="87d28-111">0x00000001 (`SN_LEAVE_KEY`)-anahtar sol kaydedilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="87d28-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="87d28-112">[out] Döndürülen ortak/özel anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="87d28-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="87d28-113">[out] Bayt cinsinden boyutu, `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="87d28-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87d28-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="87d28-114">Return Value</span></span>  
 <span data-ttu-id="87d28-115">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="87d28-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87d28-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87d28-116">Remarks</span></span>  
 <span data-ttu-id="87d28-117">[Iclrstrongname::strongnamekeygen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) yöntemi 1024 bit anahtar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87d28-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="87d28-118">Anahtarı aldıktan sonra çağırmalıdır [Iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) ayrılan belleği serbest bırakmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="87d28-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87d28-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87d28-119">Requirements</span></span>  
 <span data-ttu-id="87d28-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87d28-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87d28-121">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="87d28-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="87d28-122">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="87d28-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87d28-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87d28-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87d28-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87d28-124">See also</span></span>

- [<span data-ttu-id="87d28-125">StrongNameKeyGenEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87d28-125">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="87d28-126">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87d28-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
