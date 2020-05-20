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
ms.openlocfilehash: 91117eae23d38f3bc608f3203ebe53f92516c9c9
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610502"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="19c87-102">ISymUnmanagedVariable::GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19c87-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="19c87-103">Bu değişkenin üst sapmasını üst öğesi içinde alır.</span><span class="sxs-lookup"><span data-stu-id="19c87-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="19c87-104">Bu bir kapsamdaki yerel değişkense, bitiş boşluğu kapsam için tanımlanan uzaklıklar içinde kalır.</span><span class="sxs-lookup"><span data-stu-id="19c87-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19c87-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="19c87-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19c87-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="19c87-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="19c87-107">dışı Bitiş sapmasını alan bir işaretçisine bir işaretçisi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="19c87-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19c87-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="19c87-108">Return Value</span></span>  
 <span data-ttu-id="19c87-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="19c87-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19c87-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19c87-110">Requirements</span></span>  
 <span data-ttu-id="19c87-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="19c87-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19c87-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19c87-112">See also</span></span>

- [<span data-ttu-id="19c87-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19c87-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="19c87-114">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19c87-114">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)
