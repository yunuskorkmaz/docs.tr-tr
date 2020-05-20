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
ms.openlocfilehash: 4008b2a7d785781da5f35b3dc1e564487cb8e760
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609787"
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="59896-102">ISymUnmanagedWriter::OpenScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59896-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="59896-103">Geçerli yöntemde yeni bir sözlü kapsam açar.</span><span class="sxs-lookup"><span data-stu-id="59896-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="59896-104">Kapsam, yeni geçerli kapsam haline gelir ve bir kapsam yığınına gönderilir.</span><span class="sxs-lookup"><span data-stu-id="59896-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="59896-105">Kapsamlar bir hiyerarşi oluşturmalıdır.</span><span class="sxs-lookup"><span data-stu-id="59896-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="59896-106">Eşdüzey öğelerinin örtüşmesine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="59896-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59896-107">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="59896-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59896-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="59896-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="59896-109">'ndaki Yöntemin başından itibaren bayt cinsinden, sözcük temelli kapsamdaki ilk yönergenin boşluğu.</span><span class="sxs-lookup"><span data-stu-id="59896-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="59896-110">dışı Kapsam tanımlayıcısını alan öğesine yönelik bir işaretçi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="59896-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59896-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="59896-111">Return Value</span></span>  
 <span data-ttu-id="59896-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="59896-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59896-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59896-113">Remarks</span></span>  
 <span data-ttu-id="59896-114">`ISymUnmanagedWriter::OpenScope`bir kapsamın başlangıç ve bitiş sapmasını daha sonra tanımlamak için [ıdimunmanagedwriter:: SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) ile kullanılabilecek bir donuk kapsam tanımlayıcısı döndürür.</span><span class="sxs-lookup"><span data-stu-id="59896-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="59896-115">Bu durumda, `ISymUnmanagedWriter::OpenScope` ve [ıvmunmanagedwriter:: CloseScope](isymunmanagedwriter-closescope-method.md) öğesine geçirilen uzaklıklar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="59896-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="59896-116">Kapsam tanımlayıcıları yalnızca geçerli yöntemde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="59896-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59896-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59896-117">Requirements</span></span>  
 <span data-ttu-id="59896-118">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="59896-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59896-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59896-119">See also</span></span>

- [<span data-ttu-id="59896-120">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="59896-120">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
