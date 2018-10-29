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
ms.openlocfilehash: df6a35dcaebc681aa5463a014d3283c81efea617
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199870"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="afdca-102">ISymUnmanagedBinder::GetReaderForFile Metodu</span><span class="sxs-lookup"><span data-stu-id="afdca-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="afdca-103">Meta veri arayüzü ve bir dosya adı, doğru döndürür [Isymunmanagedreader](isymunmanagedreader-interface.md) modülle ilişkili hata ayıklama sembolleri okuyacaksa arabirimi.</span><span class="sxs-lookup"><span data-stu-id="afdca-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="afdca-104">Bu yöntem, yalnızca yürütülebilir dosyanın yanındaki ise program veritabanı (PDB) dosyası açılır.</span><span class="sxs-lookup"><span data-stu-id="afdca-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="afdca-105">Güvenlik nedeniyle bu değişiklik yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="afdca-105">This change has been made for security purposes.</span></span> <span data-ttu-id="afdca-106">PDB dosyası için daha kapsamlı bir arama ihtiyacınız varsa, [Isymunmanagedbinder2::getreaderforfile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="afdca-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afdca-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="afdca-107">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afdca-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="afdca-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="afdca-109">[in] Meta veri alma arayüzü işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="afdca-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="afdca-110">[in] Dosya adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="afdca-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="afdca-111">[in] Arama yolu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="afdca-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="afdca-112">[out] Ayarlanmış bir işaretçi ve döndürülen [Isymunmanagedreader](isymunmanagedreader-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="afdca-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="afdca-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="afdca-113">Return Value</span></span>  
 <span data-ttu-id="afdca-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="afdca-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afdca-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="afdca-115">Requirements</span></span>  
 <span data-ttu-id="afdca-116">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="afdca-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afdca-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="afdca-117">See Also</span></span>  
 [<span data-ttu-id="afdca-118">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afdca-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="afdca-119">GetReaderForFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="afdca-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
