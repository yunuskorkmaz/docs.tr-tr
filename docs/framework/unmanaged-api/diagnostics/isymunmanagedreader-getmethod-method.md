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
ms.openlocfilehash: ab6228866434b35525b16e97b8cba718b849dea1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993349"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="8f098-102">ISymUnmanagedReader::GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f098-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="8f098-103">Token metody verilen sembol okuyucu yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="8f098-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f098-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f098-104">Syntax</span></span>  
  
```  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f098-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f098-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="8f098-106">[in] Token metody</span><span class="sxs-lookup"><span data-stu-id="8f098-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="8f098-107">[out] Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8f098-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f098-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8f098-108">Return Value</span></span>  
 <span data-ttu-id="8f098-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="8f098-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f098-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f098-110">Requirements</span></span>  
 <span data-ttu-id="8f098-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8f098-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f098-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f098-112">See also</span></span>

- [<span data-ttu-id="8f098-113">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f098-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
