---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader:: GetDocuments yöntemi'
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
ms.openlocfilehash: 8ee2a2d8e83fcbe2f5b39960fa99e11de2ab4cd2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800220"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="2b385-103">ISymUnmanagedReader::GetDocuments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b385-103">ISymUnmanagedReader::GetDocuments Method</span></span>

<span data-ttu-id="2b385-104">Sembol deposunda tanımlanan tüm belgelerin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2b385-104">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b385-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b385-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b385-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b385-106">Parameters</span></span>  

 `cDocs`  
 <span data-ttu-id="2b385-107">'ndaki `pDocs` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="2b385-107">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="2b385-108">dışı Dizi uzunluğunu alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2b385-108">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="2b385-109">dışı Belge dizisini alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2b385-109">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b385-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2b385-110">Return Value</span></span>  

 <span data-ttu-id="2b385-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2b385-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b385-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b385-112">Requirements</span></span>  

 <span data-ttu-id="2b385-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2b385-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b385-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b385-114">See also</span></span>

- [<span data-ttu-id="2b385-115">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b385-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
