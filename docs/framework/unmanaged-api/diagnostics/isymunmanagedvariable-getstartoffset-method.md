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
ms.openlocfilehash: c6a30dff869075a201a669d1e703bc003b011fc3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797527"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="ec08a-102">ISymUnmanagedVariable::GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec08a-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="ec08a-103">Bu değişkenin içinde üst başlangıç uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="ec08a-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="ec08a-104">Bu kapsam içinde yerel bir değişken ise, başlangıç uzaklığı kapsam için tanımlanan uzaklık içinde kalacak.</span><span class="sxs-lookup"><span data-stu-id="ec08a-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec08a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec08a-105">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec08a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec08a-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="ec08a-107">[out] Bir işaretçi bir `ULONG32` , başlangıç uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="ec08a-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec08a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ec08a-108">Return Value</span></span>  
 <span data-ttu-id="ec08a-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ec08a-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec08a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec08a-110">Requirements</span></span>  
 <span data-ttu-id="ec08a-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ec08a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec08a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec08a-112">See also</span></span>

- [<span data-ttu-id="ec08a-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec08a-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="ec08a-114">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec08a-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
