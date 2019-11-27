---
title: ISymUnmanagedReader::GetDocuments Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocuments
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocuments
helpviewer_keywords:
- GetDocuments method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocuments method [.NET Framework debugging]
ms.assetid: e3b73a3f-d089-4101-a9a9-5e0765d05b61
topic_type:
- apiref
ms.openlocfilehash: c26c0a5f8c597613266e2e6d1998edfca8f17b82
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448334"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="5905b-102">ISymUnmanagedReader::GetDocuments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5905b-102">ISymUnmanagedReader::GetDocuments Method</span></span>
<span data-ttu-id="5905b-103">Sembol deposunda tanımlanan tüm belgelerin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5905b-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5905b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5905b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5905b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5905b-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="5905b-106">'ndaki `pDocs` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="5905b-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="5905b-107">dışı Dizi uzunluğunu alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5905b-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="5905b-108">dışı Belge dizisini alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5905b-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5905b-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5905b-109">Return Value</span></span>  
 <span data-ttu-id="5905b-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5905b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5905b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5905b-111">Requirements</span></span>  
 <span data-ttu-id="5905b-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5905b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5905b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5905b-113">See also</span></span>

- [<span data-ttu-id="5905b-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5905b-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
