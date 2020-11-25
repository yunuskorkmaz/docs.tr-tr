---
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
ms.openlocfilehash: 561a6348b9976789b02961fadb37d9127f5a6a13
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713047"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="2a285-102">ISymUnmanagedWriter::CloseScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a285-102">ISymUnmanagedWriter::CloseScope Method</span></span>

<span data-ttu-id="2a285-103">Geçerli sözcük temelli kapsamı kapatır.</span><span class="sxs-lookup"><span data-stu-id="2a285-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a285-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2a285-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a285-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a285-105">Parameters</span></span>  

 `endOffset`  
 <span data-ttu-id="2a285-106">'ndaki Sözlü kapsamdaki son yönergenin sonundaki noktanın başından itibaren bayt cinsinden olan Aralık.</span><span class="sxs-lookup"><span data-stu-id="2a285-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a285-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2a285-107">Return Value</span></span>  

 <span data-ttu-id="2a285-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2a285-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a285-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a285-109">Remarks</span></span>  

 <span data-ttu-id="2a285-110">Bir kapsam kapatıldıktan sonra, içinde daha fazla değişken tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="2a285-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="2a285-111">[Ityperunmanagedwriter:: OpenScope](isymunmanagedwriter-openscope-method.md) , daha sonra bir kapsamın başlangıç ve bitiş sapmasını tanımlamak için [ıvmunmanagedwriter:: SetScopeRange](isymunmanagedwriter-setscoperange-method.md) ile kullanılabilecek bir donuk kapsam tanımlayıcısı döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="2a285-111">[ISymUnmanagedWriter::OpenScope](isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="2a285-112">Bu durumda, ve öğesine geçirilen uzaklıklar `ISymUnmanagedWriter::OpenScope` `ISymUnmanagedWriter::CloseScope` yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="2a285-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="2a285-113">Kapsam tanımlayıcıları yalnızca geçerli yöntemde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2a285-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a285-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a285-114">Requirements</span></span>  

 <span data-ttu-id="2a285-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2a285-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a285-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a285-116">See also</span></span>

- [<span data-ttu-id="2a285-117">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a285-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
