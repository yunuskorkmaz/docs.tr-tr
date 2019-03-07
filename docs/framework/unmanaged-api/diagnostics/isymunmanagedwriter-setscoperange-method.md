---
title: ISymUnmanagedWriter::SetScopeRange Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetScopeRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3657ef40fce3d9d29e0cf6c27e8eb527be0f150e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489026"
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="594b6-102">ISymUnmanagedWriter::SetScopeRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="594b6-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="594b6-103">Sözcük Belirtilen kapsam için uzaklık aralığı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="594b6-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="594b6-104">Kapsam, yeni geçerli kapsam haline gelir ve kapsamlarının bir yığın itilir.</span><span class="sxs-lookup"><span data-stu-id="594b6-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="594b6-105">Kapsamları bir hiyerarşi oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="594b6-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="594b6-106">Eşdüzey çakıştırmayı izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="594b6-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="594b6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="594b6-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="594b6-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="594b6-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="594b6-109">[in] Kapsam için kapsam tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="594b6-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="594b6-110">[in] Yöntemin ilk yönergesinin baştan sözlü kapsamda bayt cinsinden uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="594b6-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="594b6-111">[in] Başlangıçtan itibaren sözlü kapsamda son yönergenin yönteminin bayt cinsinden uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="594b6-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="594b6-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="594b6-112">Return Value</span></span>  
 <span data-ttu-id="594b6-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="594b6-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="594b6-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="594b6-114">Remarks</span></span>  
 <span data-ttu-id="594b6-115">[Isymunmanagedwriter::openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) ile kullanılabilecek donuk kapsam tanımlayıcıyı döndürür `ISymUnmanagedWriter::SetScopeRange` bir kapsamı tanımlamak için başlangıç ve bitiş uzaklığı daha sonra.</span><span class="sxs-lookup"><span data-stu-id="594b6-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="594b6-116">Uzaklık bu durumda, geçirilen `ISymUnmanagedWriter::OpenScope` ve [Isymunmanagedwriter::closescope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="594b6-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="594b6-117">Kapsam tanımlayıcıları, yalnızca geçerli yöntemde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="594b6-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="594b6-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="594b6-118">Requirements</span></span>  
 <span data-ttu-id="594b6-119">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="594b6-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="594b6-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="594b6-120">See also</span></span>
- [<span data-ttu-id="594b6-121">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="594b6-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
