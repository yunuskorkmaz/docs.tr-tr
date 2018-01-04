---
title: "ISymUnmanagedWriter::CloseNamespace Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.CloseNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::CloseNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::CloseNamespace method [.NET Framework debugging]
- CloseNamespace method [.NET Framework debugging]
ms.assetid: 7f74d9c5-1377-4958-b842-6306d611cbd5
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 364c2a851371ea147a61a49826efe702140c5b2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="1222f-102">ISymUnmanagedWriter::CloseNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1222f-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="1222f-103">Kapanır ad alanı en son açıldı.</span><span class="sxs-lookup"><span data-stu-id="1222f-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1222f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1222f-104">Syntax</span></span>  
  
```  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1222f-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1222f-105">Return Value</span></span>  
 <span data-ttu-id="1222f-106">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1222f-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1222f-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1222f-107">Requirements</span></span>  
 <span data-ttu-id="1222f-108">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1222f-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1222f-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1222f-109">See Also</span></span>  
 [<span data-ttu-id="1222f-110">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1222f-110">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="1222f-111">OpenNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1222f-111">OpenNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)
