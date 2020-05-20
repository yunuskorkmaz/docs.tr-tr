---
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
ms.openlocfilehash: d04c9865d8272bf8d04080f6049ddfb1d4c643bb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614584"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="a4410-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4410-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="a4410-103">Yerel değişkenlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a4410-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4410-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a4410-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4410-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a4410-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="a4410-106">'ndaki Yöntemlerin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="a4410-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="a4410-107">dışı `ULONG32`Yerel değişken sayısını içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a4410-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4410-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a4410-108">Return Value</span></span>  
 <span data-ttu-id="a4410-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a4410-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4410-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a4410-110">Requirements</span></span>  
 <span data-ttu-id="a4410-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a4410-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4410-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4410-112">See also</span></span>

- [<span data-ttu-id="a4410-113">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4410-113">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
