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
ms.openlocfilehash: 587e2086a03e9c9ba57ae3b68de841f12543404e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435614"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="93f5b-102">ICLRStrongName::StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="93f5b-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="93f5b-103">Bir ortak anahtar temsil eden bir belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="93f5b-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="93f5b-104">Güçlü ad simgesi bir ortak anahtar kısaltılmış şeklidir.</span><span class="sxs-lookup"><span data-stu-id="93f5b-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93f5b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93f5b-105">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93f5b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="93f5b-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="93f5b-107">[in] Türü yapısını [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) sağlam ad imzası oluşturmak için kullanılan anahtar çifti ortak kısmını içerir.</span><span class="sxs-lookup"><span data-stu-id="93f5b-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="93f5b-108">[in] Bayt olarak boyutu, `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="93f5b-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="93f5b-109">[out] Güçlü ad belirtecin anahtarına karşılık gelen geçirilen `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="93f5b-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="93f5b-110">Ortak dil çalışma zamanı, belirteç döndürmek bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="93f5b-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="93f5b-111">Çağıranın bu bellek kullanarak serbest gerekir [Iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="93f5b-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="93f5b-112">[out] Döndürülen güçlü ad belirtecin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="93f5b-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93f5b-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="93f5b-113">Return Value</span></span>  
 <span data-ttu-id="93f5b-114">`S_OK` Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="93f5b-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93f5b-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93f5b-115">Remarks</span></span>  
 <span data-ttu-id="93f5b-116">Güçlü ad simgesi anahtar bilgileri meta verilerde depolarken alanı kaydetmek için kullanılan bir ortak anahtar kısaltılmış şeklidir.</span><span class="sxs-lookup"><span data-stu-id="93f5b-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="93f5b-117">Özellikle, güçlü ad simgeleri derleme başvurularını bağımlı derlemenin başvurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="93f5b-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93f5b-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93f5b-118">Requirements</span></span>  
 <span data-ttu-id="93f5b-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93f5b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93f5b-120">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="93f5b-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="93f5b-121">**Kitaplığı:** bir kaynak olarak mscoree.dll dahil</span><span class="sxs-lookup"><span data-stu-id="93f5b-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="93f5b-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93f5b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93f5b-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="93f5b-123">See Also</span></span>  
 [<span data-ttu-id="93f5b-124">StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="93f5b-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="93f5b-125">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="93f5b-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="93f5b-126">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93f5b-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
