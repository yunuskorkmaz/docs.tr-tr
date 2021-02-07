---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedwriter:: OpenScope Yöntemi'
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
ms.openlocfilehash: 1e47d97941b053fedcf08c7582e1083988a9fed4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762116"
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="6a74f-103">ISymUnmanagedWriter::OpenScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a74f-103">ISymUnmanagedWriter::OpenScope Method</span></span>

<span data-ttu-id="6a74f-104">Geçerli yöntemde yeni bir sözlü kapsam açar.</span><span class="sxs-lookup"><span data-stu-id="6a74f-104">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="6a74f-105">Kapsam, yeni geçerli kapsam haline gelir ve bir kapsam yığınına gönderilir.</span><span class="sxs-lookup"><span data-stu-id="6a74f-105">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="6a74f-106">Kapsamlar bir hiyerarşi oluşturmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a74f-106">Scopes must form a hierarchy.</span></span> <span data-ttu-id="6a74f-107">Eşdüzey öğelerinin örtüşmesine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="6a74f-107">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a74f-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a74f-108">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a74f-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a74f-109">Parameters</span></span>  

 `startOffset`  
 <span data-ttu-id="6a74f-110">'ndaki Yöntemin başından itibaren bayt cinsinden, sözcük temelli kapsamdaki ilk yönergenin boşluğu.</span><span class="sxs-lookup"><span data-stu-id="6a74f-110">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="6a74f-111">dışı Kapsam tanımlayıcısını alan öğesine yönelik bir işaretçi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="6a74f-111">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a74f-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6a74f-112">Return Value</span></span>  

 <span data-ttu-id="6a74f-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6a74f-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a74f-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a74f-114">Remarks</span></span>  

 <span data-ttu-id="6a74f-115">`ISymUnmanagedWriter::OpenScope` bir kapsamın başlangıç ve bitiş sapmasını daha sonra tanımlamak için [ıdimunmanagedwriter:: SetScopeRange](isymunmanagedwriter-setscoperange-method.md) ile kullanılabilecek bir donuk kapsam tanımlayıcısı döndürür.</span><span class="sxs-lookup"><span data-stu-id="6a74f-115">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="6a74f-116">Bu durumda, `ISymUnmanagedWriter::OpenScope` ve [ıvmunmanagedwriter:: CloseScope](isymunmanagedwriter-closescope-method.md) öğesine geçirilen uzaklıklar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="6a74f-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="6a74f-117">Kapsam tanımlayıcıları yalnızca geçerli yöntemde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6a74f-117">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a74f-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a74f-118">Requirements</span></span>  

 <span data-ttu-id="6a74f-119">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6a74f-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a74f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a74f-120">See also</span></span>

- [<span data-ttu-id="6a74f-121">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a74f-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
