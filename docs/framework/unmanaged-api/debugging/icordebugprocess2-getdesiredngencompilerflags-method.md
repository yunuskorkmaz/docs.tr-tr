---
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
ms.openlocfilehash: 223f66639ae24f2a54f1bc936f4a0765573356eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673923"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="f0303-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="f0303-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>

<span data-ttu-id="f0303-103">Ortak dil çalışma zamanının (CLR) Bu işleme yüklenecek doğru ön derlenmiş (yerel) görüntüyü seçmek için kullandığı geçerli derleyici bayrağı ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="f0303-103">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0303-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f0303-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0303-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0303-105">Parameters</span></span>  

 `pdwFlags`  
 <span data-ttu-id="f0303-106">dışı Yüklenecek doğru önceden derlenmiş görüntüyü seçmek için kullanılan [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırma değerlerinin bit düzeyinde birleşimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f0303-106">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0303-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0303-107">Remarks</span></span>  

 <span data-ttu-id="f0303-108">CLR 'nin yüklenecek doğru önceden derlenmiş görüntüyü seçerken kullanacağı bayrakları ayarlamak için [ICorDebugProcess2:: SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0303-108">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0303-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0303-109">Requirements</span></span>  

 <span data-ttu-id="f0303-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0303-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0303-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f0303-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0303-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f0303-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0303-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0303-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
