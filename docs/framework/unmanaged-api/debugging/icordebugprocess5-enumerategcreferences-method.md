---
title: ICorDebugProcess5::EnumerateGCReferences Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateGCReferences
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type:
- apiref
ms.openlocfilehash: 81993f108ae9b59300b5d29402d7a423c3657757
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792442"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="d374b-102">ICorDebugProcess5::EnumerateGCReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d374b-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="d374b-103">Bir işlemde çöp toplanabilecek tüm nesneler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="d374b-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d374b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d374b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d374b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d374b-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="d374b-106">'ndaki Zayıf başvuruların da oluşturulup oluşturulmayacağını gösteren bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="d374b-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="d374b-107">`enumerateWeakReferences` `true`, `ppEnum` Numaralandırıcı hem güçlü başvuruları hem de zayıf başvuruları içerir.</span><span class="sxs-lookup"><span data-stu-id="d374b-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="d374b-108">`enumerateWeakReferences` `false`, Numaralandırıcı yalnızca güçlü başvurular içerir.</span><span class="sxs-lookup"><span data-stu-id="d374b-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="d374b-109">dışı Çöp toplanabilecek nesneler için bir Numaralandırıcı olan [ıcorıtcggcreferenceenum](icordebuggcreferenceenum-interface.md) adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d374b-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d374b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d374b-110">Remarks</span></span>  
 <span data-ttu-id="d374b-111">Bu yöntem, bir işlemdeki yönetilen herhangi bir nesne için tam kök zinciri belirlemenin bir yolunu sağlar ve bir nesnenin neden hala etkin olduğunu tespit etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d374b-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d374b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d374b-112">Requirements</span></span>  
 <span data-ttu-id="d374b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d374b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d374b-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d374b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d374b-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d374b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d374b-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d374b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d374b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d374b-117">See also</span></span>

- [<span data-ttu-id="d374b-118">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d374b-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="d374b-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d374b-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
