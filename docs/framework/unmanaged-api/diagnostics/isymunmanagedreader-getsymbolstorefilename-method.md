---
title: ISymUnmanagedReader::GetSymbolStoreFileName Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymbolStoreFileName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymbolStoreFileName
helpviewer_keywords:
- GetSymbolStoreFileName method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymbolStoreFileName method [.NET Framework debugging]
ms.assetid: c84f4846-9bc8-44a4-9a76-e39106d6d8b2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b00eda9ddad65d6618f097a6ca48b5c7c0eba334
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481132"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="56d86-102">ISymUnmanagedReader::GetSymbolStoreFileName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56d86-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="56d86-103">Sembol deposundaki disk dosya adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="56d86-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56d86-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56d86-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56d86-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="56d86-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="56d86-106">[in] Boyutu `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="56d86-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="56d86-107">[out] Döndürülen adının uzunluğu alan değişken işaretçisi `szName`, null sonlandırma dahil.</span><span class="sxs-lookup"><span data-stu-id="56d86-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="56d86-108">[out] Bir işaretçi değişkenine sembol deposunun dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="56d86-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56d86-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="56d86-109">Return Value</span></span>  
 <span data-ttu-id="56d86-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="56d86-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56d86-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56d86-111">Requirements</span></span>  
 <span data-ttu-id="56d86-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="56d86-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56d86-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56d86-113">See also</span></span>
- [<span data-ttu-id="56d86-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56d86-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
