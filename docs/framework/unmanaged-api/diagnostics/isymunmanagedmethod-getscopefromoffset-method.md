---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedmethod:: Getscopefromsapmasını yöntemi'
title: ISymUnmanagedMethod::GetScopeFromOffset Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetScopeFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type:
- apiref
ms.openlocfilehash: 87dd1f1732ec5d7c8669dbc2bf73b0b6128aafa1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721326"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="bfc12-103">ISymUnmanagedMethod::GetScopeFromOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="bfc12-103">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>

<span data-ttu-id="bfc12-104">Bu yöntem içinde verilen sapmayı kapsayan en kapsamlı sözcük kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="bfc12-104">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="bfc12-105">Bu, yerel değişken aramalarını başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bfc12-105">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfc12-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bfc12-106">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfc12-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bfc12-107">Parameters</span></span>  

 `offset`  
 <span data-ttu-id="bfc12-108">'ndaki `ULONG` Bu, sapmayı içeren bir.</span><span class="sxs-lookup"><span data-stu-id="bfc12-108">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="bfc12-109">dışı Döndürülen [ıdimunmanagedscope](isymunmanagedscope-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bfc12-109">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bfc12-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bfc12-110">Return Value</span></span>  

 <span data-ttu-id="bfc12-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="bfc12-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfc12-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bfc12-112">Requirements</span></span>  

 <span data-ttu-id="bfc12-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bfc12-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfc12-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfc12-114">See also</span></span>

- [<span data-ttu-id="bfc12-115">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bfc12-115">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
