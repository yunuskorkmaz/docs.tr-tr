---
title: ISymUnmanagedVariable::GetEndOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
ms.openlocfilehash: cf4179f839b62409d5b2185f3e11e8e732c29187
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721874"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="c227f-102">ISymUnmanagedVariable::GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c227f-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>

<span data-ttu-id="c227f-103">Bu değişkenin üst sapmasını üst öğesi içinde alır.</span><span class="sxs-lookup"><span data-stu-id="c227f-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="c227f-104">Bu bir kapsamdaki yerel değişkense, bitiş boşluğu kapsam için tanımlanan uzaklıklar içinde kalır.</span><span class="sxs-lookup"><span data-stu-id="c227f-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c227f-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c227f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c227f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c227f-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="c227f-107">dışı Bitiş sapmasını alan bir işaretçisine bir işaretçisi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="c227f-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c227f-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c227f-108">Return Value</span></span>  

 <span data-ttu-id="c227f-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c227f-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c227f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c227f-110">Requirements</span></span>  

 <span data-ttu-id="c227f-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c227f-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c227f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c227f-112">See also</span></span>

- [<span data-ttu-id="c227f-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c227f-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="c227f-114">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c227f-114">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)
