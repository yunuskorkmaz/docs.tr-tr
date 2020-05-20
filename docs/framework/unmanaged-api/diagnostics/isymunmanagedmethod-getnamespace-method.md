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
ms.openlocfilehash: cda30f3c73bf75c37ff79fc415e02382b053807e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614493"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="2ff68-102">ISymUnmanagedMethod::GetNamespace Metodu</span><span class="sxs-lookup"><span data-stu-id="2ff68-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="2ff68-103">Bu yöntemin tanımlandığı ad alanını alır.</span><span class="sxs-lookup"><span data-stu-id="2ff68-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ff68-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2ff68-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ff68-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ff68-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="2ff68-106">dışı Döndürülen [ıdimunmanagednamespace](isymunmanagednamespace-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2ff68-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ff68-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2ff68-107">Return Value</span></span>  
 <span data-ttu-id="2ff68-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2ff68-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ff68-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ff68-109">Requirements</span></span>  
 <span data-ttu-id="2ff68-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2ff68-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff68-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ff68-111">See also</span></span>

- [<span data-ttu-id="2ff68-112">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2ff68-112">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
