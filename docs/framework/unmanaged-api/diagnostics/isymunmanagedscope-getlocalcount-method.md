---
title: ISymUnmanagedScope::GetLocalCount Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocalCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type:
- apiref
ms.openlocfilehash: 07c41e9d80b1703e86ae06525d64bf166ef2cf8e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717558"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="cdf13-102">ISymUnmanagedScope::GetLocalCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdf13-102">ISymUnmanagedScope::GetLocalCount Method</span></span>

<span data-ttu-id="cdf13-103">Bu kapsam içinde tanımlanan yerel değişkenlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="cdf13-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdf13-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="cdf13-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdf13-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cdf13-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="cdf13-106">dışı `ULONG32` Yerel değişkenlerin sayısını alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="cdf13-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cdf13-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cdf13-107">Return Value</span></span>  

 <span data-ttu-id="cdf13-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="cdf13-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdf13-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cdf13-109">Requirements</span></span>  

 <span data-ttu-id="cdf13-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cdf13-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdf13-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdf13-111">See also</span></span>

- [<span data-ttu-id="cdf13-112">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cdf13-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
