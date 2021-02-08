---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanagedciltçi:: GetReaderForFile yöntemi'
title: ISymUnmanagedBinder::GetReaderForFile Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderForFile
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type:
- apiref
ms.openlocfilehash: ede494cbc1bbe4059b98a639c1d0621dc2cbdfa6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790223"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="6d01a-103">ISymUnmanagedBinder::GetReaderForFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d01a-103">ISymUnmanagedBinder::GetReaderForFile Method</span></span>

<span data-ttu-id="6d01a-104">Meta veri arabirimi ve dosya adı verildiğinde, modülle ilişkili hata ayıklama sembollerini okuyacak doğru [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="6d01a-104">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="6d01a-105">Bu yöntem, program veritabanı (PDB) dosyasını yalnızca yürütülebilir dosyanın yanında olduğunda açar.</span><span class="sxs-lookup"><span data-stu-id="6d01a-105">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="6d01a-106">Bu değişiklik güvenlik amacıyla yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="6d01a-106">This change has been made for security purposes.</span></span> <span data-ttu-id="6d01a-107">PDB dosyası için daha kapsamlı bir aramanız gerekiyorsa, [ISymUnmanagedBinder2:: GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6d01a-107">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d01a-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d01a-108">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d01a-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d01a-109">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="6d01a-110">'ndaki Meta veri içeri aktarma arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6d01a-110">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="6d01a-111">'ndaki Dosya adı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6d01a-111">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="6d01a-112">'ndaki Arama yoluna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6d01a-112">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="6d01a-113">dışı Döndürülen [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6d01a-113">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d01a-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6d01a-114">Return Value</span></span>  

 <span data-ttu-id="6d01a-115">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6d01a-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d01a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d01a-116">Requirements</span></span>  

 <span data-ttu-id="6d01a-117">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6d01a-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d01a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d01a-118">See also</span></span>

- [<span data-ttu-id="6d01a-119">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d01a-119">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="6d01a-120">GetReaderForFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d01a-120">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)
