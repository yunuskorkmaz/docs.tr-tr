---
title: ISymUnmanagedWriter::SetMethodSourceRange Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetMethodSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type:
- apiref
ms.openlocfilehash: 85e65f6a3ec13c2acc31b8f87dbe4b4476ffc2a5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427870"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="01e3c-102">ISymUnmanagedWriter::SetMethodSourceRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01e3c-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="01e3c-103">Kaynak dosya içindeki bir yöntemin doğru başlangıcını ve sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="01e3c-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="01e3c-104">Yöntemin içinde var olan sıra noktalarından bağımsız olarak bir yöntemin kapsamını belirtmek için bu yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="01e3c-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01e3c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01e3c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01e3c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="01e3c-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="01e3c-107">'ndaki Başlangıç konumunu içeren belgeye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="01e3c-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="01e3c-108">'ndaki Başlangıç satır numarası.</span><span class="sxs-lookup"><span data-stu-id="01e3c-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="01e3c-109">'ndaki Başlangıç sütunu.</span><span class="sxs-lookup"><span data-stu-id="01e3c-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="01e3c-110">'ndaki Bitiş konumunu içeren belgeye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="01e3c-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="01e3c-111">'ndaki Son satır numarası.</span><span class="sxs-lookup"><span data-stu-id="01e3c-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="01e3c-112">'ndaki Bitiş sütun numarası.</span><span class="sxs-lookup"><span data-stu-id="01e3c-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01e3c-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="01e3c-113">Return Value</span></span>  
 <span data-ttu-id="01e3c-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="01e3c-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01e3c-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01e3c-115">Requirements</span></span>  
 <span data-ttu-id="01e3c-116">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="01e3c-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e3c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01e3c-117">See also</span></span>

- [<span data-ttu-id="01e3c-118">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01e3c-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
