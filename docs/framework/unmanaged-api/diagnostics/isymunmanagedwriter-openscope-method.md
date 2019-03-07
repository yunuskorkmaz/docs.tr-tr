---
title: ISymUnmanagedWriter::OpenScope Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ccaaee614b1ec4d03271e70338fff82d629a7c28
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468478"
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="7ab6a-102">ISymUnmanagedWriter::OpenScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ab6a-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="7ab6a-103">Yeni bir sözcük kapsamı geçerli yöntemde açılır.</span><span class="sxs-lookup"><span data-stu-id="7ab6a-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="7ab6a-104">Kapsam, yeni geçerli kapsam haline gelir ve kapsamlarının bir yığın itilir.</span><span class="sxs-lookup"><span data-stu-id="7ab6a-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="7ab6a-105">Kapsamları bir hiyerarşi oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ab6a-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="7ab6a-106">Eşdüzey çakıştırmayı izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="7ab6a-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ab6a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ab6a-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ab6a-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7ab6a-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="7ab6a-109">[in] İlk yönerge sözlü kapsamda yöntemi başından itibaren bayt cinsinden uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="7ab6a-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="7ab6a-110">[out] Bir işaretçi bir `ULONG32` , kapsam tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="7ab6a-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ab6a-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7ab6a-111">Return Value</span></span>  
 <span data-ttu-id="7ab6a-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="7ab6a-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ab6a-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ab6a-113">Remarks</span></span>  
 <span data-ttu-id="7ab6a-114">`ISymUnmanagedWriter::OpenScope` ile kullanılabilen donuk kapsam tanımlayıcıyı döndürür [Isymunmanagedwriter::setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) bir kapsamı tanımlamak için başlangıç ve bitiş uzaklığı daha sonra.</span><span class="sxs-lookup"><span data-stu-id="7ab6a-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="7ab6a-115">Uzaklık bu durumda, geçirilen `ISymUnmanagedWriter::OpenScope` ve [Isymunmanagedwriter::closescope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="7ab6a-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="7ab6a-116">Kapsam tanımlayıcılar yalnızca geçerli yöntemi içinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7ab6a-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ab6a-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ab6a-117">Requirements</span></span>  
 <span data-ttu-id="7ab6a-118">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7ab6a-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ab6a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ab6a-119">See also</span></span>
- [<span data-ttu-id="7ab6a-120">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ab6a-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
