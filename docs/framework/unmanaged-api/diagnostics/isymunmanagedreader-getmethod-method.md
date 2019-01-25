---
title: ISymUnmanagedReader::GetMethod Metodu
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
ms.openlocfilehash: deb5d7aa24cf750a9584ef2aa32d10816ec12f57
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614412"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="040a5-102">ISymUnmanagedReader::GetMethod Metodu</span><span class="sxs-lookup"><span data-stu-id="040a5-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="040a5-103">Token metody verilen sembol okuyucu yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="040a5-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="040a5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="040a5-104">Syntax</span></span>  
  
```  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="040a5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="040a5-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="040a5-106">[in] Token metody</span><span class="sxs-lookup"><span data-stu-id="040a5-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="040a5-107">[out] Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="040a5-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="040a5-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="040a5-108">Return Value</span></span>  
 <span data-ttu-id="040a5-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="040a5-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="040a5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="040a5-110">Requirements</span></span>  
 <span data-ttu-id="040a5-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="040a5-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="040a5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="040a5-112">See also</span></span>
- [<span data-ttu-id="040a5-113">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="040a5-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
