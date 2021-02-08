---
description: 'Şu konuda daha fazla bilgi edinin: ırivmanagedencupdate:: UpdateSymbolStore2 yöntemi'
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
ms.openlocfilehash: f2e5cbf51c1bab3a538fbf5a3e5824739fa3b250
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790145"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="97c80-103">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97c80-103">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>

<span data-ttu-id="97c80-104">Bir derleyicinin, program veritabanı (PDB) akışından değiştirilmemiş işlevleri yok saymasını sağlar. Bu, satır bilgilerinin gereksinimleri karşılaması şartıyla.</span><span class="sxs-lookup"><span data-stu-id="97c80-104">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="97c80-105">Doğru satır bilgileri, işlevdeki tüm satırlar için eski PDB satırı bilgileri ve bir Delta ile belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="97c80-105">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97c80-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97c80-106">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97c80-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97c80-107">Parameters</span></span>  

 `pIStream`  
 <span data-ttu-id="97c80-108">'ndaki Satır bilgilerini içeren bir [IStream](/windows/desktop/api/objidl/nn-objidl-istream) işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="97c80-108">[in] A pointer to an [IStream](/windows/desktop/api/objidl/nn-objidl-istream) that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="97c80-109">'ndaki Değiştirilen satırları içeren bir [SYMLINEDELTA](symlinedelta-structure.md) yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="97c80-109">[in] A pointer to a [SYMLINEDELTA](symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="97c80-110">'ndaki `ULONG` Değiştirilen satır sayısını temsil eden bir.</span><span class="sxs-lookup"><span data-stu-id="97c80-110">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97c80-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="97c80-111">Return Value</span></span>  

 <span data-ttu-id="97c80-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="97c80-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97c80-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97c80-113">Requirements</span></span>  

 <span data-ttu-id="97c80-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="97c80-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97c80-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97c80-115">See also</span></span>

- [<span data-ttu-id="97c80-116">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97c80-116">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
