---
title: "ICLRStrongName::StrongNameKeyGen Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameKeyGen
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 13eef3e4c0cf4aa8de55aa96335e570ef1985e9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="2f4fc-102">ICLRStrongName::StrongNameKeyGen Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f4fc-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="2f4fc-103">Güçlü ad kullanmak için yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f4fc-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f4fc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f4fc-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f4fc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2f4fc-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="2f4fc-106">[in] İstenen anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="2f4fc-106">[in] The requested key container name.</span></span> <span data-ttu-id="2f4fc-107">`wszKeyContainer`ya da boş dize veya geçici bir ad oluşturmak için null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2f4fc-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2f4fc-108">[in] Kayıtlı anahtarı bırakın belirtir bir değer.</span><span class="sxs-lookup"><span data-stu-id="2f4fc-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="2f4fc-109">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="2f4fc-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="2f4fc-110">kullanılan 0x00000000 - `wszKeyContainer` bir geçici anahtar kapsayıcı adı oluşturmak için null.</span><span class="sxs-lookup"><span data-stu-id="2f4fc-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="2f4fc-111">0x00000001 (`SN_LEAVE_KEY`)-anahtar sol kaydedilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2f4fc-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="2f4fc-112">[out] Döndürülen ortak/özel anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="2f4fc-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="2f4fc-113">[out] Bayt olarak boyutu, `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="2f4fc-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f4fc-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2f4fc-114">Return Value</span></span>  
 <span data-ttu-id="2f4fc-115">`S_OK`Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="2f4fc-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f4fc-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f4fc-116">Remarks</span></span>  
 <span data-ttu-id="2f4fc-117">[Iclrstrongname::strongnamekeygen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) yöntemi, 1024 bit anahtar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f4fc-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="2f4fc-118">Anahtarı aldıktan sonra çağırmalıdır [Iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) ayrılmış bellek yayımlamayı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2f4fc-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f4fc-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f4fc-119">Requirements</span></span>  
 <span data-ttu-id="2f4fc-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f4fc-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f4fc-121">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2f4fc-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2f4fc-122">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2f4fc-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f4fc-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f4fc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f4fc-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2f4fc-124">See Also</span></span>  
 [<span data-ttu-id="2f4fc-125">StrongNameKeyGenEx yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f4fc-125">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [<span data-ttu-id="2f4fc-126">Iclrstrongname arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f4fc-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
