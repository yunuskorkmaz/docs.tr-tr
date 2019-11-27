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
ms.openlocfilehash: cba4af737cc6a6441d38ba0f940fffe54f5c4f09
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449065"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="47c3e-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47c3e-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="47c3e-103">Yerel değişkenlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="47c3e-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47c3e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47c3e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47c3e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="47c3e-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="47c3e-106">'ndaki Yöntemlerin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="47c3e-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="47c3e-107">dışı Yerel değişken sayısını içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir `ULONG32` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="47c3e-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47c3e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="47c3e-108">Return Value</span></span>  
 <span data-ttu-id="47c3e-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="47c3e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47c3e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47c3e-110">Requirements</span></span>  
 <span data-ttu-id="47c3e-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="47c3e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47c3e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47c3e-112">See also</span></span>

- [<span data-ttu-id="47c3e-113">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47c3e-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
