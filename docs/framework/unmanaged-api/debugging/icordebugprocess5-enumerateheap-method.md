---
description: ': ICorDebugProcess5:: EnumerateHeap yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b43e7993b114ed64d009f91746ea987198edde74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722041"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="64c7c-103">ICorDebugProcess5::EnumerateHeap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="64c7c-103">ICorDebugProcess5::EnumerateHeap Method</span></span>

<span data-ttu-id="64c7c-104">Yönetilen yığındaki nesneler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="64c7c-104">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64c7c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64c7c-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64c7c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64c7c-106">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="64c7c-107">dışı Yönetilen yığında bulunan nesneler için bir Numaralandırıcı olan [ICorDebugHeapEnum](icordebugheapenum-interface.md) arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="64c7c-107">[out] A pointer to the address of an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64c7c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64c7c-108">Remarks</span></span>  

 <span data-ttu-id="64c7c-109">Yöntemi çağırmadan önce `ICorDebugProcess5::EnumerateHeap` , [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) metodunu çağırmanız ve `areGCStructuresValid` döndürülen [COR_HEAPINFO](cor-heapinfo-structure.md) nesnesinin alanının değerini inceleyerek, atık toplama yığınının geçerli durumunda sıralanabilir olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="64c7c-109">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="64c7c-110">Ayrıca, `ICorDebugProcess5::EnumerateHeap` `E_FAIL` yönetilen yığın için bellekten önce, işlemin kullanım ömrü içinde çok erken bir şekilde iliştirmiş olmanız halinde döndürür.</span><span class="sxs-lookup"><span data-stu-id="64c7c-110">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="64c7c-111">[ICorDebugHeapEnum](icordebugheapenum-interface.md) arabirimi nesnesi, [cor_heapobject](cor-heapobject-structure.md) nesneleri Listeletmanızı sağlayan ıcordebugger genum arabiriminden türetilmiş standart bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="64c7c-111">The [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="64c7c-112">Bu yöntem, [ICorDebugHeapEnum](icordebugheapenum-interface.md) toplama nesnesini tüm nesneler hakkında bilgi sağlayan [cor_heapobject](cor-heapobject-structure.md) örneklerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="64c7c-112">This method populates the [ICorDebugHeapEnum](icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="64c7c-113">Koleksiyon, herhangi bir nesne tarafından kök olmayan ancak henüz atık toplayıcı tarafından toplanmamış nesneler hakkında bilgi sağlayan [cor_heapobject](cor-heapobject-structure.md) örnekleri de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="64c7c-113">The collection may also include [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64c7c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64c7c-114">Requirements</span></span>  

 <span data-ttu-id="64c7c-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64c7c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64c7c-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="64c7c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64c7c-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="64c7c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64c7c-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64c7c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64c7c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64c7c-119">See also</span></span>

- [<span data-ttu-id="64c7c-120">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64c7c-120">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="64c7c-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="64c7c-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
