---
title: ISymUnmanagedBinder::GetReaderForFile Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c50bb4ca36043fc2491c9a0615b682c94c422e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="543c1-102">ISymUnmanagedBinder::GetReaderForFile Metodu</span><span class="sxs-lookup"><span data-stu-id="543c1-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="543c1-103">Bir meta veri arabirimi ve bir dosya adı doğru döndürür <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> modülü ile ilişkili hata ayıklama simgeleri okuma yapacak yapısı.</span><span class="sxs-lookup"><span data-stu-id="543c1-103">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="543c1-104">Yalnızca bu yürütülebilir dosya yanındaki ise bu yöntem program veritabanı (PDB) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="543c1-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="543c1-105">Güvenlik nedeniyle bu değişiklik yapılmadı.</span><span class="sxs-lookup"><span data-stu-id="543c1-105">This change has been made for security purposes.</span></span> <span data-ttu-id="543c1-106">PDB dosyası için daha kapsamlı bir arama gerekiyorsa kullanın [Isymunmanagedbinder2::getreaderforfile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="543c1-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="543c1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="543c1-107">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="543c1-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="543c1-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="543c1-109">[in] Meta veri alma arayüzü için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="543c1-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="543c1-110">[in] Dosya adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="543c1-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="543c1-111">[in] Arama yolu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="543c1-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="543c1-112">[out] Ayarlanmış bir işaretçi döndürülen için <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="543c1-112">[out] A pointer that is set to the returned <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="543c1-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="543c1-113">Return Value</span></span>  
 <span data-ttu-id="543c1-114">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="543c1-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="543c1-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="543c1-115">Requirements</span></span>  
 <span data-ttu-id="543c1-116">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="543c1-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="543c1-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="543c1-117">See Also</span></span>  
 [<span data-ttu-id="543c1-118">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="543c1-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="543c1-119">GetReaderForFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="543c1-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
