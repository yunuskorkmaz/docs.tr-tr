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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 760a6feb8400e60b7e14bf244d66c9026031e5dc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474243"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="88a0b-102">ISymUnmanagedDocument::FindClosestLine Yöntemi</span><span class="sxs-lookup"><span data-stu-id="88a0b-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="88a0b-103">Bir dizi noktası olmayabilir veya bu belgeyi bir satır verilen bir dizi noktası en yakın satır döndürür.</span><span class="sxs-lookup"><span data-stu-id="88a0b-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88a0b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88a0b-104">Syntax</span></span>  
  
```  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88a0b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="88a0b-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="88a0b-106">[in] Bu belgeyi bir satır.</span><span class="sxs-lookup"><span data-stu-id="88a0b-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="88a0b-107">[out] Satırın alan bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="88a0b-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88a0b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="88a0b-108">Return Value</span></span>  
 <span data-ttu-id="88a0b-109">Yöntem başarılı olursa S_OK; Aksi takdirde bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="88a0b-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88a0b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88a0b-110">See also</span></span>
- [<span data-ttu-id="88a0b-111">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="88a0b-111">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
