---
description: 'Daha fazla bilgi edinin: ICorDebugEval2:: NewParameterizedObject yöntemi'
title: ICorDebugEval2::NewParameterizedObject Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type:
- apiref
ms.openlocfilehash: 2dc746fdada0e79044a1387bd4cb1c11b81d7777
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693687"
---
# <a name="icordebugeval2newparameterizedobject-method"></a><span data-ttu-id="8e9af-103">ICorDebugEval2::NewParameterizedObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8e9af-103">ICorDebugEval2::NewParameterizedObject Method</span></span>

<span data-ttu-id="8e9af-104">Yeni parametreli bir tür nesnesi oluşturur ve nesnenin Oluşturucu yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="8e9af-104">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e9af-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e9af-105">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e9af-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8e9af-106">Parameters</span></span>  

 `pConstructor`  
 <span data-ttu-id="8e9af-107">'ndaki Örnek oluşturulacak nesnenin oluşturucusunu temsil eden bir ICorDebugFunction nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8e9af-107">[in] A pointer to an ICorDebugFunction object that represents the constructor of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="8e9af-108">'ndaki Geçirilen tür bağımsız değişkenlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="8e9af-108">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="8e9af-109">'ndaki Her biri, örneklendiği nesnenin tür bağımsız değişkenini temsil eden bir ICorDebugType nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="8e9af-109">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="8e9af-110">'ndaki Oluşturucuya geçirilen bağımsız değişkenlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="8e9af-110">[in] The number of arguments passed to the constructor.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="8e9af-111">'ndaki Her biri, oluşturucuya geçirilen bir bağımsız değişken değerini temsil eden bir ICorDebugValue nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="8e9af-111">[in] An array of pointers, each of which points to an ICorDebugValue object that represents an argument value that is passed to the constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e9af-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e9af-112">Remarks</span></span>  

 <span data-ttu-id="8e9af-113">Nesnenin oluşturucusu <xref:System.Type> parametre alabilir.</span><span class="sxs-lookup"><span data-stu-id="8e9af-113">The object's constructor may take <xref:System.Type> parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e9af-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e9af-114">Requirements</span></span>  

 <span data-ttu-id="8e9af-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e9af-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e9af-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8e9af-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e9af-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8e9af-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e9af-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e9af-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
