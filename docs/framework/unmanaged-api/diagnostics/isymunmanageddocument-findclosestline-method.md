---
title: "ISymUnmanagedDocument::FindClosestLine Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.FindClosestLine
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a5467f7d500719e8849b85a57195e98c6eeb7fb3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="29850-102">ISymUnmanagedDocument::FindClosestLine Yöntemi</span><span class="sxs-lookup"><span data-stu-id="29850-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="29850-103">Bir satır olabilir veya bir dizi noktası olmayabilir bu belgede verilen bir dizi noktası en yakın satır döndürür.</span><span class="sxs-lookup"><span data-stu-id="29850-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29850-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29850-104">Syntax</span></span>  
  
```  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29850-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29850-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="29850-106">[in] Bu belgede bir satır.</span><span class="sxs-lookup"><span data-stu-id="29850-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="29850-107">[out] Bir işaretçi bir değişkene satır alır.</span><span class="sxs-lookup"><span data-stu-id="29850-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29850-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="29850-108">Return Value</span></span>  
 <span data-ttu-id="29850-109">Yöntem başarılı olursa S_OK; Aksi takdirde bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="29850-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29850-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29850-110">See Also</span></span>  
 [<span data-ttu-id="29850-111">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29850-111">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
