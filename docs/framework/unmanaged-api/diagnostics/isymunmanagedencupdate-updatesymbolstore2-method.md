---
title: ISymUnmanagedENCUpdate::UpdateSymbolStore2 Yöntemi
ms.date: 03/30/2017
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
ms.openlocfilehash: 393984241412f543b6ac082484cf5e23edb2d9f4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448987"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="b786f-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b786f-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>
<span data-ttu-id="b786f-103">Bir derleyicinin, program veritabanı (PDB) akışından değiştirilmemiş işlevleri yok saymasını sağlar. Bu, satır bilgilerinin gereksinimleri karşılaması şartıyla.</span><span class="sxs-lookup"><span data-stu-id="b786f-103">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="b786f-104">Doğru satır bilgileri, işlevdeki tüm satırlar için eski PDB satırı bilgileri ve bir Delta ile belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b786f-104">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b786f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b786f-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b786f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b786f-106">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="b786f-107">'ndaki Satır bilgilerini içeren bir [IStream](/windows/desktop/api/objidl/nn-objidl-istream) işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b786f-107">[in] A pointer to an [IStream](/windows/desktop/api/objidl/nn-objidl-istream) that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="b786f-108">'ndaki Değiştirilen satırları içeren bir [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b786f-108">[in] A pointer to a [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="b786f-109">'ndaki Değiştirilen satır sayısını temsil eden bir `ULONG`.</span><span class="sxs-lookup"><span data-stu-id="b786f-109">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b786f-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b786f-110">Return Value</span></span>  
 <span data-ttu-id="b786f-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="b786f-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b786f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b786f-112">Requirements</span></span>  
 <span data-ttu-id="b786f-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b786f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b786f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b786f-114">See also</span></span>

- [<span data-ttu-id="b786f-115">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b786f-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
