---
title: "ICLRStrongName::StrongNameSignatureSize Yöntemi"
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
- ICLRStrongName.StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a961cca6bba24ac8a2428a20c616a2ee074b8abf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="933f5-102">ICLRStrongName::StrongNameSignatureSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="933f5-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="933f5-103">Tanımlayıcı ad imzası boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="933f5-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="933f5-104">Bu yöntem, genellikle bir gecikmeli imzalanmış derleme oluştururken dosyasında ayırmak için ne kadar alan belirlemek için derleyicileri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="933f5-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="933f5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="933f5-105">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="933f5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="933f5-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="933f5-107">[in] Türü yapısını [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) sağlam ad imzası oluşturmak için kullanılan anahtar çifti ortak kısmını içerir.</span><span class="sxs-lookup"><span data-stu-id="933f5-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="933f5-108">[in] Bayt olarak boyutu, `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="933f5-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="933f5-109">[in] Tanımlayıcı ad imzası depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="933f5-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="933f5-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="933f5-110">Return Value</span></span>  
 <span data-ttu-id="933f5-111">`S_OK`Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="933f5-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="933f5-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="933f5-112">Requirements</span></span>  
 <span data-ttu-id="933f5-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="933f5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="933f5-114">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="933f5-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="933f5-115">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="933f5-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="933f5-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="933f5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="933f5-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="933f5-117">See Also</span></span>  
 [<span data-ttu-id="933f5-118">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="933f5-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
