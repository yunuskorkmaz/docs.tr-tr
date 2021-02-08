---
description: 'Daha fazla bilgi edinin: ICLRStrongName2 Interface'
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
ms.openlocfilehash: 7442bd054af735e9f1b75b05feb8724dfa993f73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781798"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="845dc-103">ICLRStrongName2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="845dc-103">ICLRStrongName2 Interface</span></span>

<span data-ttu-id="845dc-104">, SHA-2 güvenli karma algoritmaları grubunu (SHA-256, SHA-384 ve SHA-512) kullanarak tanımlayıcı adlar oluşturma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="845dc-104">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="845dc-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="845dc-105">Methods</span></span>  
  
|<span data-ttu-id="845dc-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="845dc-106">Method</span></span>|<span data-ttu-id="845dc-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="845dc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="845dc-108">StrongNameGetPublicKeyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="845dc-108">StrongNameGetPublicKeyEx Method</span></span>](strongnamegetpublickeyex-method.md)|<span data-ttu-id="845dc-109">Ortak/özel anahtar çiftinden ortak anahtarı alır ve bir karma algoritmasını ve bir imza algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="845dc-109">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="845dc-110">StrongNameSignatureVerificationEx2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="845dc-110">StrongNameSignatureVerificationEx2 Method</span></span>](strongnamesignatureverificationex2-method.md)|<span data-ttu-id="845dc-111">Kesin adlandırılmış bir derlemenin imzasını doğrular ve ECMA anahtarından gerçek bir anahtara bir eşleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="845dc-111">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="845dc-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="845dc-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="845dc-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="845dc-113">Requirements</span></span>  

 <span data-ttu-id="845dc-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="845dc-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="845dc-115">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="845dc-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="845dc-116">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="845dc-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="845dc-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="845dc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
