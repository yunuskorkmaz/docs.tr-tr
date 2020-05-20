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
ms.openlocfilehash: 9ffba23e3821c48c9b0708e4b6b617db4ddc5959
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83611269"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="5a675-102">ISymUnmanagedScope::GetLocalCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5a675-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="5a675-103">Bu kapsam içinde tanımlanan yerel değişkenlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="5a675-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a675-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5a675-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a675-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5a675-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="5a675-106">dışı `ULONG32`Yerel değişkenlerin sayısını alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5a675-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a675-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5a675-107">Return Value</span></span>  
 <span data-ttu-id="5a675-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5a675-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a675-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a675-109">Requirements</span></span>  
 <span data-ttu-id="5a675-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5a675-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a675-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a675-111">See also</span></span>

- [<span data-ttu-id="5a675-112">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a675-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
