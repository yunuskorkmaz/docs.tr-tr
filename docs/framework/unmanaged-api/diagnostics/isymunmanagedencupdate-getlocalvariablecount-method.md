---
title: ISymUnmanagedENCUpdate::GetLocalVariableCount Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d56785815105e2f4b06217d3375e2d1cfdf0494c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776916"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="cc16c-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc16c-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="cc16c-103">Yerel değişken sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="cc16c-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc16c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc16c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc16c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cc16c-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="cc16c-106">[in] Meta veri belirteci yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="cc16c-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="cc16c-107">[out] Bir işaretçi bir `ULONG32` karakter yerel değişken sayısını içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="cc16c-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc16c-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cc16c-108">Return Value</span></span>  
 <span data-ttu-id="cc16c-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="cc16c-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc16c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc16c-110">Requirements</span></span>  
 <span data-ttu-id="cc16c-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cc16c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc16c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc16c-112">See also</span></span>

- [<span data-ttu-id="cc16c-113">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc16c-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
