---
title: "ISymUnmanagedWriter::OpenScope Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedWriter.OpenScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 99919a1d932bca1bb8677fd71c447c7098c7d44c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="8dd78-102">ISymUnmanagedWriter::OpenScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8dd78-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="8dd78-103">Yeni bir sözcük kapsamı geçerli yönteminde açar.</span><span class="sxs-lookup"><span data-stu-id="8dd78-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="8dd78-104">Kapsam yeni geçerli kapsam haline gelir ve kapsamları yığına gönderilir.</span><span class="sxs-lookup"><span data-stu-id="8dd78-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="8dd78-105">Kapsamları bir hiyerarşi oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8dd78-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="8dd78-106">Eşdüzey çakışma izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="8dd78-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dd78-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8dd78-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8dd78-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8dd78-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="8dd78-109">[in] İlk yönerge sözcük kapsamda yöntemi başından itibaren bayt uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="8dd78-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="8dd78-110">[out] Bir işaretçi bir `ULONG32` kapsam tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="8dd78-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8dd78-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8dd78-111">Return Value</span></span>  
 <span data-ttu-id="8dd78-112">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="8dd78-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8dd78-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8dd78-113">Remarks</span></span>  
 <span data-ttu-id="8dd78-114">`ISymUnmanagedWriter::OpenScope`ile birlikte kullanılabilir donuk kapsam tanımlayıcıyı döndürür [Isymunmanagedwriter::setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) bir kapsamını tanımlamak için başlangıç ve bitiş uzaklığı daha sonra.</span><span class="sxs-lookup"><span data-stu-id="8dd78-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="8dd78-115">Uzaklık bu durumda, geçirilen `ISymUnmanagedWriter::OpenScope` ve [Isymunmanagedwriter::closescope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="8dd78-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="8dd78-116">Kapsam tanımlayıcıları yalnızca geçerli yöntemi geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="8dd78-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dd78-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8dd78-117">Requirements</span></span>  
 <span data-ttu-id="8dd78-118">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8dd78-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dd78-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8dd78-119">See Also</span></span>  
 [<span data-ttu-id="8dd78-120">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8dd78-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
