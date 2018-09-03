---
title: ICLRStrongName::StrongNameTokenFromPublicKey Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98c0dbbbe65d8f8c0b0196c82db1a8fd2b0ee3dd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468252"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="f7617-102">ICLRStrongName::StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7617-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="f7617-103">Bir ortak anahtar temsil eden bir belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="f7617-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="f7617-104">Genel anahtar kısaltılmış bir tanımlayıcı ad belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="f7617-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7617-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7617-105">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7617-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f7617-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="f7617-107">[in] Türünden bir yapıyı [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) tanımlayıcı ad imzası oluşturmak için kullanılan anahtar çiftinden ortak kısmını içerir.</span><span class="sxs-lookup"><span data-stu-id="f7617-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="f7617-108">[in] Bayt cinsinden boyutu, `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="f7617-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="f7617-109">[out] Anahtarına karşılık gelen tanımlayıcı ad belirteç geçirilen `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="f7617-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="f7617-110">Ortak dil çalışma zamanı, bir belirteç döndürecek şekilde bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="f7617-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="f7617-111">Çağıranın bu bellek kullanarak ücretsiz gerekir [Iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f7617-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="f7617-112">[out] Döndürülen tanımlayıcı ad belirtecinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="f7617-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7617-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f7617-113">Return Value</span></span>  
 <span data-ttu-id="f7617-114">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="f7617-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7617-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7617-115">Remarks</span></span>  
 <span data-ttu-id="f7617-116">Tanımlayıcı ad anahtar bilgilerini meta verileri depolarken alanından tasarruf etmek için kullanılan genel anahtar kısaltılmış belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="f7617-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="f7617-117">Özellikle, tanımlayıcı ad belirteçleri, derleme başvurularını bağımlı derlemeye başvurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f7617-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7617-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7617-118">Requirements</span></span>  
 <span data-ttu-id="f7617-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7617-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7617-120">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f7617-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f7617-121">**Kitaplığı:** bir kaynak olarak mscoree.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f7617-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="f7617-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7617-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7617-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f7617-123">See Also</span></span>  
 [<span data-ttu-id="f7617-124">StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7617-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="f7617-125">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="f7617-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="f7617-126">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f7617-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
