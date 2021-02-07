---
description: ': ICorDebugAssembly:: GetName metodu hakkında daha fazla bilgi edinin'
title: ICorDebugAssembly::GetName Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type:
- apiref
ms.openlocfilehash: c2ffa910eaf97c5539a33dbcd3486b7dfb117b51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711992"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="a7344-103">ICorDebugAssembly::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="a7344-103">ICorDebugAssembly::GetName Method</span></span>

<span data-ttu-id="a7344-104">Bu `ICorDebugAssembly` örneğin temsil ettiği derlemenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="a7344-104">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7344-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7344-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7344-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7344-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="a7344-107">'ndaki `szName` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="a7344-107">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a7344-108">dışı Adın gerçek uzunluğunu belirten bir tamsayı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a7344-108">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="a7344-109">dışı Adı depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="a7344-109">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7344-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7344-110">Remarks</span></span>  

 <span data-ttu-id="a7344-111">`GetName`Yöntemi, derlemenin tam yolunu ve dosya adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="a7344-111">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7344-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7344-112">Requirements</span></span>  

 <span data-ttu-id="a7344-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7344-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7344-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a7344-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7344-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a7344-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7344-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7344-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
