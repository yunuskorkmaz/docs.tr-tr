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
ms.openlocfilehash: 325db05cc322d85e836ca9ba62b6a169e8965241
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766369"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="a999b-102">ISymUnmanagedVariable::GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a999b-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="a999b-103">Bu değişkenin içinde üst bitiş uzaklığı alır.</span><span class="sxs-lookup"><span data-stu-id="a999b-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="a999b-104">Bu kapsam içinde yerel bir değişken ise bitiş uzaklığı kapsam için tanımlanan uzaklık içinde kalacak.</span><span class="sxs-lookup"><span data-stu-id="a999b-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a999b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a999b-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a999b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a999b-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a999b-107">[out] Bir işaretçi bir `ULONG32` , bitiş uzaklığı alır.</span><span class="sxs-lookup"><span data-stu-id="a999b-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a999b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a999b-108">Return Value</span></span>  
 <span data-ttu-id="a999b-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a999b-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a999b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a999b-110">Requirements</span></span>  
 <span data-ttu-id="a999b-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a999b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a999b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a999b-112">See also</span></span>

- [<span data-ttu-id="a999b-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a999b-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="a999b-114">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a999b-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
