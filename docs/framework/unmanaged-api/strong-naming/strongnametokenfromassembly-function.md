---
title: "StrongNameTokenFromAssembly İşlevi"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 29414522eb2586b00ba3158d79155675cb468815
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="38d59-102">StrongNameTokenFromAssembly İşlevi</span><span class="sxs-lookup"><span data-stu-id="38d59-102">StrongNameTokenFromAssembly Function</span></span>
<span data-ttu-id="38d59-103">Güçlü ad belirteci belirtilen derleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="38d59-103">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="38d59-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="38d59-104">This function has been deprecated.</span></span> <span data-ttu-id="38d59-105">Kullanım [Iclrstrongname::strongnametokenfromassembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="38d59-105">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38d59-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38d59-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38d59-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38d59-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="38d59-108">[in] Derleme için taşınabilir yürütülebilir (PE) dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="38d59-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="38d59-109">[out] Döndürülen güçlü ad belirteci.</span><span class="sxs-lookup"><span data-stu-id="38d59-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="38d59-110">[out] Güçlü ad belirtecin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="38d59-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38d59-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="38d59-111">Return Value</span></span>  
 <span data-ttu-id="38d59-112">`true`başarılı tamamlanma; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="38d59-112">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38d59-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38d59-113">Remarks</span></span>  
 <span data-ttu-id="38d59-114">Güçlü ad simgesi bir ortak anahtar kısaltılmış şeklidir.</span><span class="sxs-lookup"><span data-stu-id="38d59-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="38d59-115">Belirteç derlemeyi imzalamak için kullanılan ortak anahtarı ile oluşturulan 64 bitlik bir karma olur.</span><span class="sxs-lookup"><span data-stu-id="38d59-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="38d59-116">Belirteç derleme için güçlü ad, bir parçasıdır ve derleme meta verileri okuyabilir.</span><span class="sxs-lookup"><span data-stu-id="38d59-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="38d59-117">Belirteç oluşturulduktan sonra çağırmalıdır [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) ayrılmış bellek yayımlamayı işlevi.</span><span class="sxs-lookup"><span data-stu-id="38d59-117">After the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="38d59-118">Varsa `StrongNameTokenFromAssembly` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.</span><span class="sxs-lookup"><span data-stu-id="38d59-118">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38d59-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38d59-119">Requirements</span></span>  
 <span data-ttu-id="38d59-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38d59-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38d59-121">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="38d59-121">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="38d59-122">**Kitaplığı:** bir kaynak olarak mscoree.dll dahil</span><span class="sxs-lookup"><span data-stu-id="38d59-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="38d59-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38d59-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d59-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38d59-124">See Also</span></span>  
 [<span data-ttu-id="38d59-125">StrongNameTokenFromAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38d59-125">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [<span data-ttu-id="38d59-126">StrongNameTokenFromAssemblyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38d59-126">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [<span data-ttu-id="38d59-127">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38d59-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
