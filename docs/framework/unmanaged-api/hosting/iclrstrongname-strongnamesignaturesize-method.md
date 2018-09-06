---
title: ICLRStrongName::StrongNameSignatureSize Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc5a40a0e26f116ce1700973a5000e8d6bbbd890
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799807"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="ec80e-102">ICLRStrongName::StrongNameSignatureSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec80e-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="ec80e-103">Tanımlayıcı ad imzası boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec80e-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="ec80e-104">Bu yöntem, genellikle dosyasında gecikmeli imzalanmış bir derlemeyi oluştururken ayırmak için ne kadar alan olmadığının derleyiciler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ec80e-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec80e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec80e-105">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec80e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec80e-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="ec80e-107">[in] Türünden bir yapıyı [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) tanımlayıcı ad imzası oluşturmak için kullanılan anahtar çiftinden ortak kısmını içerir.</span><span class="sxs-lookup"><span data-stu-id="ec80e-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="ec80e-108">[in] Bayt cinsinden boyutu, `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ec80e-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="ec80e-109">[in] Tanımlayıcı ad imzası depolamak için gereken bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="ec80e-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec80e-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ec80e-110">Return Value</span></span>  
 <span data-ttu-id="ec80e-111">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="ec80e-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec80e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec80e-112">Requirements</span></span>  
 <span data-ttu-id="ec80e-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec80e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec80e-114">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ec80e-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ec80e-115">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ec80e-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec80e-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec80e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec80e-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ec80e-117">See Also</span></span>  
 [<span data-ttu-id="ec80e-118">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec80e-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
