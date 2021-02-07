---
description: 'Şu konuda daha fazla bilgi edinin: ıendmunmanagedvariable:: GetEndOffset Yöntemi'
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
ms.openlocfilehash: 302f19c0d9fce1864e94a79efe3a3d1515478c0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762805"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="26e21-103">ISymUnmanagedVariable::GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26e21-103">ISymUnmanagedVariable::GetEndOffset Method</span></span>

<span data-ttu-id="26e21-104">Bu değişkenin üst sapmasını üst öğesi içinde alır.</span><span class="sxs-lookup"><span data-stu-id="26e21-104">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="26e21-105">Bu bir kapsamdaki yerel değişkense, bitiş boşluğu kapsam için tanımlanan uzaklıklar içinde kalır.</span><span class="sxs-lookup"><span data-stu-id="26e21-105">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26e21-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26e21-106">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26e21-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26e21-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="26e21-108">dışı Bitiş sapmasını alan bir işaretçisine bir işaretçisi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="26e21-108">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26e21-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="26e21-109">Return Value</span></span>  

 <span data-ttu-id="26e21-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="26e21-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26e21-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26e21-111">Requirements</span></span>  

 <span data-ttu-id="26e21-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="26e21-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26e21-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26e21-113">See also</span></span>

- [<span data-ttu-id="26e21-114">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26e21-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="26e21-115">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26e21-115">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)
