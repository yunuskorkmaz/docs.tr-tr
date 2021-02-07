---
description: 'Şu konuda daha fazla bilgi edinin: ıendmunmanagedscope:: GetEndOffset Yöntemi'
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
ms.openlocfilehash: ac95b98bb87fbf3dc3b42b5a2e5413f76dfffa34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763486"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="13d79-103">ISymUnmanagedScope::GetEndOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="13d79-103">ISymUnmanagedScope::GetEndOffset Method</span></span>

<span data-ttu-id="13d79-104">Bu kapsamın bitiş sapmasını alır.</span><span class="sxs-lookup"><span data-stu-id="13d79-104">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13d79-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13d79-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13d79-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13d79-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="13d79-107">dışı Bitiş sapmasını alan bir işaretçisine bir işaretçisi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="13d79-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13d79-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="13d79-108">Return Value</span></span>  

 <span data-ttu-id="13d79-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="13d79-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13d79-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13d79-110">Requirements</span></span>  

 <span data-ttu-id="13d79-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="13d79-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13d79-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13d79-112">See also</span></span>

- [<span data-ttu-id="13d79-113">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13d79-113">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="13d79-114">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13d79-114">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)
