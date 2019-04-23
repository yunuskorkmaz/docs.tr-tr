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
ms.openlocfilehash: e0e859ba8b6ec247073b0b69b035ea4cf074ab05
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149298"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="92006-102">ISymUnmanagedMethod::GetScopeFromOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="92006-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="92006-103">Belirtilen uzaklık kapsayan bu yöntem en kapsayan sözlü kapsamda alır.</span><span class="sxs-lookup"><span data-stu-id="92006-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="92006-104">Bu yerel değişken aramaları başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="92006-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92006-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92006-105">Syntax</span></span>  
  
```  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92006-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92006-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="92006-107">[in] A `ULONG` içeren uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="92006-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="92006-108">[out] Ayarlanmış bir işaretçi ve döndürülen [Isymunmanagedscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="92006-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92006-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="92006-109">Return Value</span></span>  
 <span data-ttu-id="92006-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="92006-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92006-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92006-111">Requirements</span></span>  
 <span data-ttu-id="92006-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="92006-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92006-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92006-113">See also</span></span>

- [<span data-ttu-id="92006-114">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92006-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
