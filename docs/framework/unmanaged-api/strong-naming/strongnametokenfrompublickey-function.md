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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 197504cbb0dd66c0cf43dee718026fc63e918d60
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798857"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="4ac03-102">StrongNameTokenFromPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="4ac03-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="4ac03-103">Ortak anahtarı temsil eden bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="4ac03-103">Gets a token representing a public key.</span></span> <span data-ttu-id="4ac03-104">Tanımlayıcı ad belirteci, ortak anahtarın kısaltılmış biçimidir.</span><span class="sxs-lookup"><span data-stu-id="4ac03-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="4ac03-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="4ac03-105">This function has been deprecated.</span></span> <span data-ttu-id="4ac03-106">Bunun yerine [ICLRStrongName:: StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ac03-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ac03-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ac03-107">Syntax</span></span>  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ac03-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4ac03-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="4ac03-109">'ndaki Tanımlayıcı ad imzasını oluşturmak için kullanılan anahtar çiftinin ortak bölümünü içeren [PublicKeyBlob](publickeyblob-structure.md) türünde bir yapı.</span><span class="sxs-lookup"><span data-stu-id="4ac03-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="4ac03-110">'ndaki Bayt cinsinden boyutu `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="4ac03-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="4ac03-111">dışı Geçilen anahtara karşılık gelen tanımlayıcı ad belirteci `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="4ac03-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="4ac03-112">Ortak dil çalışma zamanı, belirtecin döndürüleceği belleği ayırır.</span><span class="sxs-lookup"><span data-stu-id="4ac03-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="4ac03-113">Çağıranın bu belleği [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4ac03-113">The caller must free this memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="4ac03-114">dışı Döndürülen tanımlayıcı ad belirtecinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="4ac03-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ac03-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4ac03-115">Return Value</span></span>  
 <span data-ttu-id="4ac03-116">`true`başarıyla tamamlandığında; Aksi takdirde `false`,.</span><span class="sxs-lookup"><span data-stu-id="4ac03-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ac03-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ac03-117">Remarks</span></span>  
 <span data-ttu-id="4ac03-118">Tanımlayıcı ad belirteci, anahtar bilgilerini meta verilerde depolarken alan kazanmak için kullanılan bir ortak anahtarın kısaltılmış biçimidir.</span><span class="sxs-lookup"><span data-stu-id="4ac03-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="4ac03-119">Özellikle, tanımlayıcı ad belirteçleri, bağımlı derlemeye başvurmak için derleme başvurularında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4ac03-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="4ac03-120">İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo işlevini çağırın.](strongnameerrorinfo-function.md) `StrongNameTokenFromPublicKey`</span><span class="sxs-lookup"><span data-stu-id="4ac03-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ac03-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ac03-121">Requirements</span></span>  
 <span data-ttu-id="4ac03-122">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ac03-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ac03-123">**Üst bilgi** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="4ac03-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="4ac03-124">**Kitaplığı** Mscoree. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="4ac03-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="4ac03-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ac03-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ac03-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ac03-126">See also</span></span>

- [<span data-ttu-id="4ac03-127">StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4ac03-127">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="4ac03-128">StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4ac03-128">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="4ac03-129">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="4ac03-129">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
