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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220961"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="88c98-102">ISymUnmanagedVariable::GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="88c98-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="88c98-103">Bu değişkenin içinde üst bitiş uzaklığı alır.</span><span class="sxs-lookup"><span data-stu-id="88c98-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="88c98-104">Bu kapsam içinde yerel bir değişken ise bitiş uzaklığı kapsam için tanımlanan uzaklık içinde kalacak.</span><span class="sxs-lookup"><span data-stu-id="88c98-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88c98-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88c98-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88c98-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="88c98-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="88c98-107">[out] Bir işaretçi bir `ULONG32` , bitiş uzaklığı alır.</span><span class="sxs-lookup"><span data-stu-id="88c98-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88c98-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="88c98-108">Return Value</span></span>  
 <span data-ttu-id="88c98-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="88c98-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88c98-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88c98-110">Requirements</span></span>  
 <span data-ttu-id="88c98-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="88c98-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88c98-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88c98-112">See also</span></span>

- [<span data-ttu-id="88c98-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="88c98-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="88c98-114">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="88c98-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
