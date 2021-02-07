---
description: 'Daha fazla bilgi edinin: ISymUnmanagedScope2:: Getsabitleri yöntemi'
title: ISymUnmanagedScope2::GetConstants Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
ms.openlocfilehash: 025bb9ddd0501f2309b2c0a3f7af20eb961604cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763221"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="0d826-103">ISymUnmanagedScope2::GetConstants Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d826-103">ISymUnmanagedScope2::GetConstants Method</span></span>

<span data-ttu-id="0d826-104">Bu kapsam içinde tanımlanan yerel sabitleri alır.</span><span class="sxs-lookup"><span data-stu-id="0d826-104">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d826-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d826-105">Syntax</span></span>  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d826-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d826-106">Parameters</span></span>  

 `cConstants`  
 <span data-ttu-id="0d826-107">'ndaki `pcConstants` Parametrenin işaret ettiği arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="0d826-107">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="0d826-108">dışı `ULONG32` Sabitleri içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0d826-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="0d826-109">dışı Sabitleri depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="0d826-109">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d826-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0d826-110">Return Value</span></span>  

 <span data-ttu-id="0d826-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="0d826-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d826-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d826-112">Requirements</span></span>  

 <span data-ttu-id="0d826-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0d826-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d826-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d826-114">See also</span></span>

- [<span data-ttu-id="0d826-115">ISymUnmanagedScope2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d826-115">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
