---
description: 'Daha fazla bilgi edinin: ICorDebugProcess2:: GetDesiredNGENCompilerFlags yöntemi'
title: ICorDebugProcess2::GetDesiredNGENCompilerFlags Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type:
- apiref
ms.openlocfilehash: ddc1c3a958ef42ab51d0ae06fd7ff29b13829c3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650221"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="4ca9e-103">ICorDebugProcess2::GetDesiredNGENCompilerFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="4ca9e-103">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>

<span data-ttu-id="4ca9e-104">Ortak dil çalışma zamanının (CLR) Bu işleme yüklenecek doğru ön derlenmiş (yerel) görüntüyü seçmek için kullandığı geçerli derleyici bayrağı ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="4ca9e-104">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ca9e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ca9e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ca9e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4ca9e-106">Parameters</span></span>  

 `pdwFlags`  
 <span data-ttu-id="4ca9e-107">dışı Yüklenecek doğru önceden derlenmiş görüntüyü seçmek için kullanılan [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırma değerlerinin bit düzeyinde birleşimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4ca9e-107">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ca9e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ca9e-108">Remarks</span></span>  

 <span data-ttu-id="4ca9e-109">CLR 'nin yüklenecek doğru önceden derlenmiş görüntüyü seçerken kullanacağı bayrakları ayarlamak için [ICorDebugProcess2:: SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ca9e-109">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ca9e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ca9e-110">Requirements</span></span>  

 <span data-ttu-id="4ca9e-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ca9e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ca9e-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4ca9e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ca9e-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4ca9e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ca9e-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ca9e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
