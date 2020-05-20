---
title: ISymUnmanagedScope::GetEndOffset Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
ms.openlocfilehash: 4d6bd239a15bd196f840007af120cb062499f4c9
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614857"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="327e2-102">ISymUnmanagedScope::GetEndOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="327e2-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="327e2-103">Bu kapsamın bitiş sapmasını alır.</span><span class="sxs-lookup"><span data-stu-id="327e2-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="327e2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="327e2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="327e2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="327e2-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="327e2-106">dışı Bitiş sapmasını alan bir işaretçisine bir işaretçisi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="327e2-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="327e2-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="327e2-107">Return Value</span></span>  
 <span data-ttu-id="327e2-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="327e2-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="327e2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="327e2-109">Requirements</span></span>  
 <span data-ttu-id="327e2-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="327e2-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="327e2-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="327e2-111">See also</span></span>

- [<span data-ttu-id="327e2-112">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="327e2-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="327e2-113">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="327e2-113">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)
