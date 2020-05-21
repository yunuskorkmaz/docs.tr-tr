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
ms.openlocfilehash: 9715369f4cf1b2a7078be14a2fc597f735ab6fd3
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763169"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="e542b-102">ICLRStrongName2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e542b-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="e542b-103">, SHA-2 güvenli karma algoritmaları grubunu (SHA-256, SHA-384 ve SHA-512) kullanarak tanımlayıcı adlar oluşturma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e542b-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e542b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e542b-104">Methods</span></span>  
  
|<span data-ttu-id="e542b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e542b-105">Method</span></span>|<span data-ttu-id="e542b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e542b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e542b-107">StrongNameGetPublicKeyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e542b-107">StrongNameGetPublicKeyEx Method</span></span>](strongnamegetpublickeyex-method.md)|<span data-ttu-id="e542b-108">Ortak/özel anahtar çiftinden ortak anahtarı alır ve bir karma algoritmasını ve bir imza algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e542b-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="e542b-109">StrongNameSignatureVerificationEx2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e542b-109">StrongNameSignatureVerificationEx2 Method</span></span>](strongnamesignatureverificationex2-method.md)|<span data-ttu-id="e542b-110">Kesin adlandırılmış bir derlemenin imzasını doğrular ve ECMA anahtarından gerçek bir anahtara bir eşleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="e542b-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e542b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e542b-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e542b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e542b-112">Requirements</span></span>  
 <span data-ttu-id="e542b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e542b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e542b-114">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="e542b-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e542b-115">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="e542b-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e542b-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e542b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
