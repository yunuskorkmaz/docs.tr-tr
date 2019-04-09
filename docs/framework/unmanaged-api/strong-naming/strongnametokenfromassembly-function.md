---
title: StrongNameTokenFromAssembly İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f88c0feea48ee96745effc36798bb26b4ccbf3cc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168681"
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="e0750-102">StrongNameTokenFromAssembly İşlevi</span><span class="sxs-lookup"><span data-stu-id="e0750-102">StrongNameTokenFromAssembly Function</span></span>
<span data-ttu-id="e0750-103">Belirtilen derleme dosyasından bir güçlü ad simgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0750-103">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="e0750-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="e0750-104">This function has been deprecated.</span></span> <span data-ttu-id="e0750-105">Kullanım [Iclrstrongname::strongnametokenfromassembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="e0750-105">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0750-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0750-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0750-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e0750-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="e0750-108">[in] Derleme için taşınabilir yürütülebilir (PE) dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="e0750-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="e0750-109">[out] Döndürülen tanımlayıcı ad belirteç.</span><span class="sxs-lookup"><span data-stu-id="e0750-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="e0750-110">[out] Tanımlayıcı ad belirtecinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="e0750-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0750-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e0750-111">Return Value</span></span>  
 `true` <span data-ttu-id="e0750-112">başarıyla tamamlandığında; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="e0750-112">on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0750-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0750-113">Remarks</span></span>  
 <span data-ttu-id="e0750-114">Genel anahtar kısaltılmış bir tanımlayıcı ad belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="e0750-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="e0750-115">Oluşturulan derlemeyi imzalamak için kullanılacak ortak anahtarı bir 64-bit karma belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="e0750-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="e0750-116">Belirteç, tanımlayıcı ad bütünleştirilmiş kodun bir parçası olan ve derleme meta verileri okuyabilir.</span><span class="sxs-lookup"><span data-stu-id="e0750-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="e0750-117">Belirteç oluşturulduktan sonra çağırmalısınız [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) ayrılan belleği serbest bırakmak için işlevi.</span><span class="sxs-lookup"><span data-stu-id="e0750-117">After the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="e0750-118">Varsa `StrongNameTokenFromAssembly` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.</span><span class="sxs-lookup"><span data-stu-id="e0750-118">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0750-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0750-119">Requirements</span></span>  
 <span data-ttu-id="e0750-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0750-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0750-121">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e0750-121">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e0750-122">**Kitaplığı:** Bir kaynak olarak mscoree.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e0750-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 **<span data-ttu-id="e0750-123">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="e0750-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e0750-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0750-124">See also</span></span>

- [<span data-ttu-id="e0750-125">StrongNameTokenFromAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0750-125">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="e0750-126">StrongNameTokenFromAssemblyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0750-126">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="e0750-127">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0750-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
