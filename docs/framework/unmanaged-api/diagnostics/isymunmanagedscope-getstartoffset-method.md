---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedscope:: GetStartOffset Yöntemi'
title: ISymUnmanagedScope::GetStartOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetStartOffset method [.NET Framework debugging]
ms.assetid: da6bbc75-94d1-4354-9722-0d455b4428fb
topic_type:
- apiref
ms.openlocfilehash: c95fbc5229512f08052ffc00f0092f64983ea3f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763325"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="605ef-103">ISymUnmanagedScope::GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="605ef-103">ISymUnmanagedScope::GetStartOffset Method</span></span>

<span data-ttu-id="605ef-104">Bu kapsamın başlangıç sapmasını alır.</span><span class="sxs-lookup"><span data-stu-id="605ef-104">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="605ef-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="605ef-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="605ef-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="605ef-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="605ef-107">dışı `ULONG32` Başlangıç sapmasını içeren bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="605ef-107">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="605ef-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="605ef-108">Return Value</span></span>  

 <span data-ttu-id="605ef-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="605ef-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="605ef-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="605ef-110">Requirements</span></span>  

 <span data-ttu-id="605ef-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="605ef-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="605ef-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="605ef-112">See also</span></span>

- [<span data-ttu-id="605ef-113">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="605ef-113">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="605ef-114">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="605ef-114">GetEndOffset Method</span></span>](isymunmanagedscope-getendoffset-method.md)
