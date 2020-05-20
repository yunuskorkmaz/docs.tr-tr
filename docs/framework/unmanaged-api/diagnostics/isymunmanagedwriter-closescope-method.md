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
ms.openlocfilehash: 4d8790dc68bc063deed4c58ba0df8e9ea258b9d7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610086"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="b30ab-102">ISymUnmanagedWriter::CloseScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b30ab-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="b30ab-103">Geçerli sözcük temelli kapsamı kapatır.</span><span class="sxs-lookup"><span data-stu-id="b30ab-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b30ab-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b30ab-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b30ab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b30ab-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="b30ab-106">'ndaki Sözlü kapsamdaki son yönergenin sonundaki noktanın başından itibaren bayt cinsinden olan Aralık.</span><span class="sxs-lookup"><span data-stu-id="b30ab-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b30ab-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b30ab-107">Return Value</span></span>  
 <span data-ttu-id="b30ab-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="b30ab-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b30ab-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b30ab-109">Remarks</span></span>  
 <span data-ttu-id="b30ab-110">Bir kapsam kapatıldıktan sonra, içinde daha fazla değişken tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="b30ab-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="b30ab-111">[Ityperunmanagedwriter:: OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) , daha sonra bir kapsamın başlangıç ve bitiş sapmasını tanımlamak için [ıvmunmanagedwriter:: SetScopeRange](isymunmanagedwriter-setscoperange-method.md) ile kullanılabilecek bir donuk kapsam tanımlayıcısı döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="b30ab-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="b30ab-112">Bu durumda, ve öğesine geçirilen uzaklıklar `ISymUnmanagedWriter::OpenScope` `ISymUnmanagedWriter::CloseScope` yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="b30ab-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="b30ab-113">Kapsam tanımlayıcıları yalnızca geçerli yöntemde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b30ab-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b30ab-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b30ab-114">Requirements</span></span>  
 <span data-ttu-id="b30ab-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b30ab-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b30ab-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b30ab-116">See also</span></span>

- [<span data-ttu-id="b30ab-117">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b30ab-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
