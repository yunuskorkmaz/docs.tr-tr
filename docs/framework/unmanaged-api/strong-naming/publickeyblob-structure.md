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
ms.openlocfilehash: 3b00bf8295a635871bd7263928ff21c97053cc39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176961"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="06da0-102">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="06da0-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="06da0-103">İkili biçimde, ortak/özel anahtar çiftinin ortak anahtarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="06da0-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06da0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06da0-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;
```  
  
## <a name="members"></a><span data-ttu-id="06da0-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="06da0-105">Members</span></span>  
  
|<span data-ttu-id="06da0-106">Üye</span><span class="sxs-lookup"><span data-stu-id="06da0-106">Member</span></span>|<span data-ttu-id="06da0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06da0-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="06da0-108">Ortak anahtarın imza algoritması (winCrypt.h'de tanımlandığı gibi türü) `ALG_ID`tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="06da0-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="06da0-109">Ortak anahtarın karma algoritması (türü `ALG_ID`, WinCrypt.h'de tanımlandığı şekilde) tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="06da0-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="06da0-110">Baytlarda anahtarın uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="06da0-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="06da0-111">CryptoAPI tarafından döndürülen biçimdeki anahtar değerini içeren değişken uzunlukta bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="06da0-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06da0-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06da0-112">Remarks</span></span>  
 <span data-ttu-id="06da0-113">Yapı, `PublicKeyBlob` genel/özel anahtar çiftinin ortak anahtarını temsil etmek için [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)ve diğer güçlü ad işlevleri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="06da0-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06da0-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06da0-114">Requirements</span></span>  
 <span data-ttu-id="06da0-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06da0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06da0-116">**Üstbilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="06da0-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="06da0-117">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="06da0-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="06da0-118">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06da0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06da0-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06da0-119">See also</span></span>

- [<span data-ttu-id="06da0-120">StrongNameGetPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="06da0-120">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="06da0-121">StrongNameSignatureGeneration İşlevi</span><span class="sxs-lookup"><span data-stu-id="06da0-121">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
