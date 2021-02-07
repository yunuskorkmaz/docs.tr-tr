---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedvariable:: GetStartOffset Yöntemi'
title: ISymUnmanagedVariable::GetStartOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type:
- apiref
ms.openlocfilehash: 96ff27cfaf53c7a63c819b1a423e62478cf74832
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762727"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="c35e5-103">ISymUnmanagedVariable::GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c35e5-103">ISymUnmanagedVariable::GetStartOffset Method</span></span>

<span data-ttu-id="c35e5-104">Bu değişkenin üst öğesi içindeki başlangıç sapmasını alır.</span><span class="sxs-lookup"><span data-stu-id="c35e5-104">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="c35e5-105">Bu bir kapsamdaki yerel değişkense, başlangıç boşluğu kapsam için tanımlanan uzaklıklara girer.</span><span class="sxs-lookup"><span data-stu-id="c35e5-105">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c35e5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c35e5-106">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c35e5-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c35e5-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="c35e5-108">dışı Başlangıç sapmasını alan bir işaretçisine bir işaretçisi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="c35e5-108">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c35e5-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c35e5-109">Return Value</span></span>  

 <span data-ttu-id="c35e5-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c35e5-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c35e5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c35e5-111">Requirements</span></span>  

 <span data-ttu-id="c35e5-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c35e5-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c35e5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c35e5-113">See also</span></span>

- [<span data-ttu-id="c35e5-114">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c35e5-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="c35e5-115">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c35e5-115">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)
