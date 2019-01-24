---
title: ISymUnmanagedDispose::Destroy Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose.Destroy
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6a4a0bac056c7c88a491ac05a17b662ace833df1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614464"
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="0f061-102">ISymUnmanagedDispose::Destroy Metodu</span><span class="sxs-lookup"><span data-stu-id="0f061-102">ISymUnmanagedDispose::Destroy Method</span></span>
<span data-ttu-id="0f061-103">Tüm iç başvuruları bırakın ve tüm sonraki yöntem çağrılarında hata döndürmek temel alınan nesnede neden olur.</span><span class="sxs-lookup"><span data-stu-id="0f061-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f061-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f061-104">Syntax</span></span>  
  
```  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0f061-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0f061-105">Return Value</span></span>  
 <span data-ttu-id="0f061-106">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="0f061-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f061-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f061-107">Requirements</span></span>  
 <span data-ttu-id="0f061-108">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0f061-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f061-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f061-109">See also</span></span>
- [<span data-ttu-id="0f061-110">ISymUnmanagedDispose Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f061-110">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)
