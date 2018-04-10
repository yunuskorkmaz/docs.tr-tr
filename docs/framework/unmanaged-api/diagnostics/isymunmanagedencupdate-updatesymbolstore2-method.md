---
title: ISymUnmanagedENCUpdate::UpdateSymbolStore2 Yöntemi
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISymUnmanagedENCUpdate.UpdateSymbolStore2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2
helpviewer_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2 method [.NET Framework debugging]
- UpdateSymbolStore2 method [.NET Framework debugging]
ms.assetid: 35588317-6184-485c-ab41-4b15fc1765d9
topic_type:
- apiref
caps.latest.revision: 11
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9082a05900330be27066b64f2ad0e99b87e04c61
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="5711e-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5711e-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>
<span data-ttu-id="5711e-103">Program veritabanı (PDB) akışından değiştirilmiş işlevleri satır bilgilerini gereksinimlerini karşılaması koşuluyla atlamak bir derleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="5711e-103">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="5711e-104">Doğru satır bilgilerini eski PDB satırı bilgileri ve işlev tüm satırlar için bir delta ile belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="5711e-104">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5711e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5711e-105">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5711e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5711e-106">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="5711e-107">[in] Bir işaretçi bir [IStream](https://msdn.microsoft.com/library/aa380034.aspx) satır bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5711e-107">[in] A pointer to an [IStream](https://msdn.microsoft.com/library/aa380034.aspx) that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="5711e-108">[in] Bir işaretçi bir [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) değiştirilen satırları içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="5711e-108">[in] A pointer to a [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="5711e-109">[in] A `ULONG` değişmiş satır sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5711e-109">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5711e-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5711e-110">Return Value</span></span>  
 <span data-ttu-id="5711e-111">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5711e-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5711e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5711e-112">Requirements</span></span>  
 <span data-ttu-id="5711e-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5711e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5711e-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5711e-114">See Also</span></span>  
 [<span data-ttu-id="5711e-115">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5711e-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
