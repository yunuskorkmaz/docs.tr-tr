---
title: ISymUnmanagedDocument::FindClosestLine Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.FindClosestLine
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type:
- apiref
ms.openlocfilehash: 0e95255479792c7056bee7ee4f6c507e0f41eb6a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449221"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="e8577-102">ISymUnmanagedDocument::FindClosestLine Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e8577-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="e8577-103">Bu belgede bir sıra noktası olabilecek veya olmayan bir satır verildiğinde, bir dizi noktası olan en yakın çizgiyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="e8577-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8577-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8577-104">Syntax</span></span>  
  
```cpp  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8577-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e8577-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="e8577-106">'ndaki Bu belgedeki bir çizgi.</span><span class="sxs-lookup"><span data-stu-id="e8577-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e8577-107">dışı Satırı alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e8577-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8577-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e8577-108">Return Value</span></span>  
 <span data-ttu-id="e8577-109">Yöntem başarılı olursa S_OK; Aksi takdirde, bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="e8577-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8577-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8577-110">See also</span></span>

- [<span data-ttu-id="e8577-111">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e8577-111">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
