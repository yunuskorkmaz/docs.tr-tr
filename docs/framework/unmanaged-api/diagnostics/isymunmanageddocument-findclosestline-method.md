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
ms.openlocfilehash: 5ec67758e3174493cbd5cec1de0dcce30013ac43
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698591"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="953ce-102">ISymUnmanagedDocument::FindClosestLine Yöntemi</span><span class="sxs-lookup"><span data-stu-id="953ce-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>

<span data-ttu-id="953ce-103">Bu belgede bir sıra noktası olabilecek veya olmayan bir satır verildiğinde, bir dizi noktası olan en yakın çizgiyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="953ce-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="953ce-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="953ce-104">Syntax</span></span>  
  
```cpp  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="953ce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="953ce-105">Parameters</span></span>  

 `line`  
 <span data-ttu-id="953ce-106">'ndaki Bu belgedeki bir çizgi.</span><span class="sxs-lookup"><span data-stu-id="953ce-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="953ce-107">dışı Satırı alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="953ce-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="953ce-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="953ce-108">Return Value</span></span>  

 <span data-ttu-id="953ce-109">Yöntem başarılı olursa S_OK; Aksi takdirde, bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="953ce-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="953ce-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="953ce-110">See also</span></span>

- [<span data-ttu-id="953ce-111">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="953ce-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
