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
ms.openlocfilehash: 189fbb1943d049dc4f52ea6cb626c02e9e25b3c7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686151"
---
# <a name="iclrreferenceassemblyenum-interface"></a><span data-ttu-id="94b7f-102">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94b7f-102">ICLRReferenceAssemblyEnum Interface</span></span>

<span data-ttu-id="94b7f-103">Ana bilgisayarın, ortak dil çalışma zamanına (CLR) yönelik derleme kimliği verilerini kullanarak bu kimlikleri oluşturmaya veya anlamaya gerek kalmadan, bir dosya veya akış tarafından başvurulan derlemeler kümesini değiştirmesine izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="94b7f-103">Provides methods that allow the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the common language runtime (CLR), without needing to create or understand those identities.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="94b7f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="94b7f-104">Methods</span></span>  
  
|<span data-ttu-id="94b7f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="94b7f-105">Method</span></span>|<span data-ttu-id="94b7f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94b7f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="94b7f-107">Get Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94b7f-107">Get Method</span></span>](iclrreferenceassemblyenum-get-method.md)|<span data-ttu-id="94b7f-108">Belirtilen dizinde derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="94b7f-108">Gets the assembly identity at the supplied index.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="94b7f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94b7f-109">Requirements</span></span>  

 <span data-ttu-id="94b7f-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94b7f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94b7f-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="94b7f-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="94b7f-112">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="94b7f-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94b7f-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94b7f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94b7f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94b7f-114">See also</span></span>

- [<span data-ttu-id="94b7f-115">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94b7f-115">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="94b7f-116">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94b7f-116">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="94b7f-117">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="94b7f-117">Hosting Interfaces</span></span>](hosting-interfaces.md)
