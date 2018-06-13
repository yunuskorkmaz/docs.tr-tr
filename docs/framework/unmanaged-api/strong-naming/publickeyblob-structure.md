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
ms.openlocfilehash: d7577a24a023c38370f5ac1f8c471ce31409e75d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459345"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="1f349-102">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="1f349-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="1f349-103">, İkili dosya biçiminde bir genel/özel anahtar çifti ortak anahtarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1f349-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f349-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f349-104">Syntax</span></span>  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="1f349-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1f349-105">Members</span></span>  
  
|<span data-ttu-id="1f349-106">Üye</span><span class="sxs-lookup"><span data-stu-id="1f349-106">Member</span></span>|<span data-ttu-id="1f349-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f349-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="1f349-108">İmza algoritmasının tanımlayıcıyı (tür `ALG_ID`, WinCrypt.h içinde tanımlandığı gibi) ortak anahtarın.</span><span class="sxs-lookup"><span data-stu-id="1f349-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="1f349-109">Karma algoritmasının tanımlayıcıyı (tür `ALG_ID`, WinCrypt.h içinde tanımlandığı gibi) ortak anahtarın.</span><span class="sxs-lookup"><span data-stu-id="1f349-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="1f349-110">Anahtar bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="1f349-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="1f349-111">CryptoAPI tarafından döndürülen biçimindeki anahtar değerini içeren bir değişken uzunlukta bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="1f349-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f349-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f349-112">Remarks</span></span>  
 <span data-ttu-id="1f349-113">`PublicKeyBlob` Yapısı tarafından kullanılan [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)ve bir genel/özel anahtar çifti ortak anahtarını temsil etmek için diğer güçlü ad işlevleri.</span><span class="sxs-lookup"><span data-stu-id="1f349-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f349-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f349-114">Requirements</span></span>  
 <span data-ttu-id="1f349-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f349-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f349-116">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="1f349-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="1f349-117">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1f349-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1f349-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f349-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f349-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f349-119">See Also</span></span>  
 [<span data-ttu-id="1f349-120">StrongNameGetPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="1f349-120">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 [<span data-ttu-id="1f349-121">StrongNameSignatureGeneration İşlevi</span><span class="sxs-lookup"><span data-stu-id="1f349-121">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 [<span data-ttu-id="1f349-122">Güçlü adlandırma yapıları</span><span class="sxs-lookup"><span data-stu-id="1f349-122">Strong Naming Structures</span></span>](http://msdn.microsoft.com/library/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)
