---
title: PublicKeyBlob Yapısı
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
ms.openlocfilehash: 42cd3cc22fbbb8eb3d5ac44544fce36650b6461f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705936"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="fbf5b-102">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="fbf5b-102">PublicKeyBlob Structure</span></span>

<span data-ttu-id="fbf5b-103">Ortak/özel anahtar çiftinin ortak anahtarını ikili biçimde temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fbf5b-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbf5b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fbf5b-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;
```  
  
## <a name="members"></a><span data-ttu-id="fbf5b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fbf5b-105">Members</span></span>  
  
|<span data-ttu-id="fbf5b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fbf5b-106">Member</span></span>|<span data-ttu-id="fbf5b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fbf5b-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="fbf5b-108">Ortak anahtarın imza algoritması için tanımlayıcı ( `ALG_ID` Örneğin, WinCrypt. h içinde tanımlanmıştır).</span><span class="sxs-lookup"><span data-stu-id="fbf5b-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="fbf5b-109">Ortak anahtarın karma algoritmasının ( `ALG_ID` WinCrypt. h içinde tanımlanan türü) tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="fbf5b-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="fbf5b-110">Anahtarın bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="fbf5b-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="fbf5b-111">CryptoAPI tarafından döndürülen biçimdeki anahtar değerini içeren değişken uzunlukta bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="fbf5b-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbf5b-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fbf5b-112">Remarks</span></span>  

 <span data-ttu-id="fbf5b-113">`PublicKeyBlob`Yapı, [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)ve ortak/özel anahtar çiftinin ortak anahtarını temsil eden diğer tanımlayıcı ad işlevleri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fbf5b-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbf5b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fbf5b-114">Requirements</span></span>  

 <span data-ttu-id="fbf5b-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbf5b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbf5b-116">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="fbf5b-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="fbf5b-117">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fbf5b-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fbf5b-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbf5b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbf5b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbf5b-119">See also</span></span>

- [<span data-ttu-id="fbf5b-120">StrongNameGetPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="fbf5b-120">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="fbf5b-121">StrongNameSignatureGeneration İşlevi</span><span class="sxs-lookup"><span data-stu-id="fbf5b-121">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
