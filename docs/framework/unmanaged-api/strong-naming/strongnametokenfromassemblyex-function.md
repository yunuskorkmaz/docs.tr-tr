---
title: "StrongNameTokenFromAssemblyEx İşlevi"
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
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5c118455932fd6c0bf44a486effa90632745d0e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="f7b4e-102">StrongNameTokenFromAssemblyEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="f7b4e-102">StrongNameTokenFromAssemblyEx Function</span></span>
<span data-ttu-id="f7b4e-103">Belirtilen derleme dosyasından bir güçlü ad belirteci oluşturur ve belirteci temsil eder ortak anahtarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="f7b4e-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-104">This function has been deprecated.</span></span> <span data-ttu-id="f7b4e-105">Kullanım [Iclrstrongname::strongnametokenfromassemblyex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7b4e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7b4e-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7b4e-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f7b4e-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="f7b4e-108">[in] Derleme için taşınabilir yürütülebilir (PE) dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="f7b4e-109">[out] Döndürülen güçlü ad belirteci.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="f7b4e-110">[out] Güçlü ad belirtecin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="f7b4e-111">[out] Döndürülen ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="f7b4e-112">[out] Ortak anahtarın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7b4e-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f7b4e-113">Return Value</span></span>  
 <span data-ttu-id="f7b4e-114">`true`başarılı tamamlanma; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7b4e-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7b4e-115">Remarks</span></span>  
 <span data-ttu-id="f7b4e-116">Güçlü ad simgesi bir ortak anahtar kısaltılmış şeklidir.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="f7b4e-117">Belirteç derlemeyi imzalamak için kullanılan ortak anahtarı ile oluşturulan 64 bitlik bir karma olur.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="f7b4e-118">Belirteç derleme için güçlü ad, bir parçasıdır ve derleme meta verileri okuyabilir.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="f7b4e-119">Anahtar aldı ve belirteç oluşturulduktan sonra çağırmalıdır [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) ayrılmış bellek yayımlamayı işlevi.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="f7b4e-120">Varsa `StrongNameTokenFromAssemblyEx` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7b4e-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7b4e-121">Requirements</span></span>  
 <span data-ttu-id="f7b4e-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7b4e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7b4e-123">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="f7b4e-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f7b4e-124">**Kitaplığı:** bir kaynak olarak mscoree.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f7b4e-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="f7b4e-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7b4e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7b4e-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f7b4e-126">See Also</span></span>  
 [<span data-ttu-id="f7b4e-127">StrongNameTokenFromAssemblyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7b4e-127">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [<span data-ttu-id="f7b4e-128">StrongNameTokenFromAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7b4e-128">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [<span data-ttu-id="f7b4e-129">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f7b4e-129">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
