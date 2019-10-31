---
title: ICLRReferenceAssemblyEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum
helpviewer_keywords:
- ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: 8adbf092-c3ba-4bee-b25b-0de6e43a4ce5
topic_type:
- apiref
ms.openlocfilehash: 466b0ceec8ce9c9800393f96055730ecafc153b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120542"
---
# <a name="iclrreferenceassemblyenum-interface"></a><span data-ttu-id="6e913-102">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e913-102">ICLRReferenceAssemblyEnum Interface</span></span>
<span data-ttu-id="6e913-103">Ana bilgisayarın, ortak dil çalışma zamanına (CLR) yönelik derleme kimliği verilerini kullanarak bu kimlikleri oluşturmaya veya anlamaya gerek kalmadan, bir dosya veya akış tarafından başvurulan derlemeler kümesini değiştirmesine izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e913-103">Provides methods that allow the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the common language runtime (CLR), without needing to create or understand those identities.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e913-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6e913-104">Methods</span></span>  
  
|<span data-ttu-id="6e913-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6e913-105">Method</span></span>|<span data-ttu-id="6e913-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e913-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e913-107">Get Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e913-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-get-method.md)|<span data-ttu-id="6e913-108">Belirtilen dizinde derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="6e913-108">Gets the assembly identity at the supplied index.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6e913-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e913-109">Requirements</span></span>  
 <span data-ttu-id="6e913-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e913-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e913-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6e913-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e913-112">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="6e913-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e913-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e913-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e913-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e913-114">See also</span></span>

- [<span data-ttu-id="6e913-115">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e913-115">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="6e913-116">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e913-116">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="6e913-117">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6e913-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
