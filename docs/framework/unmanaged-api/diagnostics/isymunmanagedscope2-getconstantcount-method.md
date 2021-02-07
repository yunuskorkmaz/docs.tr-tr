---
description: 'Daha fazla bilgi edinin: ISymUnmanagedScope2:: GetConstantCount yöntemi'
title: ISymUnmanagedScope2::GetConstantCount Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstantCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type:
- apiref
ms.openlocfilehash: e5b084edb116432aa43360db72ca2528dd3cc6a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763260"
---
# <a name="isymunmanagedscope2getconstantcount-method"></a><span data-ttu-id="0dcd5-103">ISymUnmanagedScope2::GetConstantCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0dcd5-103">ISymUnmanagedScope2::GetConstantCount Method</span></span>

<span data-ttu-id="0dcd5-104">Bu kapsam içinde tanımlanan sabitlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0dcd5-104">Gets a count of the constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dcd5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0dcd5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dcd5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0dcd5-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="0dcd5-107">dışı `ULONG32` Sabitleri içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0dcd5-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0dcd5-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0dcd5-108">Return Value</span></span>  

 <span data-ttu-id="0dcd5-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="0dcd5-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dcd5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0dcd5-110">Requirements</span></span>  

 <span data-ttu-id="0dcd5-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0dcd5-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dcd5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dcd5-112">See also</span></span>

- [<span data-ttu-id="0dcd5-113">ISymUnmanagedScope2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0dcd5-113">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
