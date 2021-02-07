---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanageddocument:: FindClosestLine yöntemi'
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
ms.openlocfilehash: 0409a5cc29bf148a49a5267d34662f763fc302d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737837"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="36104-103">ISymUnmanagedDocument::FindClosestLine Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36104-103">ISymUnmanagedDocument::FindClosestLine Method</span></span>

<span data-ttu-id="36104-104">Bu belgede bir sıra noktası olabilecek veya olmayan bir satır verildiğinde, bir dizi noktası olan en yakın çizgiyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="36104-104">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36104-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36104-105">Syntax</span></span>  
  
```cpp  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36104-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="36104-106">Parameters</span></span>  

 `line`  
 <span data-ttu-id="36104-107">'ndaki Bu belgedeki bir çizgi.</span><span class="sxs-lookup"><span data-stu-id="36104-107">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="36104-108">dışı Satırı alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="36104-108">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36104-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="36104-109">Return Value</span></span>  

 <span data-ttu-id="36104-110">Yöntem başarılı olursa S_OK; Aksi takdirde, bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="36104-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36104-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36104-111">See also</span></span>

- [<span data-ttu-id="36104-112">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36104-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
