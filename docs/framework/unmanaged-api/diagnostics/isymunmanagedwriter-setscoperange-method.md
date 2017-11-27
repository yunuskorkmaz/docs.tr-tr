---
title: "ISymUnmanagedWriter::SetScopeRange Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetScopeRange
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b86df423d53c9fa3a738c603d6cc575add594cae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="f831d-102">ISymUnmanagedWriter::SetScopeRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f831d-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="f831d-103">Belirtilen sözcük kapsamı için uzaklık aralığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f831d-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="f831d-104">Kapsam yeni geçerli kapsam haline gelir ve kapsamları yığına gönderilir.</span><span class="sxs-lookup"><span data-stu-id="f831d-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="f831d-105">Kapsamları bir hiyerarşi oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f831d-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="f831d-106">Eşdüzey çakışma izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="f831d-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f831d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f831d-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f831d-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f831d-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="f831d-109">[in] Kapsam için kapsam tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="f831d-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="f831d-110">[in] Başlangıçtan itibaren sözcük kapsamdaki ilk yönergenin yönteminin bayt uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="f831d-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="f831d-111">[in] Başlangıçtan itibaren sözcük kapsamdaki son yönergenin yönteminin bayt uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="f831d-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f831d-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f831d-112">Return Value</span></span>  
 <span data-ttu-id="f831d-113">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="f831d-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f831d-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f831d-114">Remarks</span></span>  
 <span data-ttu-id="f831d-115">[Isymunmanagedwriter::openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) ile kullanılan donuk kapsam tanımlayıcıyı döndürür `ISymUnmanagedWriter::SetScopeRange` bir kapsamını tanımlamak için başlangıç ve bitiş uzaklığı daha sonra.</span><span class="sxs-lookup"><span data-stu-id="f831d-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="f831d-116">Uzaklık bu durumda, geçirilen `ISymUnmanagedWriter::OpenScope` ve [Isymunmanagedwriter::closescope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="f831d-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="f831d-117">Kapsam yalnızca geçerli yönteminde geçerli tanımlayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="f831d-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f831d-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f831d-118">Requirements</span></span>  
 <span data-ttu-id="f831d-119">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f831d-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f831d-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f831d-120">See Also</span></span>  
 [<span data-ttu-id="f831d-121">Isymunmanagedwriter arabirimi</span><span class="sxs-lookup"><span data-stu-id="f831d-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
