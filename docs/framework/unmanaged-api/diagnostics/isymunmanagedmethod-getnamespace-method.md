---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedmethod:: GetNamespace yöntemi'
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
ms.openlocfilehash: 8cb211b1047aff31cc4f12d538fee414c578155b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721417"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="785a3-103">ISymUnmanagedMethod::GetNamespace Metodu</span><span class="sxs-lookup"><span data-stu-id="785a3-103">ISymUnmanagedMethod::GetNamespace Method</span></span>

<span data-ttu-id="785a3-104">Bu yöntemin tanımlandığı ad alanını alır.</span><span class="sxs-lookup"><span data-stu-id="785a3-104">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="785a3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="785a3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="785a3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="785a3-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="785a3-107">dışı Döndürülen [ıdimunmanagednamespace](isymunmanagednamespace-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="785a3-107">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="785a3-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="785a3-108">Return Value</span></span>  

 <span data-ttu-id="785a3-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="785a3-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="785a3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="785a3-110">Requirements</span></span>  

 <span data-ttu-id="785a3-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="785a3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="785a3-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="785a3-112">See also</span></span>

- [<span data-ttu-id="785a3-113">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="785a3-113">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
