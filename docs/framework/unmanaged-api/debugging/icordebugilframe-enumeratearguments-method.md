---
title: ICorDebugILFrame::EnumerateArguments Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateArguments
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type:
- apiref
ms.openlocfilehash: 3945b1dea62dc0616d669356faf60f0d09cfb084
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210312"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="d5698-102">ICorDebugILFrame::EnumerateArguments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5698-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="d5698-103">Bu çerçevedeki bağımsız değişkenler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="d5698-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5698-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5698-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5698-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5698-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="d5698-106">dışı Bu çerçevedeki bağımsız değişkenlerin numaralandırıcısının bulunduğu ICorDebugValueEnum nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d5698-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5698-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5698-107">Remarks</span></span>  
 <span data-ttu-id="d5698-108">`EnumerateArguments`Bu ICorDebugILFrame nesnesi tarafından temsil edilen çağrı çerçevesinde kullanılabilir olan bağımsız değişkenleri listeleyerek bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="d5698-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="d5698-109">Listede, [vararg](/cpp/windows/vararg) olan bağımsız değişkenler (yani, değişken sayıda bağımsız değişken) ve olmayan bağımsız değişkenler yer alır `vararg` .</span><span class="sxs-lookup"><span data-stu-id="d5698-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5698-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5698-110">Requirements</span></span>  
 <span data-ttu-id="d5698-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5698-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5698-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d5698-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5698-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d5698-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5698-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5698-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
