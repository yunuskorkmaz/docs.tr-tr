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
ms.openlocfilehash: fa6d563873045b4b5b427f06f0caa5420d31590b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777212"
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="06d37-102">ISymUnmanagedWriter::OpenScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="06d37-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="06d37-103">Yeni bir sözcük kapsamı geçerli yöntemde açılır.</span><span class="sxs-lookup"><span data-stu-id="06d37-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="06d37-104">Kapsam, yeni geçerli kapsam haline gelir ve kapsamlarının bir yığın itilir.</span><span class="sxs-lookup"><span data-stu-id="06d37-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="06d37-105">Kapsamları bir hiyerarşi oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="06d37-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="06d37-106">Eşdüzey çakıştırmayı izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="06d37-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06d37-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06d37-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06d37-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06d37-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="06d37-109">[in] İlk yönerge sözlü kapsamda yöntemi başından itibaren bayt cinsinden uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="06d37-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="06d37-110">[out] Bir işaretçi bir `ULONG32` , kapsam tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="06d37-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06d37-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="06d37-111">Return Value</span></span>  
 <span data-ttu-id="06d37-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="06d37-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06d37-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06d37-113">Remarks</span></span>  
 <span data-ttu-id="06d37-114">`ISymUnmanagedWriter::OpenScope` ile kullanılabilen donuk kapsam tanımlayıcıyı döndürür [Isymunmanagedwriter::setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) bir kapsamı tanımlamak için başlangıç ve bitiş uzaklığı daha sonra.</span><span class="sxs-lookup"><span data-stu-id="06d37-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="06d37-115">Uzaklık bu durumda, geçirilen `ISymUnmanagedWriter::OpenScope` ve [Isymunmanagedwriter::closescope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="06d37-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="06d37-116">Kapsam tanımlayıcılar yalnızca geçerli yöntemi içinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="06d37-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06d37-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06d37-117">Requirements</span></span>  
 <span data-ttu-id="06d37-118">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="06d37-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06d37-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06d37-119">See also</span></span>

- [<span data-ttu-id="06d37-120">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06d37-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
