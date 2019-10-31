---
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
ms.openlocfilehash: 5d01ab0b6b5d489b2181056129e22661a50108a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084850"
---
# <a name="icordebugeval2newparameterizedobject-method"></a><span data-ttu-id="f98a0-102">ICorDebugEval2::NewParameterizedObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f98a0-102">ICorDebugEval2::NewParameterizedObject Method</span></span>
<span data-ttu-id="f98a0-103">Yeni parametreli bir tür nesnesi oluşturur ve nesnenin Oluşturucu yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="f98a0-103">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f98a0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f98a0-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f98a0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f98a0-105">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="f98a0-106">'ndaki Örnek oluşturulacak nesnenin oluşturucusunu temsil eden bir ICorDebugFunction nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f98a0-106">[in] A pointer to an ICorDebugFunction object that represents the constructor of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="f98a0-107">'ndaki Geçirilen tür bağımsız değişkenlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="f98a0-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="f98a0-108">'ndaki Her biri, örneklendiği nesnenin tür bağımsız değişkenini temsil eden bir ICorDebugType nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="f98a0-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="f98a0-109">'ndaki Oluşturucuya geçirilen bağımsız değişkenlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="f98a0-109">[in] The number of arguments passed to the constructor.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="f98a0-110">'ndaki Her biri, oluşturucuya geçirilen bir bağımsız değişken değerini temsil eden bir ICorDebugValue nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="f98a0-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents an argument value that is passed to the constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f98a0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f98a0-111">Remarks</span></span>  
 <span data-ttu-id="f98a0-112">Nesnenin Oluşturucusu <xref:System.Type> parametre alabilir.</span><span class="sxs-lookup"><span data-stu-id="f98a0-112">The object's constructor may take <xref:System.Type> parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f98a0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f98a0-113">Requirements</span></span>  
 <span data-ttu-id="f98a0-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f98a0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f98a0-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f98a0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f98a0-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f98a0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f98a0-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f98a0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
