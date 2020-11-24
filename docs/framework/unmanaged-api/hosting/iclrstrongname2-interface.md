---
title: ICLRStrongName2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRStrongName2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName2
helpviewer_keywords:
- ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type:
- apiref
ms.openlocfilehash: df570f32d694ec21e9642e75b4965e169afaccfc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677654"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="6c741-102">ICLRStrongName2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c741-102">ICLRStrongName2 Interface</span></span>

<span data-ttu-id="6c741-103">, SHA-2 güvenli karma algoritmaları grubunu (SHA-256, SHA-384 ve SHA-512) kullanarak tanımlayıcı adlar oluşturma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c741-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c741-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6c741-104">Methods</span></span>  
  
|<span data-ttu-id="6c741-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6c741-105">Method</span></span>|<span data-ttu-id="6c741-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c741-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c741-107">StrongNameGetPublicKeyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c741-107">StrongNameGetPublicKeyEx Method</span></span>](strongnamegetpublickeyex-method.md)|<span data-ttu-id="6c741-108">Ortak/özel anahtar çiftinden ortak anahtarı alır ve bir karma algoritmasını ve bir imza algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c741-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="6c741-109">StrongNameSignatureVerificationEx2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c741-109">StrongNameSignatureVerificationEx2 Method</span></span>](strongnamesignatureverificationex2-method.md)|<span data-ttu-id="6c741-110">Kesin adlandırılmış bir derlemenin imzasını doğrular ve ECMA anahtarından gerçek bir anahtara bir eşleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c741-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c741-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c741-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c741-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c741-112">Requirements</span></span>  

 <span data-ttu-id="6c741-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c741-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c741-114">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="6c741-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6c741-115">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6c741-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c741-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c741-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
