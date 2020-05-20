---
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
ms.openlocfilehash: c4416e8e4395c4e1967155310d12a1eb68c42d83
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441740"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="2882c-102">ISymUnmanagedBinder::GetReaderForFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2882c-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="2882c-103">Meta veri arabirimi ve dosya adı verildiğinde, modülle ilişkili hata ayıklama sembollerini okuyacak doğru [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2882c-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="2882c-104">Bu yöntem, program veritabanı (PDB) dosyasını yalnızca yürütülebilir dosyanın yanında olduğunda açar.</span><span class="sxs-lookup"><span data-stu-id="2882c-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="2882c-105">Bu değişiklik güvenlik amacıyla yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="2882c-105">This change has been made for security purposes.</span></span> <span data-ttu-id="2882c-106">PDB dosyası için daha kapsamlı bir aramanız gerekiyorsa, [ISymUnmanagedBinder2:: GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2882c-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2882c-107">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2882c-107">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2882c-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2882c-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="2882c-109">'ndaki Meta veri içeri aktarma arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2882c-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="2882c-110">'ndaki Dosya adı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2882c-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="2882c-111">'ndaki Arama yoluna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2882c-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="2882c-112">dışı Döndürülen [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2882c-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2882c-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2882c-113">Return Value</span></span>  
 <span data-ttu-id="2882c-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2882c-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2882c-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2882c-115">Requirements</span></span>  
 <span data-ttu-id="2882c-116">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2882c-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2882c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2882c-117">See also</span></span>

- [<span data-ttu-id="2882c-118">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2882c-118">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="2882c-119">GetReaderForFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2882c-119">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)
