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
ms.openlocfilehash: 94cda16466ea5a3d35a478a2ae80281e9414f719
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449364"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="3f2a9-102">ISymUnmanagedBinder::GetReaderForFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f2a9-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="3f2a9-103">Meta veri arabirimi ve dosya adı verildiğinde, modülle ilişkili hata ayıklama sembollerini okuyacak doğru [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="3f2a9-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="3f2a9-104">Bu yöntem, program veritabanı (PDB) dosyasını yalnızca yürütülebilir dosyanın yanında olduğunda açar.</span><span class="sxs-lookup"><span data-stu-id="3f2a9-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="3f2a9-105">Bu değişiklik güvenlik amacıyla yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3f2a9-105">This change has been made for security purposes.</span></span> <span data-ttu-id="3f2a9-106">PDB dosyası için daha kapsamlı bir aramanız gerekiyorsa, [ISymUnmanagedBinder2:: GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f2a9-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f2a9-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f2a9-107">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f2a9-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f2a9-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="3f2a9-109">'ndaki Meta veri içeri aktarma arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3f2a9-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="3f2a9-110">'ndaki Dosya adı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3f2a9-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="3f2a9-111">'ndaki Arama yoluna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3f2a9-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="3f2a9-112">dışı Döndürülen [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3f2a9-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f2a9-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3f2a9-113">Return Value</span></span>  
 <span data-ttu-id="3f2a9-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3f2a9-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f2a9-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f2a9-115">Requirements</span></span>  
 <span data-ttu-id="3f2a9-116">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3f2a9-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f2a9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f2a9-117">See also</span></span>

- [<span data-ttu-id="3f2a9-118">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f2a9-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="3f2a9-119">GetReaderForFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f2a9-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
