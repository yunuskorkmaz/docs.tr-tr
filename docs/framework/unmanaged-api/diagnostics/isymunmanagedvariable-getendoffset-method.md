---
title: ISymUnmanagedVariable::GetEndOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ef32a963b73f2109b9747ef303e8ccd6a729838
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778266"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="ceacf-102">ISymUnmanagedVariable::GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceacf-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="ceacf-103">Bu değişkenin içinde üst bitiş uzaklığı alır.</span><span class="sxs-lookup"><span data-stu-id="ceacf-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="ceacf-104">Bu kapsam içinde yerel bir değişken ise bitiş uzaklığı kapsam için tanımlanan uzaklık içinde kalacak.</span><span class="sxs-lookup"><span data-stu-id="ceacf-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceacf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ceacf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ceacf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ceacf-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="ceacf-107">[out] Bir işaretçi bir `ULONG32` , bitiş uzaklığı alır.</span><span class="sxs-lookup"><span data-stu-id="ceacf-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ceacf-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ceacf-108">Return Value</span></span>  
 <span data-ttu-id="ceacf-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ceacf-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ceacf-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ceacf-110">Requirements</span></span>  
 <span data-ttu-id="ceacf-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ceacf-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceacf-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ceacf-112">See also</span></span>

- [<span data-ttu-id="ceacf-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ceacf-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="ceacf-114">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceacf-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
