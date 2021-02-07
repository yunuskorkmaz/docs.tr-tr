---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedwriter:: CloseScope yöntemi'
title: ISymUnmanagedWriter::CloseScope Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
ms.openlocfilehash: bb41e69955632d1e4d86250a63a9f25a7d1ae807
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762558"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="c8246-103">ISymUnmanagedWriter::CloseScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c8246-103">ISymUnmanagedWriter::CloseScope Method</span></span>

<span data-ttu-id="c8246-104">Geçerli sözcük temelli kapsamı kapatır.</span><span class="sxs-lookup"><span data-stu-id="c8246-104">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8246-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8246-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8246-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c8246-106">Parameters</span></span>  

 `endOffset`  
 <span data-ttu-id="c8246-107">'ndaki Sözlü kapsamdaki son yönergenin sonundaki noktanın başından itibaren bayt cinsinden olan Aralık.</span><span class="sxs-lookup"><span data-stu-id="c8246-107">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8246-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c8246-108">Return Value</span></span>  

 <span data-ttu-id="c8246-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c8246-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8246-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8246-110">Remarks</span></span>  

 <span data-ttu-id="c8246-111">Bir kapsam kapatıldıktan sonra, içinde daha fazla değişken tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="c8246-111">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="c8246-112">[Ityperunmanagedwriter:: OpenScope](isymunmanagedwriter-openscope-method.md) , daha sonra bir kapsamın başlangıç ve bitiş sapmasını tanımlamak için [ıvmunmanagedwriter:: SetScopeRange](isymunmanagedwriter-setscoperange-method.md) ile kullanılabilecek bir donuk kapsam tanımlayıcısı döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="c8246-112">[ISymUnmanagedWriter::OpenScope](isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="c8246-113">Bu durumda, ve öğesine geçirilen uzaklıklar `ISymUnmanagedWriter::OpenScope` `ISymUnmanagedWriter::CloseScope` yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="c8246-113">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="c8246-114">Kapsam tanımlayıcıları yalnızca geçerli yöntemde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c8246-114">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8246-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8246-115">Requirements</span></span>  

 <span data-ttu-id="c8246-116">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c8246-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8246-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8246-117">See also</span></span>

- [<span data-ttu-id="c8246-118">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8246-118">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
