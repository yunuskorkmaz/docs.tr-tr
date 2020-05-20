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
ms.openlocfilehash: b8a3a74888a3caae03da6f88a003bd277939ae59
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615052"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="1e637-102">ISymUnmanagedReader::GetDocuments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e637-102">ISymUnmanagedReader::GetDocuments Method</span></span>
<span data-ttu-id="1e637-103">Sembol deposunda tanımlanan tüm belgelerin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e637-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e637-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1e637-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e637-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e637-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="1e637-106">'ndaki `pDocs`Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="1e637-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="1e637-107">dışı Dizi uzunluğunu alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1e637-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="1e637-108">dışı Belge dizisini alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1e637-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e637-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1e637-109">Return Value</span></span>  
 <span data-ttu-id="1e637-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1e637-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e637-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e637-111">Requirements</span></span>  
 <span data-ttu-id="1e637-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1e637-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e637-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e637-113">See also</span></span>

- [<span data-ttu-id="1e637-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e637-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
