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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a361e04b6f8f39ec0083471d8cb47d5a29376c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000356"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="13f83-102">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="13f83-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="13f83-103">, İkili biçimde bir ortak/özel anahtar çifti ortak anahtarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="13f83-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13f83-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13f83-104">Syntax</span></span>  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="13f83-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="13f83-105">Members</span></span>  
  
|<span data-ttu-id="13f83-106">Üye</span><span class="sxs-lookup"><span data-stu-id="13f83-106">Member</span></span>|<span data-ttu-id="13f83-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13f83-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="13f83-108">İmza algoritması için olan tanımlayıcıyla (tür `ALG_ID`, WinCrypt.h içinde tanımlandığı şekilde) ortak anahtarın.</span><span class="sxs-lookup"><span data-stu-id="13f83-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="13f83-109">Karma algoritması için olan tanımlayıcıyla (tür `ALG_ID`, WinCrypt.h içinde tanımlandığı şekilde) ortak anahtarın.</span><span class="sxs-lookup"><span data-stu-id="13f83-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="13f83-110">Anahtarın bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="13f83-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="13f83-111">CryptoAPI tarafından verilen biçim anahtar değerini içeren bir değişken uzunluklu bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="13f83-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13f83-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13f83-112">Remarks</span></span>  
 <span data-ttu-id="13f83-113">`PublicKeyBlob` Yapısı tarafından kullanılan [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), bir ortak/özel anahtar çifti ortak anahtarını temsil etmek için İşlevler ve diğerleri tanımlayıcı ad.</span><span class="sxs-lookup"><span data-stu-id="13f83-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13f83-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13f83-114">Requirements</span></span>  
 <span data-ttu-id="13f83-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13f83-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13f83-116">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="13f83-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="13f83-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="13f83-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="13f83-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13f83-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f83-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13f83-119">See also</span></span>

- [<span data-ttu-id="13f83-120">StrongNameGetPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="13f83-120">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)
- [<span data-ttu-id="13f83-121">StrongNameSignatureGeneration İşlevi</span><span class="sxs-lookup"><span data-stu-id="13f83-121">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)
