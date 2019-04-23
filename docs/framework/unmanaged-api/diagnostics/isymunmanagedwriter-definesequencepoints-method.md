---
title: ISymUnmanagedWriter::DefineSequencePoints Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 735b33ac1f049f8d4d3740239e7c34a6fa16dd32
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146945"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="6bba4-102">ISymUnmanagedWriter::DefineSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bba4-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="6bba4-103">Bir dizi noktaları geçerli yöntemi içinde grubunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6bba4-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="6bba4-104">Her bir başlangıç satırı ve başlangıç sütunu bir ifade bir yöntem içinde başlangıcı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6bba4-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="6bba4-105">Her bitiş satır ve sütun bitiş sonu bir deyimin bir yöntem içinde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6bba4-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="6bba4-106">Diziler uzaklıkları artan düzende sıralanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6bba4-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="6bba4-107">Uzaklık her zaman başından itibaren bayt cinsinden yöntemi ölçülür.</span><span class="sxs-lookup"><span data-stu-id="6bba4-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bba4-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6bba4-108">Syntax</span></span>  
  
```  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bba4-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6bba4-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="6bba4-110">[in] Dizi noktaları tanımlı belge nesnesi.</span><span class="sxs-lookup"><span data-stu-id="6bba4-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="6bba4-111">[in] A `ULONG32` her birinin boyutunu belirtir `offsets`, `lines`, `columns`, `endLines`, ve `endColumns` arabellek.</span><span class="sxs-lookup"><span data-stu-id="6bba4-111">[in] A `ULONG32` that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="6bba4-112">[in] Dizi noktaları uzaklığı yöntemi başından itibaren ölçülür.</span><span class="sxs-lookup"><span data-stu-id="6bba4-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="6bba4-113">[in] Dizi noktaları başlangıç satır sayısı.</span><span class="sxs-lookup"><span data-stu-id="6bba4-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="6bba4-114">[in] Başlangıç sütunu numaralarını sıralama noktaları.</span><span class="sxs-lookup"><span data-stu-id="6bba4-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="6bba4-115">[in] Dizi noktaları bitiş satır numaraları.</span><span class="sxs-lookup"><span data-stu-id="6bba4-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="6bba4-116">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6bba4-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="6bba4-117">[in] Bitiş sütunu numaralarını sıralama noktaları.</span><span class="sxs-lookup"><span data-stu-id="6bba4-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="6bba4-118">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6bba4-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6bba4-119">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6bba4-119">Return Value</span></span>  
 <span data-ttu-id="6bba4-120">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6bba4-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bba4-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6bba4-121">Requirements</span></span>  
 <span data-ttu-id="6bba4-122">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6bba4-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bba4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bba4-123">See also</span></span>

- [<span data-ttu-id="6bba4-124">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6bba4-124">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
