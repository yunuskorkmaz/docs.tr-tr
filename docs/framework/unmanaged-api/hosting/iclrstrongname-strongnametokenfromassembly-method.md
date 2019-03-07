---
title: ICLRStrongName::StrongNameTokenFromAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly method [.NET Framework hosting]
- StrongNameTokenFromAssembly method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: fc725afb-b66b-4015-aa44-1c0d1304197f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 78c7ee4073357af09bdd3b0edd3d848458069da9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484816"
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a><span data-ttu-id="328a0-102">ICLRStrongName::StrongNameTokenFromAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="328a0-102">ICLRStrongName::StrongNameTokenFromAssembly Method</span></span>
<span data-ttu-id="328a0-103">Belirtilen derleme dosyasından bir güçlü ad simgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="328a0-103">Creates a strong name token from the specified assembly file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="328a0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="328a0-104">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="328a0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="328a0-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="328a0-106">[in] Derleme için taşınabilir yürütülebilir (PE) dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="328a0-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="328a0-107">[out] Döndürülen tanımlayıcı ad belirteç.</span><span class="sxs-lookup"><span data-stu-id="328a0-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="328a0-108">[out] Tanımlayıcı ad belirtecinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="328a0-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="328a0-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="328a0-109">Return Value</span></span>  
 <span data-ttu-id="328a0-110">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="328a0-110">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="328a0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="328a0-111">Remarks</span></span>  
 <span data-ttu-id="328a0-112">Genel anahtar kısaltılmış bir tanımlayıcı ad belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="328a0-112">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="328a0-113">Oluşturulan derlemeyi imzalamak için kullanılacak ortak anahtarı bir 64-bit karma belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="328a0-113">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="328a0-114">Belirteç, tanımlayıcı ad bütünleştirilmiş kodun bir parçası olan ve derleme meta verileri okuyabilir.</span><span class="sxs-lookup"><span data-stu-id="328a0-114">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="328a0-115">Belirteç oluşturulduktan sonra çağırmalısınız [Iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) ayrılan belleği serbest bırakmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="328a0-115">After the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="328a0-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="328a0-116">Requirements</span></span>  
 <span data-ttu-id="328a0-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="328a0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="328a0-118">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="328a0-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="328a0-119">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="328a0-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="328a0-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="328a0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="328a0-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="328a0-121">See also</span></span>
- [<span data-ttu-id="328a0-122">StrongNameTokenFromAssemblyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="328a0-122">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="328a0-123">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="328a0-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
