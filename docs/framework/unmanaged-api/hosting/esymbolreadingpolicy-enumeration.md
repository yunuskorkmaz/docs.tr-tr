---
description: ': ESymbolReadingPolicy numaralandırması hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e84c31343b589cb6019d88fafc9b94207c5f5892
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785425"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="136be-103">ESymbolReadingPolicy Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="136be-103">ESymbolReadingPolicy Enumeration</span></span>

<span data-ttu-id="136be-104">Program veritabanı (PDB) dosyalarını okumaya yönelik ilkeyi belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="136be-104">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="136be-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="136be-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="136be-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="136be-106">Members</span></span>  
  
|<span data-ttu-id="136be-107">Üye</span><span class="sxs-lookup"><span data-stu-id="136be-107">Member</span></span>|<span data-ttu-id="136be-108">Description</span><span class="sxs-lookup"><span data-stu-id="136be-108">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="136be-109">Hata ayıklayıcının her zaman PDB dosyalarını okuduğunuzu belirtir.</span><span class="sxs-lookup"><span data-stu-id="136be-109">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="136be-110">Hata ayıklayıcının yalnızca tam güven Derlemeleriyle ilişkili PDB dosyalarını okuması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="136be-110">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="136be-111">Hata ayıklayıcının PDB dosyalarını asla okumayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="136be-111">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="136be-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="136be-112">Remarks</span></span>  

 <span data-ttu-id="136be-113">`ESymbolReadingPolicy`Sabit listesi [ICLRDebugManager:: SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md) yöntemiyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="136be-113">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="136be-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="136be-114">Requirements</span></span>  

 <span data-ttu-id="136be-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="136be-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="136be-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="136be-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="136be-117">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="136be-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="136be-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="136be-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="136be-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="136be-119">See also</span></span>

- [<span data-ttu-id="136be-120">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="136be-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
