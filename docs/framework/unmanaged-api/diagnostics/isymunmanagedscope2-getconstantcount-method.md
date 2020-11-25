---
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
ms.openlocfilehash: 59f4d85f1d8f24724a2d7eef332ac3b3387b7c91
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725865"
---
# <a name="isymunmanagedscope2getconstantcount-method"></a><span data-ttu-id="98a17-102">ISymUnmanagedScope2::GetConstantCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98a17-102">ISymUnmanagedScope2::GetConstantCount Method</span></span>

<span data-ttu-id="98a17-103">Bu kapsam içinde tanımlanan sabitlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="98a17-103">Gets a count of the constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98a17-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="98a17-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98a17-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98a17-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="98a17-106">dışı `ULONG32` Sabitleri içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="98a17-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98a17-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="98a17-107">Return Value</span></span>  

 <span data-ttu-id="98a17-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="98a17-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98a17-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98a17-109">Requirements</span></span>  

 <span data-ttu-id="98a17-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="98a17-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98a17-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98a17-111">See also</span></span>

- [<span data-ttu-id="98a17-112">ISymUnmanagedScope2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98a17-112">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
