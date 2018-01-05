---
title: ISymUnmanagedReader::GetGlobalVariables Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetGlobalVariables
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetGlobalVariables
helpviewer_keywords:
- GetGlobalVariables method [.NET Framework debugging]
- ISymUnmanagedReader::GetGlobalVariables method [.NET Framework debugging]
ms.assetid: a2dd5098-3e58-4be5-b7a2-e4160b3b505a
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b17abe352dc37b366294e72de53bcc4e1ad8dc9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="29019-102">ISymUnmanagedReader::GetGlobalVariables Metodu</span><span class="sxs-lookup"><span data-stu-id="29019-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>
<span data-ttu-id="29019-103">Tüm genel değişkenler döndürür.</span><span class="sxs-lookup"><span data-stu-id="29019-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29019-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29019-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29019-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29019-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="29019-106">[in] Tarafından için arabellek uzunluğu işaret `pcVars`.</span><span class="sxs-lookup"><span data-stu-id="29019-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="29019-107">[out] Bir işaretçi bir `ULONG32` değişkenleri içermesi gerekir arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="29019-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="29019-108">[out] Değişkenleri içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="29019-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29019-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="29019-109">Return Value</span></span>  
 <span data-ttu-id="29019-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="29019-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29019-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29019-111">Requirements</span></span>  
 <span data-ttu-id="29019-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="29019-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29019-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29019-113">See Also</span></span>  
 [<span data-ttu-id="29019-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29019-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
