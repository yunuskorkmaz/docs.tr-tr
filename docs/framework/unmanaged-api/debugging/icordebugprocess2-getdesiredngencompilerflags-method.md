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
ms.openlocfilehash: 015735e1c6c3b6c146f2fca3a9bdc28baeca2f92
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792516"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="f4aaa-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="f4aaa-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="f4aaa-103">Ortak dil çalışma zamanının (CLR) Bu işleme yüklenecek doğru ön derlenmiş (yerel) görüntüyü seçmek için kullandığı geçerli derleyici bayrağı ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="f4aaa-103">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4aaa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4aaa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4aaa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f4aaa-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="f4aaa-106">dışı Yüklenecek doğru önceden derlenmiş görüntüyü seçmek için kullanılan [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırma değerlerinin bit düzeyinde birleşimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f4aaa-106">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4aaa-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4aaa-107">Remarks</span></span>  
 <span data-ttu-id="f4aaa-108">CLR 'nin yüklenecek doğru önceden derlenmiş görüntüyü seçerken kullanacağı bayrakları ayarlamak için [ICorDebugProcess2:: SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4aaa-108">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4aaa-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4aaa-109">Requirements</span></span>  
 <span data-ttu-id="f4aaa-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4aaa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4aaa-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f4aaa-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4aaa-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f4aaa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4aaa-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4aaa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
