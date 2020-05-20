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
ms.openlocfilehash: 650a64e72b410cddfbee7dce676ddbb5a3b8b3d3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614454"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="a783e-102">ISymUnmanagedMethod::GetRootScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a783e-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="a783e-103">Bu metot içindeki kök sözcük kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="a783e-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="a783e-104">Bu kapsam tüm yöntemi barındırır.</span><span class="sxs-lookup"><span data-stu-id="a783e-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a783e-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a783e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a783e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a783e-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a783e-107">dışı Döndürülen [ıdimunmanagedscope](isymunmanagedscope-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a783e-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a783e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a783e-108">Return Value</span></span>  
 <span data-ttu-id="a783e-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a783e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a783e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a783e-110">Requirements</span></span>  
 <span data-ttu-id="a783e-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a783e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a783e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a783e-112">See also</span></span>

- [<span data-ttu-id="a783e-113">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a783e-113">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
