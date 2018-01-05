---
title: "ILCodeKind Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ILCodeKind
api_location: mscordbi.dll
api_type: COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a79444fe379d6147895e89b25e513b7f4ac7a0ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="cbda5-102">ILCodeKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cbda5-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="cbda5-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="cbda5-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="cbda5-104">Hata ayıklayıcı yerel değişkenler veya profiler ReJIT araçları eklenen kod erişmek yapılıp yapılamayacağını belirten değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="cbda5-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbda5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cbda5-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="cbda5-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cbda5-106">Members</span></span>  
  
|<span data-ttu-id="cbda5-107">Üye adı</span><span class="sxs-lookup"><span data-stu-id="cbda5-107">Member name</span></span>|<span data-ttu-id="cbda5-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbda5-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="cbda5-109">Hata ayıklayıcı erişimi ReJIT araçları bilgileri yok.</span><span class="sxs-lookup"><span data-stu-id="cbda5-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="cbda5-110">Hata ayıklayıcı ReJIT Araçları ' bilgilerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="cbda5-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbda5-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cbda5-111">Remarks</span></span>  
 <span data-ttu-id="cbda5-112">Üye `ILCodeKind` numaralandırması için geçirilebilir [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) ve [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) hata ayıklayıcı Profil Oluşturucusu'nda eklenen değişkenleri erişebileceğini belirlemek için yöntemleri ReJIT araçları ve [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) hata ayıklayıcı erişebileceğini belirlemek amacıyla yöntemi IL işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="cbda5-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbda5-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cbda5-113">Requirements</span></span>  
 <span data-ttu-id="cbda5-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbda5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbda5-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cbda5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cbda5-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbda5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbda5-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbda5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbda5-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cbda5-118">See Also</span></span>  
 [<span data-ttu-id="cbda5-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="cbda5-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="cbda5-120">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbda5-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="cbda5-121">ReJIT: Nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cbda5-121">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
