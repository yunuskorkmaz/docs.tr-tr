---
title: ISymUnmanagedDispose::Destroy Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDispose.Destroy
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d418bbb476fea306bf9ad92ce2b30d558627009
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="53ca7-102">ISymUnmanagedDispose::Destroy Metodu</span><span class="sxs-lookup"><span data-stu-id="53ca7-102">ISymUnmanagedDispose::Destroy Method</span></span>
<span data-ttu-id="53ca7-103">Tüm iç başvuruları sürüm ve tüm sonraki yöntem çağrılarını hatası dönmek temel alınan nesnenin neden olur.</span><span class="sxs-lookup"><span data-stu-id="53ca7-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53ca7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53ca7-104">Syntax</span></span>  
  
```  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="53ca7-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="53ca7-105">Return Value</span></span>  
 <span data-ttu-id="53ca7-106">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="53ca7-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53ca7-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53ca7-107">Requirements</span></span>  
 <span data-ttu-id="53ca7-108">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="53ca7-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53ca7-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="53ca7-109">See Also</span></span>  
 [<span data-ttu-id="53ca7-110">ISymUnmanagedDispose Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53ca7-110">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)
