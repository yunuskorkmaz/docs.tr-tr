---
title: "ISymUnmanagedWriter::OpenNamespace Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.OpenNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e3dffd9605bd238446156d7a32e8e668ddd80916
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="3701c-102">ISymUnmanagedWriter::OpenNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3701c-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="3701c-103">Yeni bir ad alanı açılır.</span><span class="sxs-lookup"><span data-stu-id="3701c-103">Opens a new namespace.</span></span> <span data-ttu-id="3701c-104">Yöntem veya bir ad alanı kaplar değişkenleri tanımlamadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="3701c-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="3701c-105">Ad alanları iç içe.</span><span class="sxs-lookup"><span data-stu-id="3701c-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3701c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3701c-106">Syntax</span></span>  
  
```  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3701c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3701c-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="3701c-108">[in] Yeni ad alanı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3701c-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3701c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3701c-109">Return Value</span></span>  
 <span data-ttu-id="3701c-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3701c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3701c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3701c-111">Requirements</span></span>  
 <span data-ttu-id="3701c-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3701c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3701c-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3701c-113">See Also</span></span>  
 [<span data-ttu-id="3701c-114">Isymunmanagedwriter arabirimi</span><span class="sxs-lookup"><span data-stu-id="3701c-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="3701c-115">CloseNamespace yöntemi</span><span class="sxs-lookup"><span data-stu-id="3701c-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
