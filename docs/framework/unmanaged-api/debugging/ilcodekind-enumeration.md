---
title: ILCodeKind Numaralandırması
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f7e20618180961ab6d8ad0bbb79a626a4a7f4f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993490"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="71f31-102">ILCodeKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="71f31-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="71f31-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="71f31-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="71f31-104">Hata ayıklayıcı yerel değişkenler veya ReJIT izleme profil oluşturucu, eklenen kod erişmek mümkün olup olmadığını belirten değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="71f31-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71f31-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71f31-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="71f31-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="71f31-106">Members</span></span>  
  
|<span data-ttu-id="71f31-107">Üye adı</span><span class="sxs-lookup"><span data-stu-id="71f31-107">Member name</span></span>|<span data-ttu-id="71f31-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71f31-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="71f31-109">Hata ayıklayıcı erişimi ReJIT İzleme'den bilgileri yok.</span><span class="sxs-lookup"><span data-stu-id="71f31-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="71f31-110">Hata ayıklayıcı ReJIT İzleme'den bilgilerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="71f31-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71f31-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71f31-111">Remarks</span></span>  
 <span data-ttu-id="71f31-112">Üye `ILCodeKind` numaralandırma geçilebilir [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) ve [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) hata ayıklayıcı değişkenleri profil oluşturucu, eklenen erişip erişemeyeceğini belirlemek için yöntemleri ReJIT araçları ve [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) yöntemi hata ayıklayıcı erişip erişemeyeceğini belirlemek için IL işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="71f31-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71f31-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71f31-113">Requirements</span></span>  
 <span data-ttu-id="71f31-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71f31-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71f31-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71f31-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71f31-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71f31-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71f31-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71f31-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71f31-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71f31-118">See also</span></span>

- [<span data-ttu-id="71f31-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="71f31-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="71f31-120">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71f31-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="71f31-121">ReJIT: Nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="71f31-121">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
