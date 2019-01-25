---
title: ISymUnmanagedBinder::GetReaderForFile Metodu
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 53558e1b76d5bb22ff2af3b8d7d9e4006072775b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734294"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="4d7e5-102">ISymUnmanagedBinder::GetReaderForFile Metodu</span><span class="sxs-lookup"><span data-stu-id="4d7e5-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="4d7e5-103">Meta veri arayüzü ve bir dosya adı, doğru döndürür [Isymunmanagedreader](isymunmanagedreader-interface.md) modülle ilişkili hata ayıklama sembolleri okuyacaksa arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4d7e5-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="4d7e5-104">Bu yöntem, yalnızca yürütülebilir dosyanın yanındaki ise program veritabanı (PDB) dosyası açılır.</span><span class="sxs-lookup"><span data-stu-id="4d7e5-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="4d7e5-105">Güvenlik nedeniyle bu değişiklik yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="4d7e5-105">This change has been made for security purposes.</span></span> <span data-ttu-id="4d7e5-106">PDB dosyası için daha kapsamlı bir arama ihtiyacınız varsa, [Isymunmanagedbinder2::getreaderforfile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4d7e5-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d7e5-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d7e5-107">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d7e5-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4d7e5-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="4d7e5-109">[in] Meta veri alma arayüzü işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4d7e5-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="4d7e5-110">[in] Dosya adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4d7e5-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="4d7e5-111">[in] Arama yolu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4d7e5-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="4d7e5-112">[out] Ayarlanmış bir işaretçi ve döndürülen [Isymunmanagedreader](isymunmanagedreader-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4d7e5-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d7e5-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4d7e5-113">Return Value</span></span>  
 <span data-ttu-id="4d7e5-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="4d7e5-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d7e5-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d7e5-115">Requirements</span></span>  
 <span data-ttu-id="4d7e5-116">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4d7e5-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d7e5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d7e5-117">See also</span></span>
- [<span data-ttu-id="4d7e5-118">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d7e5-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="4d7e5-119">GetReaderForFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d7e5-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
