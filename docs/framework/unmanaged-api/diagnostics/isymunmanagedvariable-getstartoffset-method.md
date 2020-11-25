---
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
ms.openlocfilehash: 68d20c33c5ccd554554cae57ee55f6f51d5d980c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733314"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="0adfd-102">ISymUnmanagedVariable::GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0adfd-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>

<span data-ttu-id="0adfd-103">Bu değişkenin üst öğesi içindeki başlangıç sapmasını alır.</span><span class="sxs-lookup"><span data-stu-id="0adfd-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="0adfd-104">Bu bir kapsamdaki yerel değişkense, başlangıç boşluğu kapsam için tanımlanan uzaklıklara girer.</span><span class="sxs-lookup"><span data-stu-id="0adfd-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0adfd-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0adfd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0adfd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0adfd-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="0adfd-107">dışı Başlangıç sapmasını alan bir işaretçisine bir işaretçisi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="0adfd-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0adfd-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0adfd-108">Return Value</span></span>  

 <span data-ttu-id="0adfd-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="0adfd-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0adfd-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0adfd-110">Requirements</span></span>  

 <span data-ttu-id="0adfd-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0adfd-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0adfd-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0adfd-112">See also</span></span>

- [<span data-ttu-id="0adfd-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0adfd-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="0adfd-114">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0adfd-114">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)
