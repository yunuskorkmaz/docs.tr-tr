---
description: 'Şu konuda daha fazla bilgi edinin: ırivmanagedencupdate:: GetLocalVariableCount Yöntemi'
title: ISymUnmanagedENCUpdate::GetLocalVariableCount Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
ms.openlocfilehash: ab75ba0b0dda5722aebdbdc8b9a242cc90b0ac11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790158"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="174a5-103">ISymUnmanagedENCUpdate::GetLocalVariableCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="174a5-103">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>

<span data-ttu-id="174a5-104">Yerel değişkenlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="174a5-104">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="174a5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="174a5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="174a5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="174a5-106">Parameters</span></span>  

 `mdMethodToken`  
 <span data-ttu-id="174a5-107">'ndaki Yöntemlerin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="174a5-107">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="174a5-108">dışı `ULONG32` Yerel değişken sayısını içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="174a5-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="174a5-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="174a5-109">Return Value</span></span>  

 <span data-ttu-id="174a5-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="174a5-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="174a5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="174a5-111">Requirements</span></span>  

 <span data-ttu-id="174a5-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="174a5-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="174a5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="174a5-113">See also</span></span>

- [<span data-ttu-id="174a5-114">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="174a5-114">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
