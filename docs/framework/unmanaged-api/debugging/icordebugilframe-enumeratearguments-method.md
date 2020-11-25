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
ms.openlocfilehash: 9b0bc59b67b5d4b2184733f22616433bf33be616
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703232"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="5e1b0-102">ICorDebugILFrame::EnumerateArguments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e1b0-102">ICorDebugILFrame::EnumerateArguments Method</span></span>

<span data-ttu-id="5e1b0-103">Bu çerçevedeki bağımsız değişkenler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="5e1b0-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e1b0-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5e1b0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e1b0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5e1b0-105">Parameters</span></span>  

 `ppValueEnum`  
 <span data-ttu-id="5e1b0-106">dışı Bu çerçevedeki bağımsız değişkenlerin numaralandırıcısının bulunduğu ICorDebugValueEnum nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5e1b0-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e1b0-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e1b0-107">Remarks</span></span>  

 <span data-ttu-id="5e1b0-108">`EnumerateArguments` Bu ICorDebugILFrame nesnesi tarafından temsil edilen çağrı çerçevesinde kullanılabilir olan bağımsız değişkenleri listeleyerek bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="5e1b0-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="5e1b0-109">Listede, [vararg](/cpp/windows/vararg) olan bağımsız değişkenler (yani, değişken sayıda bağımsız değişken) ve olmayan bağımsız değişkenler yer alır `vararg` .</span><span class="sxs-lookup"><span data-stu-id="5e1b0-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e1b0-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e1b0-110">Requirements</span></span>  

 <span data-ttu-id="5e1b0-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e1b0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e1b0-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5e1b0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e1b0-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5e1b0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e1b0-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e1b0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
