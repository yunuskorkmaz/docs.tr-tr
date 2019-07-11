---
title: ISymUnmanagedReader::GetMethod Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedReader interface [.NET Framework debugging]
- ISymUnmanagedReader::GetMethod method [.NET Framework debugging]
ms.assetid: ae6cfb29-bc2c-4606-af86-1d32ebd31020
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 35dd8dd272ea8b4fc21cb9d7dce6899ceb836265
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777006"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="ba610-102">ISymUnmanagedReader::GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba610-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="ba610-103">Token metody verilen sembol okuyucu yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="ba610-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba610-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba610-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba610-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba610-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="ba610-106">[in] Token metody</span><span class="sxs-lookup"><span data-stu-id="ba610-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ba610-107">[out] Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ba610-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba610-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ba610-108">Return Value</span></span>  
 <span data-ttu-id="ba610-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ba610-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba610-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba610-110">Requirements</span></span>  
 <span data-ttu-id="ba610-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ba610-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba610-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba610-112">See also</span></span>

- [<span data-ttu-id="ba610-113">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba610-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
