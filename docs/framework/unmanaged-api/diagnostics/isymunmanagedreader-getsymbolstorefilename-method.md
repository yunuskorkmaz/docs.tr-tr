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
ms.openlocfilehash: 147b33a3f49f9163daea776779ca26f62561a84e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670020"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="3eee7-102">ISymUnmanagedReader::GetSymbolStoreFileName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3eee7-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="3eee7-103">Sembol deposundaki disk dosya adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3eee7-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eee7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3eee7-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3eee7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3eee7-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="3eee7-106">[in] Boyutu `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="3eee7-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3eee7-107">[out] Döndürülen adının uzunluğu alan değişken işaretçisi `szName`, null sonlandırma dahil.</span><span class="sxs-lookup"><span data-stu-id="3eee7-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="3eee7-108">[out] Bir işaretçi değişkenine sembol deposunun dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="3eee7-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3eee7-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3eee7-109">Return Value</span></span>  
 <span data-ttu-id="3eee7-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3eee7-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3eee7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3eee7-111">Requirements</span></span>  
 <span data-ttu-id="3eee7-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3eee7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eee7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3eee7-113">See also</span></span>

- [<span data-ttu-id="3eee7-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3eee7-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
