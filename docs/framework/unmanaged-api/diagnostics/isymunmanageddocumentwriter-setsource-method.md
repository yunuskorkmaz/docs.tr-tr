---
title: "ISymUnmanagedDocumentWriter::SetSource Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocumentWriter.SetSource
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 287eba260ca20bae9da94ed2d00dcf1661fe14cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="510d5-102">ISymUnmanagedDocumentWriter::SetSource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="510d5-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="510d5-103">Yazılmakta bir belgeyi katıştırılmış kaynağı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="510d5-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="510d5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="510d5-104">Syntax</span></span>  
  
```  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="510d5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="510d5-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="510d5-106">[in] A `ULONG32` boyutunu içeren `source` arabellek.</span><span class="sxs-lookup"><span data-stu-id="510d5-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="510d5-107">[in] Katıştırılmış kaynak depolayan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="510d5-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="510d5-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="510d5-108">Return Value</span></span>  
 <span data-ttu-id="510d5-109">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="510d5-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="510d5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="510d5-110">Requirements</span></span>  
 <span data-ttu-id="510d5-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="510d5-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="510d5-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="510d5-112">See Also</span></span>  
 [<span data-ttu-id="510d5-113">ISymUnmanagedDocumentWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="510d5-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
