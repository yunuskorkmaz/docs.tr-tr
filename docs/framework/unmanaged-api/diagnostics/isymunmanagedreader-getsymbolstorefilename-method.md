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
ms.openlocfilehash: 50cd6d1e3666dd1f15c1e6a6b4f7dcb931b79d8d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777068"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="ca907-102">ISymUnmanagedReader::GetSymbolStoreFileName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca907-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="ca907-103">Sembol deposundaki disk dosya adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca907-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca907-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca907-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca907-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ca907-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ca907-106">[in] Boyutu `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="ca907-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ca907-107">[out] Döndürülen adının uzunluğu alan değişken işaretçisi `szName`, null sonlandırma dahil.</span><span class="sxs-lookup"><span data-stu-id="ca907-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="ca907-108">[out] Bir işaretçi değişkenine sembol deposunun dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="ca907-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca907-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ca907-109">Return Value</span></span>  
 <span data-ttu-id="ca907-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ca907-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca907-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca907-111">Requirements</span></span>  
 <span data-ttu-id="ca907-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ca907-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca907-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca907-113">See also</span></span>

- [<span data-ttu-id="ca907-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca907-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
