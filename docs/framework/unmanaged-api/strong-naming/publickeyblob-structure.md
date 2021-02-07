---
description: 'Daha fazla bilgi edinin: PublicKeyBlob yapısı'
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
ms.openlocfilehash: 94c1ea3d5a41bbb8941658e87f97cd6d6336187a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736506"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="d378b-103">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="d378b-103">PublicKeyBlob Structure</span></span>

<span data-ttu-id="d378b-104">Ortak/özel anahtar çiftinin ortak anahtarını ikili biçimde temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d378b-104">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d378b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d378b-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;
```  
  
## <a name="members"></a><span data-ttu-id="d378b-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d378b-106">Members</span></span>  
  
|<span data-ttu-id="d378b-107">Üye</span><span class="sxs-lookup"><span data-stu-id="d378b-107">Member</span></span>|<span data-ttu-id="d378b-108">Description</span><span class="sxs-lookup"><span data-stu-id="d378b-108">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="d378b-109">Ortak anahtarın imza algoritması için tanımlayıcı ( `ALG_ID` Örneğin, WinCrypt. h içinde tanımlanmıştır).</span><span class="sxs-lookup"><span data-stu-id="d378b-109">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="d378b-110">Ortak anahtarın karma algoritmasının ( `ALG_ID` WinCrypt. h içinde tanımlanan türü) tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="d378b-110">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="d378b-111">Anahtarın bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="d378b-111">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="d378b-112">CryptoAPI tarafından döndürülen biçimdeki anahtar değerini içeren değişken uzunlukta bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="d378b-112">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d378b-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d378b-113">Remarks</span></span>  

 <span data-ttu-id="d378b-114">`PublicKeyBlob`Yapı, [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)ve ortak/özel anahtar çiftinin ortak anahtarını temsil eden diğer tanımlayıcı ad işlevleri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d378b-114">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d378b-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d378b-115">Requirements</span></span>  

 <span data-ttu-id="d378b-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d378b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d378b-117">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="d378b-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d378b-118">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d378b-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d378b-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d378b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d378b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d378b-120">See also</span></span>

- [<span data-ttu-id="d378b-121">StrongNameGetPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="d378b-121">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="d378b-122">StrongNameSignatureGeneration İşlevi</span><span class="sxs-lookup"><span data-stu-id="d378b-122">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
