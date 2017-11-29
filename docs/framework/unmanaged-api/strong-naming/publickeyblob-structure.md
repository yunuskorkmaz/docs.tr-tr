---
title: "PublicKeyBlob Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: PublicKeyBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: PublicKeyBlob
helpviewer_keywords: PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e273570c77b2855d942db580be95b040870a4c01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="b1a3a-102">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="b1a3a-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="b1a3a-103">, İkili dosya biçiminde bir genel/özel anahtar çifti ortak anahtarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b1a3a-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1a3a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1a3a-104">Syntax</span></span>  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="b1a3a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b1a3a-105">Members</span></span>  
  
|<span data-ttu-id="b1a3a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b1a3a-106">Member</span></span>|<span data-ttu-id="b1a3a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1a3a-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="b1a3a-108">İmza algoritmasının tanımlayıcıyı (tür `ALG_ID`, WinCrypt.h içinde tanımlandığı gibi) ortak anahtarın.</span><span class="sxs-lookup"><span data-stu-id="b1a3a-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="b1a3a-109">Karma algoritmasının tanımlayıcıyı (tür `ALG_ID`, WinCrypt.h içinde tanımlandığı gibi) ortak anahtarın.</span><span class="sxs-lookup"><span data-stu-id="b1a3a-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="b1a3a-110">Anahtar bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="b1a3a-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="b1a3a-111">CryptoAPI tarafından döndürülen biçimindeki anahtar değerini içeren bir değişken uzunlukta bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="b1a3a-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1a3a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1a3a-112">Remarks</span></span>  
 <span data-ttu-id="b1a3a-113">`PublicKeyBlob` Yapısı tarafından kullanılan [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)ve bir genel/özel anahtar çifti ortak anahtarını temsil etmek için diğer güçlü ad işlevleri.</span><span class="sxs-lookup"><span data-stu-id="b1a3a-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1a3a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1a3a-114">Requirements</span></span>  
 <span data-ttu-id="b1a3a-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1a3a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1a3a-116">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="b1a3a-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b1a3a-117">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b1a3a-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b1a3a-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1a3a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a3a-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1a3a-119">See Also</span></span>  
 [<span data-ttu-id="b1a3a-120">StrongNameGetPublicKey işlevi</span><span class="sxs-lookup"><span data-stu-id="b1a3a-120">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 [<span data-ttu-id="b1a3a-121">StrongNameSignatureGeneration işlevi</span><span class="sxs-lookup"><span data-stu-id="b1a3a-121">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 [<span data-ttu-id="b1a3a-122">Güçlü adlandırma yapıları</span><span class="sxs-lookup"><span data-stu-id="b1a3a-122">Strong Naming Structures</span></span>](http://msdn.microsoft.com/en-us/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)
