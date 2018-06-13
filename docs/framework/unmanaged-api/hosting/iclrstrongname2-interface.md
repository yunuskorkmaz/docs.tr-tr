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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bf9e3d2df8f507e118b393007c3958358a830cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432979"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="03ac5-102">ICLRStrongName2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03ac5-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="03ac5-103">Tanımlayıcı adlar SHA-2 grubunu güvenli karma algoritması (SHA-256, SHA-384 ve SHA-512) kullanarak oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="03ac5-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="03ac5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="03ac5-104">Methods</span></span>  
  
|<span data-ttu-id="03ac5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="03ac5-105">Method</span></span>|<span data-ttu-id="03ac5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03ac5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="03ac5-107">StrongNameGetPublicKeyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03ac5-107">StrongNameGetPublicKeyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|<span data-ttu-id="03ac5-108">Ortak anahtarı bir genel/özel anahtar çifti alır ve bir karma algoritması ve imza algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="03ac5-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="03ac5-109">StrongNameSignatureVerificationEx2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03ac5-109">StrongNameSignatureVerificationEx2 Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|<span data-ttu-id="03ac5-110">Türü kesin adlandırılmış bir derleme imzasını doğrular ve gerçek bir anahtara ECMA anahtarından bir eşleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="03ac5-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03ac5-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03ac5-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03ac5-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03ac5-112">Requirements</span></span>  
 <span data-ttu-id="03ac5-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03ac5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03ac5-114">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="03ac5-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="03ac5-115">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="03ac5-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03ac5-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03ac5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
