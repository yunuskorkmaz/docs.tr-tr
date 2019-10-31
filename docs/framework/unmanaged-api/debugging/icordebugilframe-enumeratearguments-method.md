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
ms.openlocfilehash: d74c5a6f966201c8ca9d2854de2e9986e7f1d0fa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131035"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="4bca8-102">ICorDebugILFrame::EnumerateArguments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4bca8-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="4bca8-103">Bu çerçevedeki bağımsız değişkenler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="4bca8-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bca8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4bca8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bca8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4bca8-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="4bca8-106">dışı Bu çerçevedeki bağımsız değişkenlerin numaralandırıcısının bulunduğu ICorDebugValueEnum nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4bca8-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bca8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4bca8-107">Remarks</span></span>  
 <span data-ttu-id="4bca8-108">`EnumerateArguments`, bu ICorDebugILFrame nesnesi tarafından temsil edilen çağrı çerçevesinde kullanılabilir olan bağımsız değişkenleri listeleyerek bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="4bca8-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="4bca8-109">Listede, [vararg](/cpp/windows/vararg) olan bağımsız değişkenler (yani, değişken sayıda bağımsız değişken), `vararg`olmayan bağımsız değişkenler de bulunur.</span><span class="sxs-lookup"><span data-stu-id="4bca8-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bca8-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4bca8-110">Requirements</span></span>  
 <span data-ttu-id="4bca8-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bca8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bca8-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4bca8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4bca8-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4bca8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4bca8-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bca8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
