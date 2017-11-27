---
title: ISymUnmanagedBinder::GetReaderForFile Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder.GetReaderForFile
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 856f7eb506f77181d41ebd10148f321197ebfda3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="2265a-102">ISymUnmanagedBinder::GetReaderForFile Metodu</span><span class="sxs-lookup"><span data-stu-id="2265a-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="2265a-103">Bir meta veri arabirimi ve bir dosya adı doğru döndürür <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> modülü ile ilişkili hata ayıklama simgeleri okuma yapacak yapısı.</span><span class="sxs-lookup"><span data-stu-id="2265a-103">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="2265a-104">Yalnızca bu yürütülebilir dosya yanındaki ise bu yöntem program veritabanı (PDB) dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="2265a-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="2265a-105">Güvenlik nedeniyle bu değişiklik yapılmadı.</span><span class="sxs-lookup"><span data-stu-id="2265a-105">This change has been made for security purposes.</span></span> <span data-ttu-id="2265a-106">PDB dosyası için daha kapsamlı bir arama gerekiyorsa kullanın [Isymunmanagedbinder2::getreaderforfile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2265a-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2265a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2265a-107">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2265a-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2265a-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="2265a-109">[in] Meta veri alma arayüzü için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2265a-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="2265a-110">[in] Dosya adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2265a-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="2265a-111">[in] Arama yolu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2265a-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="2265a-112">[out] Ayarlanmış bir işaretçi döndürülen için <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="2265a-112">[out] A pointer that is set to the returned <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2265a-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2265a-113">Return Value</span></span>  
 <span data-ttu-id="2265a-114">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2265a-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2265a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2265a-115">Requirements</span></span>  
 <span data-ttu-id="2265a-116">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2265a-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2265a-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2265a-117">See Also</span></span>  
 [<span data-ttu-id="2265a-118">Isymunmanagedbinder arabirimi</span><span class="sxs-lookup"><span data-stu-id="2265a-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="2265a-119">GetReaderForFile2 yöntemi</span><span class="sxs-lookup"><span data-stu-id="2265a-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
