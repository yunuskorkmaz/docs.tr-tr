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
ms.openlocfilehash: 9e6134d39096c4ab157aa545646d83339f92a0b8
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441038"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="79c3b-102">ISymUnmanagedDocument::FindClosestLine Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79c3b-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="79c3b-103">Bu belgede bir sıra noktası olabilecek veya olmayan bir satır verildiğinde, bir dizi noktası olan en yakın çizgiyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="79c3b-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79c3b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="79c3b-104">Syntax</span></span>  
  
```cpp  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79c3b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79c3b-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="79c3b-106">'ndaki Bu belgedeki bir çizgi.</span><span class="sxs-lookup"><span data-stu-id="79c3b-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="79c3b-107">dışı Satırı alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="79c3b-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79c3b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="79c3b-108">Return Value</span></span>  
 <span data-ttu-id="79c3b-109">Yöntem başarılı olursa S_OK; Aksi takdirde, bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="79c3b-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79c3b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79c3b-110">See also</span></span>

- [<span data-ttu-id="79c3b-111">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79c3b-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
