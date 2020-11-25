---
title: ESymbolReadingPolicy Numaralandırması
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
ms.openlocfilehash: 42ce1f02294db98c5c593a5f16de5226703d5f9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733717"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="494e7-102">ESymbolReadingPolicy Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="494e7-102">ESymbolReadingPolicy Enumeration</span></span>

<span data-ttu-id="494e7-103">Program veritabanı (PDB) dosyalarını okumaya yönelik ilkeyi belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="494e7-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="494e7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="494e7-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="494e7-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="494e7-105">Members</span></span>  
  
|<span data-ttu-id="494e7-106">Üye</span><span class="sxs-lookup"><span data-stu-id="494e7-106">Member</span></span>|<span data-ttu-id="494e7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="494e7-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="494e7-108">Hata ayıklayıcının her zaman PDB dosyalarını okuduğunuzu belirtir.</span><span class="sxs-lookup"><span data-stu-id="494e7-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="494e7-109">Hata ayıklayıcının yalnızca tam güven Derlemeleriyle ilişkili PDB dosyalarını okuması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="494e7-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="494e7-110">Hata ayıklayıcının PDB dosyalarını asla okumayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="494e7-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="494e7-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="494e7-111">Remarks</span></span>  

 <span data-ttu-id="494e7-112">`ESymbolReadingPolicy`Sabit listesi [ICLRDebugManager:: SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md) yöntemiyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="494e7-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="494e7-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="494e7-113">Requirements</span></span>  

 <span data-ttu-id="494e7-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="494e7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="494e7-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="494e7-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="494e7-116">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="494e7-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="494e7-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="494e7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="494e7-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="494e7-118">See also</span></span>

- [<span data-ttu-id="494e7-119">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="494e7-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
