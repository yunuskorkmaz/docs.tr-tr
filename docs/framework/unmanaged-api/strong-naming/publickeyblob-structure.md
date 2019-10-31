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
ms.openlocfilehash: 6c58a0726e0869178838999c6b000e0ad975f145
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140611"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="0a68f-102">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="0a68f-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="0a68f-103">Ortak/özel anahtar çiftinin ortak anahtarını ikili biçimde temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0a68f-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a68f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a68f-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="0a68f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0a68f-105">Members</span></span>  
  
|<span data-ttu-id="0a68f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0a68f-106">Member</span></span>|<span data-ttu-id="0a68f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a68f-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="0a68f-108">Ortak anahtarın imza algoritmasının (WinCrypt. h içinde tanımlanan `ALG_ID`türü) tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="0a68f-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="0a68f-109">Ortak anahtarın karma algoritma (WinCrypt. h içinde tanımlanan `ALG_ID`türü) için tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="0a68f-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="0a68f-110">Anahtarın bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="0a68f-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="0a68f-111">CryptoAPI tarafından döndürülen biçimdeki anahtar değerini içeren değişken uzunlukta bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="0a68f-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a68f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a68f-112">Remarks</span></span>  
 <span data-ttu-id="0a68f-113">`PublicKeyBlob` yapısı, [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)ve Public/Private anahtar çiftinin ortak anahtarını temsil eden diğer tanımlayıcı ad işlevleri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0a68f-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a68f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a68f-114">Requirements</span></span>  
 <span data-ttu-id="0a68f-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a68f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a68f-116">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="0a68f-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0a68f-117">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0a68f-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0a68f-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a68f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a68f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a68f-119">See also</span></span>

- [<span data-ttu-id="0a68f-120">StrongNameGetPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="0a68f-120">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="0a68f-121">StrongNameSignatureGeneration İşlevi</span><span class="sxs-lookup"><span data-stu-id="0a68f-121">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
