---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanagedwriter:: SetMethodSourceRange Yöntemi'
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
ms.openlocfilehash: 2e2f0f664d8be30a8c3628100fafb3740d34f54f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762077"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="d0ac5-103">ISymUnmanagedWriter::SetMethodSourceRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0ac5-103">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>

<span data-ttu-id="d0ac5-104">Kaynak dosya içindeki bir yöntemin doğru başlangıcını ve sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d0ac5-104">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="d0ac5-105">Yöntemin içinde var olan sıra noktalarından bağımsız olarak bir yöntemin kapsamını belirtmek için bu yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0ac5-105">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0ac5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0ac5-106">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0ac5-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0ac5-107">Parameters</span></span>  

 `startDoc`  
 <span data-ttu-id="d0ac5-108">'ndaki Başlangıç konumunu içeren belgeye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d0ac5-108">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="d0ac5-109">'ndaki Başlangıç satır numarası.</span><span class="sxs-lookup"><span data-stu-id="d0ac5-109">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="d0ac5-110">'ndaki Başlangıç sütunu.</span><span class="sxs-lookup"><span data-stu-id="d0ac5-110">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="d0ac5-111">'ndaki Bitiş konumunu içeren belgeye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d0ac5-111">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="d0ac5-112">'ndaki Son satır numarası.</span><span class="sxs-lookup"><span data-stu-id="d0ac5-112">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="d0ac5-113">'ndaki Bitiş sütun numarası.</span><span class="sxs-lookup"><span data-stu-id="d0ac5-113">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0ac5-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d0ac5-114">Return Value</span></span>  

 <span data-ttu-id="d0ac5-115">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="d0ac5-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0ac5-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0ac5-116">Requirements</span></span>  

 <span data-ttu-id="d0ac5-117">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d0ac5-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0ac5-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0ac5-118">See also</span></span>

- [<span data-ttu-id="d0ac5-119">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0ac5-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
