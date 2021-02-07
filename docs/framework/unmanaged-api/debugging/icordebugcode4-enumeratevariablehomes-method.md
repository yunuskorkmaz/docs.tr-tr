---
description: 'Hakkında daha fazla bilgi edinin: ICorDebugCode4:: Enumeratevariableevler yöntemi'
title: 'ICorDebugCode4:: Enumeratevariableevler yöntemi'
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
ms.openlocfilehash: 58f5f9063cd22356efd3a77ece9fb43b6b4c1062
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710965"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="a8e1e-103">ICorDebugCode4:: Enumeratevariableevler yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8e1e-103">ICorDebugCode4::EnumerateVariableHomes Method</span></span>

<span data-ttu-id="a8e1e-104">Bir işlevdeki yerel değişkenlere ve bağımsız değişkenlere bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="a8e1e-104">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8e1e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8e1e-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8e1e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a8e1e-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="a8e1e-107">Bir işlevdeki yerel değişkenler ve bağımsız değişkenler için bir Numaralandırıcı olan [ıcordebugvariablehomeenum](icordebugvariablehomeenum-interface.md) arabirim nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a8e1e-107">A pointer to the address of an [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8e1e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8e1e-108">Remarks</span></span>  

 <span data-ttu-id="a8e1e-109">[Icordebugvariablehomeenum](icordebugvariablehomeenum-interface.md) arabirimi nesnesi, [ıcordebugvariablehome](icordebugvariablehome-interface.md) nesnelerini Listeletmanızı sağlayan "ıcordebugger genum" arabiriminden türetilmiş standart bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="a8e1e-109">The [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="a8e1e-110">Koleksiyonda farklı noktalarda farklı evler varsa, koleksiyonda aynı yuva veya bağımsız değişken dizini için birden çok [ıcordebugvariablehome](icordebugvariablehome-interface.md) nesnesi bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="a8e1e-110">The collection may include multiple [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8e1e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8e1e-111">Requirements</span></span>  

 <span data-ttu-id="a8e1e-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8e1e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8e1e-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a8e1e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8e1e-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a8e1e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8e1e-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8e1e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8e1e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8e1e-116">See also</span></span>

- [<span data-ttu-id="a8e1e-117">ICorDebugCode4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a8e1e-117">ICorDebugCode4 Interface</span></span>](icordebugcode4-interface.md)
- [<span data-ttu-id="a8e1e-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a8e1e-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
