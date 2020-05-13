---
title: ICorDebugProcess5::EnumerateHeap Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
ms.openlocfilehash: 9386c77cc98df17d797d5886e1603ffc4824b6dc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205232"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="84979-102">ICorDebugProcess5::EnumerateHeap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84979-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="84979-103">Yönetilen yığındaki nesneler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="84979-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84979-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84979-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84979-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84979-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="84979-106">dışı Yönetilen yığında bulunan nesneler için bir Numaralandırıcı olan [ICorDebugHeapEnum](icordebugheapenum-interface.md) arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="84979-106">[out] A pointer to the address of an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84979-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84979-107">Remarks</span></span>  
 <span data-ttu-id="84979-108">Yöntemi çağırmadan önce `ICorDebugProcess5::EnumerateHeap` , [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) metodunu çağırmanız ve `areGCStructuresValid` döndürülen [COR_HEAPINFO](cor-heapinfo-structure.md) nesnesinin alanının değerini inceleyerek, atık toplama yığınının geçerli durumunda sıralanabilir olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="84979-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="84979-109">Ayrıca, `ICorDebugProcess5::EnumerateHeap` `E_FAIL` yönetilen yığın için bellekten önce, işlemin kullanım ömrü içinde çok erken bir şekilde iliştirmiş olmanız halinde döndürür.</span><span class="sxs-lookup"><span data-stu-id="84979-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="84979-110">[ICorDebugHeapEnum](icordebugheapenum-interface.md) arabirimi nesnesi, [cor_heapobject](cor-heapobject-structure.md) nesneleri Listeletmanızı sağlayan ıcordebugger genum arabiriminden türetilmiş standart bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="84979-110">The [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="84979-111">Bu yöntem, [ICorDebugHeapEnum](icordebugheapenum-interface.md) toplama nesnesini tüm nesneler hakkında bilgi sağlayan [cor_heapobject](cor-heapobject-structure.md) örneklerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="84979-111">This method populates the [ICorDebugHeapEnum](icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="84979-112">Koleksiyon, herhangi bir nesne tarafından kök olmayan ancak henüz atık toplayıcı tarafından toplanmamış nesneler hakkında bilgi sağlayan [cor_heapobject](cor-heapobject-structure.md) örnekleri de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="84979-112">The collection may also include [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84979-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84979-113">Requirements</span></span>  
 <span data-ttu-id="84979-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84979-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84979-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="84979-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84979-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="84979-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84979-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84979-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84979-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84979-118">See also</span></span>

- [<span data-ttu-id="84979-119">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84979-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="84979-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="84979-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
