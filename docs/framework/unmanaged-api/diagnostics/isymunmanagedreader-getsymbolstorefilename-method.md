---
title: ISymUnmanagedReader::GetSymbolStoreFileName Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetSymbolStoreFileName
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetSymbolStoreFileName
helpviewer_keywords:
- GetSymbolStoreFileName method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymbolStoreFileName method [.NET Framework debugging]
ms.assetid: c84f4846-9bc8-44a4-9a76-e39106d6d8b2
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1646e8fa5f04da56e4489dca9581e9dc56e01d0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="87df1-102">ISymUnmanagedReader::GetSymbolStoreFileName Metodu</span><span class="sxs-lookup"><span data-stu-id="87df1-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="87df1-103">Sembol deposu disk üzerinde dosya adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="87df1-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87df1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87df1-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87df1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87df1-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="87df1-106">[in] Boyutunu `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="87df1-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="87df1-107">[out] Bir işaretçi döndürdü adının uzunluğu alır değişken `szName`, null sonlandırma dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="87df1-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="87df1-108">[out] Bir işaretçi simge deposunun dosya adını alır değişken.</span><span class="sxs-lookup"><span data-stu-id="87df1-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87df1-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="87df1-109">Return Value</span></span>  
 <span data-ttu-id="87df1-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="87df1-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87df1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87df1-111">Requirements</span></span>  
 <span data-ttu-id="87df1-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="87df1-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87df1-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87df1-113">See Also</span></span>  
 [<span data-ttu-id="87df1-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87df1-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
