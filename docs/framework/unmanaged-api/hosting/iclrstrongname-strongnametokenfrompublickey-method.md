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
ms.openlocfilehash: 919c1321f18ca163481d27fa204c78f38af1e456
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176324"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="9c15f-102">ICLRStrongName::StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c15f-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="9c15f-103">Ortak anahtarı temsil eden bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="9c15f-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="9c15f-104">Güçlü bir ad belirteci, ortak anahtarın kısaltılmış biçimidir.</span><span class="sxs-lookup"><span data-stu-id="9c15f-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c15f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c15f-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c15f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9c15f-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="9c15f-107">[içinde] Güçlü ad imzasını oluşturmak için kullanılan anahtar çiftinin ortak bölümünü içeren [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) türünden bir yapı.</span><span class="sxs-lookup"><span data-stu-id="9c15f-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="9c15f-108">[içinde] Boyutu, bayt, ve. `pbPublicKeyBlob`</span><span class="sxs-lookup"><span data-stu-id="9c15f-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="9c15f-109">[çıkış] Anahtara karşılık gelen güçlü ad `pbPublicKeyBlob`belirteci.</span><span class="sxs-lookup"><span data-stu-id="9c15f-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="9c15f-110">Ortak dil çalışma süresi belirteci döndürmek için bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="9c15f-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="9c15f-111">Arayan ICLRStrongName kullanarak bu belleği serbest [gerekir::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9c15f-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="9c15f-112">[çıkış] Döndürülen güçlü ad belirteci boyutu, baytlar halinde.</span><span class="sxs-lookup"><span data-stu-id="9c15f-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c15f-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9c15f-113">Return Value</span></span>  
 <span data-ttu-id="9c15f-114">`S_OK`yöntem başarıyla tamamlanırsa; aksi takdirde, başarısızlığı gösteren bir HRESULT değeri (liste için [Ortak HRESULT Değerleri'ne](/windows/win32/seccrypto/common-hresult-values) bakın).</span><span class="sxs-lookup"><span data-stu-id="9c15f-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c15f-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c15f-115">Remarks</span></span>  
 <span data-ttu-id="9c15f-116">Güçlü bir ad belirteci, meta verilerde önemli bilgileri depolarken yer kazanmak için kullanılan ortak anahtarın kısaltılmış biçimidir.</span><span class="sxs-lookup"><span data-stu-id="9c15f-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="9c15f-117">Özellikle, bağlı derleme başvurmak için derleme başvurularında güçlü ad belirteçleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9c15f-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c15f-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c15f-118">Requirements</span></span>  
 <span data-ttu-id="9c15f-119">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c15f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c15f-120">**Üstbilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9c15f-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9c15f-121">**Kütüphane:** mscoree.dll'de kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="9c15f-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="9c15f-122">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c15f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c15f-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c15f-123">See also</span></span>

- [<span data-ttu-id="9c15f-124">StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c15f-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="9c15f-125">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="9c15f-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="9c15f-126">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c15f-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
