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
ms.openlocfilehash: bc871c29f53a9ea4451a0fc1c747939724b0da87
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092239"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="448f8-102">ICLRStrongName2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="448f8-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="448f8-103">, SHA-2 güvenli karma algoritmaları grubunu (SHA-256, SHA-384 ve SHA-512) kullanarak tanımlayıcı adlar oluşturma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="448f8-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="448f8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="448f8-104">Methods</span></span>  
  
|<span data-ttu-id="448f8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="448f8-105">Method</span></span>|<span data-ttu-id="448f8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="448f8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="448f8-107">StrongNameGetPublicKeyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="448f8-107">StrongNameGetPublicKeyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|<span data-ttu-id="448f8-108">Ortak/özel anahtar çiftinden ortak anahtarı alır ve bir karma algoritmasını ve bir imza algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="448f8-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="448f8-109">StrongNameSignatureVerificationEx2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="448f8-109">StrongNameSignatureVerificationEx2 Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|<span data-ttu-id="448f8-110">Kesin adlandırılmış bir derlemenin imzasını doğrular ve ECMA anahtarından gerçek bir anahtara bir eşleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="448f8-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="448f8-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="448f8-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="448f8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="448f8-112">Requirements</span></span>  
 <span data-ttu-id="448f8-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="448f8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="448f8-114">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="448f8-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="448f8-115">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="448f8-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="448f8-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="448f8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
