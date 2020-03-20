---
title: StrongNameTokenFromPublicKey İşlevi
ms.date: 03/30/2017
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
ms.openlocfilehash: 20be3114908ef78966eead05ae8ba6333a491404
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175063"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="4e2ad-102">StrongNameTokenFromPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="4e2ad-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="4e2ad-103">Ortak anahtarı temsil eden bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="4e2ad-103">Gets a token representing a public key.</span></span> <span data-ttu-id="4e2ad-104">Güçlü bir ad belirteci, ortak anahtarın kısaltılmış biçimidir.</span><span class="sxs-lookup"><span data-stu-id="4e2ad-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="4e2ad-105">Bu işlev amortismana kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="4e2ad-105">This function has been deprecated.</span></span> <span data-ttu-id="4e2ad-106">Bunun yerine [ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4e2ad-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e2ad-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e2ad-107">Syntax</span></span>  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e2ad-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e2ad-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="4e2ad-109">[içinde] Güçlü ad imzasını oluşturmak için kullanılan anahtar çiftinin ortak bölümünü içeren [PublicKeyBlob](publickeyblob-structure.md) türünden bir yapı.</span><span class="sxs-lookup"><span data-stu-id="4e2ad-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="4e2ad-110">[içinde] Boyutu, bayt, ve. `pbPublicKeyBlob`</span><span class="sxs-lookup"><span data-stu-id="4e2ad-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="4e2ad-111">[çıkış] Anahtara karşılık gelen güçlü ad `pbPublicKeyBlob`belirteci.</span><span class="sxs-lookup"><span data-stu-id="4e2ad-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="4e2ad-112">Ortak dil çalışma süresi belirteci döndürmek için bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="4e2ad-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="4e2ad-113">Arayan, [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak bu belleği serbest etmelidir.</span><span class="sxs-lookup"><span data-stu-id="4e2ad-113">The caller must free this memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="4e2ad-114">[çıkış] Döndürülen güçlü ad belirteci boyutu, baytlar halinde.</span><span class="sxs-lookup"><span data-stu-id="4e2ad-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e2ad-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4e2ad-115">Return Value</span></span>  
 <span data-ttu-id="4e2ad-116">`true`başarılı bir şekilde tamamlandığında; aksi `false`takdirde, .</span><span class="sxs-lookup"><span data-stu-id="4e2ad-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e2ad-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e2ad-117">Remarks</span></span>  
 <span data-ttu-id="4e2ad-118">Güçlü bir ad belirteci, meta verilerde önemli bilgileri depolarken yer kazanmak için kullanılan ortak anahtarın kısaltılmış biçimidir.</span><span class="sxs-lookup"><span data-stu-id="4e2ad-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="4e2ad-119">Özellikle, bağlı derleme başvurmak için derleme başvurularında güçlü ad belirteçleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4e2ad-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="4e2ad-120">`StrongNameTokenFromPublicKey` İşlev başarıyla tamamlanmamışsa, oluşturulan son hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini arayın.</span><span class="sxs-lookup"><span data-stu-id="4e2ad-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e2ad-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e2ad-121">Requirements</span></span>  
 <span data-ttu-id="4e2ad-122">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e2ad-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e2ad-123">**Üstbilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="4e2ad-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="4e2ad-124">**Kütüphane:** mscoree.dll'de kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="4e2ad-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="4e2ad-125">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e2ad-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e2ad-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e2ad-126">See also</span></span>

- [<span data-ttu-id="4e2ad-127">StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e2ad-127">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="4e2ad-128">StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e2ad-128">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="4e2ad-129">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="4e2ad-129">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
