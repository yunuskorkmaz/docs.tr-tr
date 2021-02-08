---
description: ': ICorDebugILFrame:: EnumerateArguments Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 513f931e70a4e914b89f440545cf33ea1cce1fdf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791406"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="ae565-103">ICorDebugILFrame::EnumerateArguments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae565-103">ICorDebugILFrame::EnumerateArguments Method</span></span>

<span data-ttu-id="ae565-104">Bu çerçevedeki bağımsız değişkenler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="ae565-104">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae565-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae565-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae565-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae565-106">Parameters</span></span>  

 `ppValueEnum`  
 <span data-ttu-id="ae565-107">dışı Bu çerçevedeki bağımsız değişkenlerin numaralandırıcısının bulunduğu ICorDebugValueEnum nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ae565-107">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae565-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae565-108">Remarks</span></span>  

 <span data-ttu-id="ae565-109">`EnumerateArguments` Bu ICorDebugILFrame nesnesi tarafından temsil edilen çağrı çerçevesinde kullanılabilir olan bağımsız değişkenleri listeleyerek bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="ae565-109">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="ae565-110">Listede, [vararg](/cpp/windows/vararg) olan bağımsız değişkenler (yani, değişken sayıda bağımsız değişken) ve olmayan bağımsız değişkenler yer alır `vararg` .</span><span class="sxs-lookup"><span data-stu-id="ae565-110">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae565-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae565-111">Requirements</span></span>  

 <span data-ttu-id="ae565-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae565-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae565-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ae565-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae565-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ae565-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae565-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae565-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
