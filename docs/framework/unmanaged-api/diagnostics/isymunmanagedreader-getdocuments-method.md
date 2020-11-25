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
ms.openlocfilehash: 757b7fecbbb187da079c8a5c51462ec58431966f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707626"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="25b2c-102">ISymUnmanagedReader::GetDocuments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25b2c-102">ISymUnmanagedReader::GetDocuments Method</span></span>

<span data-ttu-id="25b2c-103">Sembol deposunda tanımlanan tüm belgelerin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="25b2c-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25b2c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="25b2c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25b2c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25b2c-105">Parameters</span></span>  

 `cDocs`  
 <span data-ttu-id="25b2c-106">'ndaki `pDocs` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="25b2c-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="25b2c-107">dışı Dizi uzunluğunu alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="25b2c-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="25b2c-108">dışı Belge dizisini alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="25b2c-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25b2c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="25b2c-109">Return Value</span></span>  

 <span data-ttu-id="25b2c-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="25b2c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25b2c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25b2c-111">Requirements</span></span>  

 <span data-ttu-id="25b2c-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="25b2c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b2c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25b2c-113">See also</span></span>

- [<span data-ttu-id="25b2c-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25b2c-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
