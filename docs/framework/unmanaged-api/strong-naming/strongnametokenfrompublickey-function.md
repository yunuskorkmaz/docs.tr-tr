---
title: "StrongNameTokenFromPublicKey İşlevi"
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
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0cb649f43bfea2e11c986aa3fff5a702e2b58c25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="3282b-102">StrongNameTokenFromPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="3282b-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="3282b-103">Bir ortak anahtar temsil eden bir belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="3282b-103">Gets a token representing a public key.</span></span> <span data-ttu-id="3282b-104">Güçlü ad simgesi bir ortak anahtar kısaltılmış şeklidir.</span><span class="sxs-lookup"><span data-stu-id="3282b-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="3282b-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="3282b-105">This function has been deprecated.</span></span> <span data-ttu-id="3282b-106">Kullanım [Iclrstrongname::strongnametokenfrompublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="3282b-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3282b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3282b-107">Syntax</span></span>  
  
```  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3282b-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3282b-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="3282b-109">[in] Türü yapısını [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) sağlam ad imzası oluşturmak için kullanılan anahtar çifti ortak kısmını içerir.</span><span class="sxs-lookup"><span data-stu-id="3282b-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="3282b-110">[in] Bayt olarak boyutu, `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="3282b-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="3282b-111">[out] Güçlü ad belirtecin anahtarına karşılık gelen geçirilen `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="3282b-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="3282b-112">Ortak dil çalışma zamanı, belirteç döndürmek bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="3282b-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="3282b-113">Çağıranın bu bellek kullanarak serbest gerekir [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="3282b-113">The caller must free this memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="3282b-114">[out] Döndürülen güçlü ad belirtecin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="3282b-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3282b-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3282b-115">Return Value</span></span>  
 <span data-ttu-id="3282b-116">`true`başarılı tamamlanma; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="3282b-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3282b-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3282b-117">Remarks</span></span>  
 <span data-ttu-id="3282b-118">Güçlü ad simgesi anahtar bilgileri meta verilerde depolarken alanı kaydetmek için kullanılan bir ortak anahtar kısaltılmış şeklidir.</span><span class="sxs-lookup"><span data-stu-id="3282b-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="3282b-119">Özellikle, güçlü ad simgeleri derleme başvurularını bağımlı derlemenin başvurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3282b-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="3282b-120">Varsa `StrongNameTokenFromPublicKey` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.</span><span class="sxs-lookup"><span data-stu-id="3282b-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3282b-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3282b-121">Requirements</span></span>  
 <span data-ttu-id="3282b-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3282b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3282b-123">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="3282b-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3282b-124">**Kitaplığı:** bir kaynak olarak mscoree.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3282b-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="3282b-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3282b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3282b-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3282b-126">See Also</span></span>  
 [<span data-ttu-id="3282b-127">StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3282b-127">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="3282b-128">StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3282b-128">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="3282b-129">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="3282b-129">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
