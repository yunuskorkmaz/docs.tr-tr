---
description: 'Daha fazla bilgi edinin: CorDebugInternalFrameType numaralandırması'
title: CorDebugInternalFrameType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugInternalFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInternalFrameType
helpviewer_keywords:
- CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type:
- apiref
ms.openlocfilehash: 0479ae7602224e03086b9dacf91d360253b61818
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662006"
---
# <a name="cordebuginternalframetype-enumeration"></a><span data-ttu-id="ad40c-103">CorDebugInternalFrameType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ad40c-103">CorDebugInternalFrameType Enumeration</span></span>

<span data-ttu-id="ad40c-104">Yığın çerçevesinin türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ad40c-104">Identifies the type of stack frame.</span></span> <span data-ttu-id="ad40c-105">Bu numaralandırma [ICorDebugInternalFrame:: GetFrameType](icordebuginternalframe-getframetype-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ad40c-105">This enumeration is used by the [ICorDebugInternalFrame::GetFrameType](icordebuginternalframe-getframetype-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad40c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ad40c-106">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a><span data-ttu-id="ad40c-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ad40c-107">Members</span></span>  
  
|<span data-ttu-id="ad40c-108">Üye</span><span class="sxs-lookup"><span data-stu-id="ad40c-108">Member</span></span>|<span data-ttu-id="ad40c-109">Description</span><span class="sxs-lookup"><span data-stu-id="ad40c-109">Description</span></span>|  
|------------|-----------------|  
|`STUBFRAME_NONE`|<span data-ttu-id="ad40c-110">Null değer.</span><span class="sxs-lookup"><span data-stu-id="ad40c-110">A null value.</span></span> <span data-ttu-id="ad40c-111">`ICorDebugInternalFrame::GetFrameType`Yöntem hiçbir şekilde bu değeri döndürmez.</span><span class="sxs-lookup"><span data-stu-id="ad40c-111">The `ICorDebugInternalFrame::GetFrameType` method never returns this value.</span></span>|  
|`STUBFRAME_M2U`|<span data-ttu-id="ad40c-112">Yönetilen-yönetilmeyen bir saplama çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="ad40c-112">A managed-to-unmanaged stub frame.</span></span>|  
|`STUBFRAME_U2M`|<span data-ttu-id="ad40c-113">Yönetilmeyenden yönetilene bir saplama çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="ad40c-113">An unmanaged-to-managed stub frame.</span></span>|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|<span data-ttu-id="ad40c-114">Uygulama etki alanları arasında geçiş.</span><span class="sxs-lookup"><span data-stu-id="ad40c-114">A transition between application domains.</span></span>|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|<span data-ttu-id="ad40c-115">Hafif bir yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="ad40c-115">A lightweight method call.</span></span>|  
|`STUBFRAME_FUNC_EVAL`|<span data-ttu-id="ad40c-116">İşlev değerlendirmesinin başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="ad40c-116">The start of function evaluation.</span></span>|  
|`STUBFRAME_INTERNALCALL`|<span data-ttu-id="ad40c-117">Ortak dil çalışma zamanına bir iç çağrı.</span><span class="sxs-lookup"><span data-stu-id="ad40c-117">An internal call into the common language runtime.</span></span>|  
|`STUBFRAME_CLASS_INIT`|<span data-ttu-id="ad40c-118">Bir sınıf başlatma başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="ad40c-118">The start of a class initialization.</span></span>|  
|`STUBFRAME_EXCEPTION`|<span data-ttu-id="ad40c-119">Oluşturulan özel durum.</span><span class="sxs-lookup"><span data-stu-id="ad40c-119">An exception that is thrown.</span></span>|  
|`STUBFRAME_SECURITY`|<span data-ttu-id="ad40c-120">Kod erişim güvenliği için kullanılan çerçeve.</span><span class="sxs-lookup"><span data-stu-id="ad40c-120">A frame used for code access security.</span></span>|  
|`STUBFRAME_JIT_COMPILATION`|<span data-ttu-id="ad40c-121">Çalışma zamanı JıT olarak bir yöntemi derlemedir.</span><span class="sxs-lookup"><span data-stu-id="ad40c-121">The runtime is JIT-compiling a method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ad40c-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad40c-122">Requirements</span></span>  

 <span data-ttu-id="ad40c-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad40c-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad40c-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ad40c-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad40c-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ad40c-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad40c-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad40c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad40c-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad40c-127">See also</span></span>

- [<span data-ttu-id="ad40c-128">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="ad40c-128">Debugging Enumerations</span></span>](debugging-enumerations.md)
