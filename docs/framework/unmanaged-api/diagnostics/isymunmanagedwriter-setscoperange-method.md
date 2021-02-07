---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedwriter:: SetScopeRange Yöntemi'
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
ms.openlocfilehash: 43cfbeaa0d366b9f2d25068cfa7b91a0fea8ac59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762064"
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="a9499-103">ISymUnmanagedWriter::SetScopeRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9499-103">ISymUnmanagedWriter::SetScopeRange Method</span></span>

<span data-ttu-id="a9499-104">Belirtilen sözcük temelli kapsamın fark aralığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a9499-104">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="a9499-105">Kapsam, yeni geçerli kapsam haline gelir ve bir kapsam yığınına gönderilir.</span><span class="sxs-lookup"><span data-stu-id="a9499-105">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="a9499-106">Kapsamlar bir hiyerarşi oluşturmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a9499-106">Scopes must form a hierarchy.</span></span> <span data-ttu-id="a9499-107">Eşdüzey öğelerinin örtüşmesine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="a9499-107">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9499-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9499-108">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9499-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9499-109">Parameters</span></span>  

 `scopeId`  
 <span data-ttu-id="a9499-110">'ndaki Kapsamın kapsam tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a9499-110">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="a9499-111">'ndaki Metodun başındaki sözcük temelli kapsamdaki ilk yönergenin bayt cinsinden değeri.</span><span class="sxs-lookup"><span data-stu-id="a9499-111">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="a9499-112">'ndaki Metodun başındaki sözcük temelli kapsamdaki son yönergenin bayt cinsinden değeri.</span><span class="sxs-lookup"><span data-stu-id="a9499-112">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9499-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a9499-113">Return Value</span></span>  

 <span data-ttu-id="a9499-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a9499-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9499-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9499-115">Remarks</span></span>  

 <span data-ttu-id="a9499-116">[Ivmunmanagedwriter:: OpenScope](isymunmanagedwriter-openscope-method.md) , bir `ISymUnmanagedWriter::SetScopeRange` kapsamın başlangıç ve bitiş sapmasını daha sonra tanımlamak için ile birlikte kullanılabilecek bir donuk kapsam tanımlayıcısı döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="a9499-116">[ISymUnmanagedWriter::OpenScope](isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="a9499-117">Bu durumda, `ISymUnmanagedWriter::OpenScope` ve [ıvmunmanagedwriter:: CloseScope](isymunmanagedwriter-closescope-method.md) öğesine geçirilen uzaklıklar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="a9499-117">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="a9499-118">Kapsam tanımlayıcıları yalnızca geçerli yöntemde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a9499-118">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9499-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9499-119">Requirements</span></span>  

 <span data-ttu-id="a9499-120">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a9499-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9499-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9499-121">See also</span></span>

- [<span data-ttu-id="a9499-122">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9499-122">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
