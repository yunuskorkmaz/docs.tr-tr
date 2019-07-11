---
title: ISymUnmanagedVariable::GetStartOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3dbe5b4e57f21970b518e4974707175f4bdcf02a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778223"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="f2611-102">ISymUnmanagedVariable::GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2611-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="f2611-103">Bu değişkenin içinde üst başlangıç uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="f2611-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="f2611-104">Bu kapsam içinde yerel bir değişken ise, başlangıç uzaklığı kapsam için tanımlanan uzaklık içinde kalacak.</span><span class="sxs-lookup"><span data-stu-id="f2611-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2611-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2611-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2611-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2611-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="f2611-107">[out] Bir işaretçi bir `ULONG32` , başlangıç uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="f2611-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2611-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f2611-108">Return Value</span></span>  
 <span data-ttu-id="f2611-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="f2611-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2611-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2611-110">Requirements</span></span>  
 <span data-ttu-id="f2611-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f2611-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2611-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2611-112">See also</span></span>

- [<span data-ttu-id="f2611-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2611-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="f2611-114">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2611-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
