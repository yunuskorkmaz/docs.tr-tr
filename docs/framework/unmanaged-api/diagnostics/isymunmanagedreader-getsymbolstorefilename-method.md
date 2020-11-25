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
ms.openlocfilehash: df503e44f20a0b1f02e2c609cc4b52712520faea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720574"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="cfa92-102">ISymUnmanagedReader::GetSymbolStoreFileName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cfa92-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>

<span data-ttu-id="cfa92-103">Sembol deposunun disk üzerindeki dosya adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cfa92-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfa92-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="cfa92-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfa92-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cfa92-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="cfa92-106">'ndaki `szName` Arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="cfa92-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="cfa92-107">dışı Null sonlandırma dahil olmak üzere içinde döndürülen adın uzunluğunu alan değişkene yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="cfa92-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="cfa92-108">dışı Sembol deposunun dosya adını alan değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cfa92-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cfa92-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cfa92-109">Return Value</span></span>  

 <span data-ttu-id="cfa92-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="cfa92-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfa92-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cfa92-111">Requirements</span></span>  

 <span data-ttu-id="cfa92-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cfa92-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfa92-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfa92-113">See also</span></span>

- [<span data-ttu-id="cfa92-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfa92-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
