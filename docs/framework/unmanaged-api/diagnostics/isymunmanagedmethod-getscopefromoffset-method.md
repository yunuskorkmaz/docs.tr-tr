---
title: ISymUnmanagedMethod::GetScopeFromOffset Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetScopeFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0898d554a2602a1139f2e37eb67f3aa00c5bd79e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436091"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="cbb81-102">ISymUnmanagedMethod::GetScopeFromOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="cbb81-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="cbb81-103">Belirtilen uzaklık kapsayan bu yöntem en kapsayan sözcük kapsamında alır.</span><span class="sxs-lookup"><span data-stu-id="cbb81-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="cbb81-104">Bu yerel değişken aramaları başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cbb81-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbb81-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cbb81-105">Syntax</span></span>  
  
```  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cbb81-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cbb81-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="cbb81-107">[in] A `ULONG` uzaklık içerir.</span><span class="sxs-lookup"><span data-stu-id="cbb81-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="cbb81-108">[out] Ayarlanmış bir işaretçi döndürülen için [Isymunmanagedscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="cbb81-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbb81-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cbb81-109">Return Value</span></span>  
 <span data-ttu-id="cbb81-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="cbb81-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbb81-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cbb81-111">Requirements</span></span>  
 <span data-ttu-id="cbb81-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cbb81-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb81-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cbb81-113">See Also</span></span>  
 [<span data-ttu-id="cbb81-114">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbb81-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
