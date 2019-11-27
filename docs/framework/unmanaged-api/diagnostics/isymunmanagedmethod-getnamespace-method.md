---
title: ISymUnmanagedMethod::GetNamespace Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type:
- apiref
ms.openlocfilehash: b8bbedb4c60a2df6070373f2b6a104fff094869a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448972"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="1e207-102">ISymUnmanagedMethod::GetNamespace Metodu</span><span class="sxs-lookup"><span data-stu-id="1e207-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="1e207-103">Bu yöntemin tanımlandığı ad alanını alır.</span><span class="sxs-lookup"><span data-stu-id="1e207-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e207-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e207-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e207-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e207-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="1e207-106">dışı Döndürülen [ıdimunmanagednamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1e207-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e207-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1e207-107">Return Value</span></span>  
 <span data-ttu-id="1e207-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1e207-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e207-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e207-109">Requirements</span></span>  
 <span data-ttu-id="1e207-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1e207-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e207-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e207-111">See also</span></span>

- [<span data-ttu-id="1e207-112">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e207-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
