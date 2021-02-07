---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader:: GetSymbolStoreFileName yöntemi'
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
ms.openlocfilehash: 5cbb33a39cf2e93eab64d5f1f1fefc5ceba1d418
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763949"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="3cc87-103">ISymUnmanagedReader::GetSymbolStoreFileName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3cc87-103">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>

<span data-ttu-id="3cc87-104">Sembol deposunun disk üzerindeki dosya adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3cc87-104">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cc87-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3cc87-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cc87-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3cc87-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="3cc87-107">'ndaki `szName` Arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="3cc87-107">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3cc87-108">dışı Null sonlandırma dahil olmak üzere içinde döndürülen adın uzunluğunu alan değişkene yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="3cc87-108">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="3cc87-109">dışı Sembol deposunun dosya adını alan değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3cc87-109">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3cc87-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3cc87-110">Return Value</span></span>  

 <span data-ttu-id="3cc87-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3cc87-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cc87-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3cc87-112">Requirements</span></span>  

 <span data-ttu-id="3cc87-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3cc87-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc87-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cc87-114">See also</span></span>

- [<span data-ttu-id="3cc87-115">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cc87-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
