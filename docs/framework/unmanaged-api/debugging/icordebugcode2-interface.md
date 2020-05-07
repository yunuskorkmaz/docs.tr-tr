---
title: ICorDebugCode2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugCode2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2
helpviewer_keywords:
- ICorDebugCode2 interface [.NET Framework debugging]
ms.assetid: 9321903b-7dea-40d8-ba32-99016c00cc46
topic_type:
- apiref
ms.openlocfilehash: 39767ea2603018d088aaefc5da32879aaf49fee6
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893481"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="83916-102">ICorDebugCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83916-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="83916-103">"ICorDebugCode" yeteneklerini genişleten yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="83916-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="83916-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="83916-104">Methods</span></span>  
  
|<span data-ttu-id="83916-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="83916-105">Method</span></span>|<span data-ttu-id="83916-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83916-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="83916-107">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83916-107">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="83916-108">Bu kod nesnesinin oluştuğu kod öbeklerini alır.</span><span class="sxs-lookup"><span data-stu-id="83916-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="83916-109">GetCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83916-109">GetCompilerFlags Method</span></span>](icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="83916-110">Bu kod nesnesinin yerel görüntü Oluşturucu (Ngen. exe) kullanılarak derlenen veya oluşturulan koşulları belirten bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="83916-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83916-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83916-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="83916-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="83916-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83916-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83916-113">Requirements</span></span>  
 <span data-ttu-id="83916-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83916-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83916-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="83916-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83916-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="83916-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83916-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83916-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83916-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83916-118">See also</span></span>

- [<span data-ttu-id="83916-119">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83916-119">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="83916-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="83916-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
