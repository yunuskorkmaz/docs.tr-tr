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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 734857428c205b6d806a4279213afb1193f914c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086175"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="b151f-102">ISymUnmanagedWriter::SetMethodSourceRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b151f-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="b151f-103">Gerçek başlangıç ve bitiş bir kaynak dosyası içinde bir yöntemin belirtir.</span><span class="sxs-lookup"><span data-stu-id="b151f-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="b151f-104">Bir yöntem içinde yöntemi mevcut dizi noktaları bağımsız olarak kapsamını belirtmek için bu yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="b151f-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b151f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b151f-105">Syntax</span></span>  
  
```  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b151f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b151f-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="b151f-107">[in] Başlangıç konumu içeren belge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b151f-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="b151f-108">[in] Başlangıç satırı numarası.</span><span class="sxs-lookup"><span data-stu-id="b151f-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="b151f-109">[in] Başlangıç sütunu.</span><span class="sxs-lookup"><span data-stu-id="b151f-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="b151f-110">[in] Bitiş konumu içeren belge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b151f-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="b151f-111">[in] Bitiş satır sayısı.</span><span class="sxs-lookup"><span data-stu-id="b151f-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="b151f-112">[in] Bitiş sütun sayısı.</span><span class="sxs-lookup"><span data-stu-id="b151f-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b151f-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b151f-113">Return Value</span></span>  
 <span data-ttu-id="b151f-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="b151f-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b151f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b151f-115">Requirements</span></span>  
 <span data-ttu-id="b151f-116">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b151f-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b151f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b151f-117">See also</span></span>

- [<span data-ttu-id="b151f-118">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b151f-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
