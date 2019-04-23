---
title: ICLRStrongName::StrongNameTokenFromAssemblyEx Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 203c8647366952b1d58799b97dfd53aea22859ed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127874"
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a><span data-ttu-id="65384-102">ICLRStrongName::StrongNameTokenFromAssemblyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65384-102">ICLRStrongName::StrongNameTokenFromAssemblyEx Method</span></span>
<span data-ttu-id="65384-103">Belirtilen derleme dosyasından tanımlayıcı ad belirteci oluşturur ve belirteci temsil eden genel anahtarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="65384-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65384-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65384-104">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65384-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65384-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="65384-106">[in] Derleme için taşınabilir yürütülebilir (PE) dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="65384-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="65384-107">[out] Döndürülen tanımlayıcı ad belirteç.</span><span class="sxs-lookup"><span data-stu-id="65384-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="65384-108">[out] Tanımlayıcı ad belirtecinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="65384-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="65384-109">[out] Döndürülen ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="65384-109">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="65384-110">[out] Ortak anahtarın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="65384-110">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65384-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="65384-111">Return Value</span></span>  
 <span data-ttu-id="65384-112">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="65384-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65384-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65384-113">Remarks</span></span>  
 <span data-ttu-id="65384-114">Genel anahtar kısaltılmış bir tanımlayıcı ad belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="65384-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="65384-115">Oluşturulan derlemeyi imzalamak için kullanılacak ortak anahtarı bir 64-bit karma belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="65384-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="65384-116">Belirteç, tanımlayıcı ad bütünleştirilmiş kodun bir parçası olan ve derleme meta verileri okuyabilir.</span><span class="sxs-lookup"><span data-stu-id="65384-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="65384-117">Anahtar alındığı ve belirteç oluşturulduktan sonra çağırmalısınız [Iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) ayrılan belleği serbest bırakmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="65384-117">After the key is retrieved and the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65384-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65384-118">Requirements</span></span>  
 <span data-ttu-id="65384-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65384-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65384-120">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="65384-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="65384-121">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="65384-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65384-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65384-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65384-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65384-123">See also</span></span>

- [<span data-ttu-id="65384-124">StrongNameTokenFromAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65384-124">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="65384-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65384-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
