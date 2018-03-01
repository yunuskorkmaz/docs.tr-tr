---
title: "ICLRStrongName::StrongNameKeyGenEx Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 581f486a2def90f44c0fb3f1bcf9d3bbcc1fc317
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="7d456-102">ICLRStrongName::StrongNameKeyGenEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d456-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="7d456-103">Güçlü ad kullanım için belirtilen anahtar boyutu ile yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7d456-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d456-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d456-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d456-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d456-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="7d456-106">[in] İstenen anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="7d456-106">[in] The requested key container name.</span></span> <span data-ttu-id="7d456-107">`wszKeyContainer`ya da boş dize veya geçici bir ad oluşturmak için null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d456-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="7d456-108">[in] Kayıtlı anahtarı bırakın belirtir bir değer.</span><span class="sxs-lookup"><span data-stu-id="7d456-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="7d456-109">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="7d456-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="7d456-110">kullanılan 0x00000000 - `wszKeyContainer` bir geçici anahtar kapsayıcı adı oluşturmak için null.</span><span class="sxs-lookup"><span data-stu-id="7d456-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="7d456-111">0x00000001 (`SN_LEAVE_KEY`)-anahtar sol kaydedilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d456-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="7d456-112">[in] Bit cinsinden anahtar istenen boyutu.</span><span class="sxs-lookup"><span data-stu-id="7d456-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="7d456-113">[out] Döndürülen ortak/özel anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="7d456-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="7d456-114">[out] Bayt olarak boyutu, `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="7d456-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d456-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7d456-115">Return Value</span></span>  
 <span data-ttu-id="7d456-116">`S_OK`Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="7d456-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d456-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d456-117">Remarks</span></span>  
 <span data-ttu-id="7d456-118">.NET Framework sürüm 1.0 ve 1.1 gerektiren bir `dwKeySize` derlemeyi tanımlayıcı adla; imzalamak için 1024 bit 2048 bit anahtar için desteklenen sürüm 2.0 ekler.</span><span class="sxs-lookup"><span data-stu-id="7d456-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="7d456-119">Anahtarı aldıktan sonra çağırmalıdır [Iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) ayrılmış bellek yayımlamayı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7d456-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d456-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d456-120">Requirements</span></span>  
 <span data-ttu-id="7d456-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d456-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d456-122">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7d456-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7d456-123">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7d456-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d456-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d456-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d456-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d456-125">See Also</span></span>  
 [<span data-ttu-id="7d456-126">StrongNameKeyGen Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d456-126">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="7d456-127">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d456-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
