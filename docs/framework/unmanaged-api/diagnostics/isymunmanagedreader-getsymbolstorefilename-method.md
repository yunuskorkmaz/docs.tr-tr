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
ms.openlocfilehash: b3674c4058dba2f6185418b55b35eefb14c312f6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431234"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="b67b1-102">ISymUnmanagedReader::GetSymbolStoreFileName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b67b1-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="b67b1-103">Sembol deposunun disk üzerindeki dosya adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b67b1-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b67b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b67b1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b67b1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b67b1-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="b67b1-106">'ndaki `szName` arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="b67b1-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b67b1-107">dışı Null sonlandırma dahil olmak üzere, `szName`döndürülen adın uzunluğunu alan değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b67b1-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="b67b1-108">dışı Sembol deposunun dosya adını alan değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b67b1-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b67b1-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b67b1-109">Return Value</span></span>  
 <span data-ttu-id="b67b1-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="b67b1-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b67b1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b67b1-111">Requirements</span></span>  
 <span data-ttu-id="b67b1-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b67b1-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b67b1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b67b1-113">See also</span></span>

- [<span data-ttu-id="b67b1-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b67b1-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
