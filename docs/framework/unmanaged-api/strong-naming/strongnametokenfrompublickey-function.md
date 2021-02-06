---
description: 'Daha fazla bilgi edinin: StrongNameTokenFromPublicKey Işlevi'
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
ms.openlocfilehash: f978c9b2727db4b293b9c92a8789fbf9ba749d41
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636292"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="136ab-103">StrongNameTokenFromPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="136ab-103">StrongNameTokenFromPublicKey Function</span></span>

<span data-ttu-id="136ab-104">Ortak anahtarı temsil eden bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="136ab-104">Gets a token representing a public key.</span></span> <span data-ttu-id="136ab-105">Tanımlayıcı ad belirteci, ortak anahtarın kısaltılmış biçimidir.</span><span class="sxs-lookup"><span data-stu-id="136ab-105">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="136ab-106">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="136ab-106">This function has been deprecated.</span></span> <span data-ttu-id="136ab-107">Bunun yerine [ICLRStrongName:: StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="136ab-107">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="136ab-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="136ab-108">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="136ab-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="136ab-109">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="136ab-110">'ndaki Tanımlayıcı ad imzasını oluşturmak için kullanılan anahtar çiftinin ortak bölümünü içeren [PublicKeyBlob](publickeyblob-structure.md) türünde bir yapı.</span><span class="sxs-lookup"><span data-stu-id="136ab-110">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="136ab-111">'ndaki Bayt cinsinden boyutu `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="136ab-111">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="136ab-112">dışı Geçilen anahtara karşılık gelen tanımlayıcı ad belirteci `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="136ab-112">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="136ab-113">Ortak dil çalışma zamanı, belirtecin döndürüleceği belleği ayırır.</span><span class="sxs-lookup"><span data-stu-id="136ab-113">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="136ab-114">Çağıranın bu belleği [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="136ab-114">The caller must free this memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="136ab-115">dışı Döndürülen tanımlayıcı ad belirtecinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="136ab-115">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="136ab-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="136ab-116">Return Value</span></span>  

 <span data-ttu-id="136ab-117">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="136ab-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="136ab-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="136ab-118">Remarks</span></span>  

 <span data-ttu-id="136ab-119">Tanımlayıcı ad belirteci, anahtar bilgilerini meta verilerde depolarken alan kazanmak için kullanılan bir ortak anahtarın kısaltılmış biçimidir.</span><span class="sxs-lookup"><span data-stu-id="136ab-119">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="136ab-120">Özellikle, tanımlayıcı ad belirteçleri, bağımlı derlemeye başvurmak için derleme başvurularında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="136ab-120">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="136ab-121">`StrongNameTokenFromPublicKey`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="136ab-121">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="136ab-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="136ab-122">Requirements</span></span>  

 <span data-ttu-id="136ab-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="136ab-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="136ab-124">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="136ab-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="136ab-125">**Kitaplık:** mscoree.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="136ab-125">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="136ab-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="136ab-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="136ab-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="136ab-127">See also</span></span>

- [<span data-ttu-id="136ab-128">StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="136ab-128">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="136ab-129">StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="136ab-129">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="136ab-130">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="136ab-130">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
