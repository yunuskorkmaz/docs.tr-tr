---
title: ICorDebugType2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
ms.openlocfilehash: 0e480db953131d7771e493a8f367154a7d17dada
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396638"
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="db6f2-102">ICorDebugType2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db6f2-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="db6f2-103">Bir temel türün tür tanımlayıcısını veya karmaşık (Kullanıcı tanımlı) türünü almak için ICorDebugType arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="db6f2-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="db6f2-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="db6f2-104">Methods</span></span>  
  
|<span data-ttu-id="db6f2-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="db6f2-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="db6f2-106">GetTypeID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="db6f2-106">GetTypeID Method</span></span>](icordebugtype2-gettypeid-method.md)|<span data-ttu-id="db6f2-107">Bu tür için bir [COR_TYPEID](cor-typeid-structure.md) alır.</span><span class="sxs-lookup"><span data-stu-id="db6f2-107">Gets a [COR_TYPEID](cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db6f2-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db6f2-108">Remarks</span></span>  
 <span data-ttu-id="db6f2-109">Bu arabirim, ICorDebugType arabiriminin mantıksal uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="db6f2-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db6f2-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="db6f2-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db6f2-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="db6f2-111">Example</span></span>  
 <span data-ttu-id="db6f2-112">Aşağıdaki kod parçası, [ICorDebugType2:: GetTypeId](icordebugtype2-gettypeid-method.md) yönteminin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="db6f2-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="db6f2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db6f2-113">Requirements</span></span>  
 <span data-ttu-id="db6f2-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db6f2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db6f2-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="db6f2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db6f2-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="db6f2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db6f2-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db6f2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db6f2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db6f2-118">See also</span></span>

- [<span data-ttu-id="db6f2-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="db6f2-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
