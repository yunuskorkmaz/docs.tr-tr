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
ms.openlocfilehash: 0d98df05291ed8405addcfd183d7e02332e4e025
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209701"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="854ba-102">ICorDebugProcess5::EnumerateGCReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="854ba-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="854ba-103">Bir işlemde çöp toplanabilecek tüm nesneler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="854ba-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="854ba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="854ba-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="854ba-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="854ba-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="854ba-106">'ndaki Zayıf başvuruların da oluşturulup oluşturulmayacağını gösteren bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="854ba-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="854ba-107">`enumerateWeakReferences`İse `true` , `ppEnum` Numaralandırıcı hem güçlü başvuruları hem de zayıf başvuruları içerir.</span><span class="sxs-lookup"><span data-stu-id="854ba-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="854ba-108">`enumerateWeakReferences`İse `false` , Numaralandırıcı yalnızca güçlü başvurular içerir.</span><span class="sxs-lookup"><span data-stu-id="854ba-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="854ba-109">dışı Çöp toplanabilecek nesneler için bir Numaralandırıcı olan [ıcorıtcggcreferenceenum](icordebuggcreferenceenum-interface.md) adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="854ba-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="854ba-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="854ba-110">Remarks</span></span>  
 <span data-ttu-id="854ba-111">Bu yöntem, bir işlemdeki yönetilen herhangi bir nesne için tam kök zinciri belirlemenin bir yolunu sağlar ve bir nesnenin neden hala etkin olduğunu tespit etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="854ba-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="854ba-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="854ba-112">Requirements</span></span>  
 <span data-ttu-id="854ba-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="854ba-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="854ba-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="854ba-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="854ba-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="854ba-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="854ba-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="854ba-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="854ba-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="854ba-117">See also</span></span>

- [<span data-ttu-id="854ba-118">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="854ba-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="854ba-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="854ba-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
