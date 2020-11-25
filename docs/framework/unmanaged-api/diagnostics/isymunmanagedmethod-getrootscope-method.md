---
title: ISymUnmanagedMethod::GetRootScope Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRootScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type:
- apiref
ms.openlocfilehash: 071738c8fb9b40457215e21172240aa7e77198cd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699475"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="e9192-102">ISymUnmanagedMethod::GetRootScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9192-102">ISymUnmanagedMethod::GetRootScope Method</span></span>

<span data-ttu-id="e9192-103">Bu metot içindeki kök sözcük kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="e9192-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="e9192-104">Bu kapsam tüm yöntemi barındırır.</span><span class="sxs-lookup"><span data-stu-id="e9192-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9192-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e9192-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9192-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9192-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="e9192-107">dışı Döndürülen [ıdimunmanagedscope](isymunmanagedscope-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e9192-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9192-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e9192-108">Return Value</span></span>  

 <span data-ttu-id="e9192-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="e9192-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9192-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9192-110">Requirements</span></span>  

 <span data-ttu-id="e9192-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e9192-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9192-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9192-112">See also</span></span>

- [<span data-ttu-id="e9192-113">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9192-113">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
