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
ms.openlocfilehash: aea9fb2bb9c4535e30a42ad956b04b3bb06a798a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433994"
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a><span data-ttu-id="f3966-102">ICLRStrongName::StrongNameTokenFromAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f3966-102">ICLRStrongName::StrongNameTokenFromAssembly Method</span></span>
<span data-ttu-id="f3966-103">Güçlü ad belirteci belirtilen derleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f3966-103">Creates a strong name token from the specified assembly file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3966-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3966-104">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3966-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f3966-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="f3966-106">[in] Derleme için taşınabilir yürütülebilir (PE) dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="f3966-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="f3966-107">[out] Döndürülen güçlü ad belirteci.</span><span class="sxs-lookup"><span data-stu-id="f3966-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="f3966-108">[out] Güçlü ad belirtecin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="f3966-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3966-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f3966-109">Return Value</span></span>  
 <span data-ttu-id="f3966-110">`S_OK` Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="f3966-110">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3966-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3966-111">Remarks</span></span>  
 <span data-ttu-id="f3966-112">Güçlü ad simgesi bir ortak anahtar kısaltılmış şeklidir.</span><span class="sxs-lookup"><span data-stu-id="f3966-112">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="f3966-113">Belirteç derlemeyi imzalamak için kullanılan ortak anahtarı ile oluşturulan 64 bitlik bir karma olur.</span><span class="sxs-lookup"><span data-stu-id="f3966-113">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="f3966-114">Belirteç derleme için güçlü ad, bir parçasıdır ve derleme meta verileri okuyabilir.</span><span class="sxs-lookup"><span data-stu-id="f3966-114">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="f3966-115">Belirteç oluşturulduktan sonra çağırmalıdır [Iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) ayrılmış bellek yayımlamayı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f3966-115">After the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3966-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3966-116">Requirements</span></span>  
 <span data-ttu-id="f3966-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3966-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3966-118">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f3966-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f3966-119">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f3966-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3966-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3966-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3966-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3966-121">See Also</span></span>  
 [<span data-ttu-id="f3966-122">StrongNameTokenFromAssemblyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f3966-122">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [<span data-ttu-id="f3966-123">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f3966-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
