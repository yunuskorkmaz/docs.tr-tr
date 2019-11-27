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
ms.openlocfilehash: 264b4487483ed5439a9809feefcdc1b20af402dc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428081"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="997e5-102">ISymUnmanagedWriter::CloseScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="997e5-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="997e5-103">Geçerli sözcük temelli kapsamı kapatır.</span><span class="sxs-lookup"><span data-stu-id="997e5-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="997e5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="997e5-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="997e5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="997e5-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="997e5-106">'ndaki Sözlü kapsamdaki son yönergenin sonundaki noktanın başından itibaren bayt cinsinden olan Aralık.</span><span class="sxs-lookup"><span data-stu-id="997e5-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="997e5-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="997e5-107">Return Value</span></span>  
 <span data-ttu-id="997e5-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="997e5-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="997e5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="997e5-109">Remarks</span></span>  
 <span data-ttu-id="997e5-110">Bir kapsam kapatıldıktan sonra, içinde daha fazla değişken tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="997e5-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="997e5-111">[Ityperunmanagedwriter:: OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) , daha sonra bir kapsamın başlangıç ve bitiş sapmasını tanımlamak için [ıvmunmanagedwriter:: SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) ile kullanılabilecek bir donuk kapsam tanımlayıcısı döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="997e5-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="997e5-112">Bu durumda, `ISymUnmanagedWriter::OpenScope` ve `ISymUnmanagedWriter::CloseScope` geçirilen uzaklıklar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="997e5-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="997e5-113">Kapsam tanımlayıcıları yalnızca geçerli yöntemde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="997e5-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="997e5-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="997e5-114">Requirements</span></span>  
 <span data-ttu-id="997e5-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="997e5-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="997e5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="997e5-116">See also</span></span>

- [<span data-ttu-id="997e5-117">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="997e5-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
