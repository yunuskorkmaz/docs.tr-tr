---
title: "ISymUnmanagedWriter::DefineSequencePoints Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineSequencePoints
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 836774114798324ac16d3263e58dd56665a9aa49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="203b6-102">ISymUnmanagedWriter::DefineSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="203b6-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="203b6-103">Geçerli yöntemi içinde sıralama noktaları grubunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="203b6-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="203b6-104">Her bir başlangıç satırı ve başlangıç sütunu deyimi bir yöntem içinde başlangıcı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="203b6-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="203b6-105">Her bitiş satır ve sütun bitiş deyimi bir yöntem içinde sonuna tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="203b6-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="203b6-106">Diziler uzaklıkları artan düzende sıralanmış.</span><span class="sxs-lookup"><span data-stu-id="203b6-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="203b6-107">Uzaklık her zaman yönteminin bayt cinsinden ölçülür.</span><span class="sxs-lookup"><span data-stu-id="203b6-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="203b6-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="203b6-108">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="203b6-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="203b6-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="203b6-110">[in] Sıralama noktaları tanımlı belge nesnesi.</span><span class="sxs-lookup"><span data-stu-id="203b6-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="203b6-111">[in] A `ULONG32` her birinin boyutunu gösterir, `offsets`, `lines`, `columns`, `endLines`, ve `endColumns` arabellek.</span><span class="sxs-lookup"><span data-stu-id="203b6-111">[in] A `ULONG32` that that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="203b6-112">[in] Sıralama noktaları uzaklığını yöntemi başından itibaren ölçülür.</span><span class="sxs-lookup"><span data-stu-id="203b6-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="203b6-113">[in] Sıralama noktaları başlangıç satır sayısı.</span><span class="sxs-lookup"><span data-stu-id="203b6-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="203b6-114">[in] Sıralama noktaları başlangıç sütun sayıları.</span><span class="sxs-lookup"><span data-stu-id="203b6-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="203b6-115">[in] Sıralama noktaları bitiş satır numaralarını.</span><span class="sxs-lookup"><span data-stu-id="203b6-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="203b6-116">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="203b6-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="203b6-117">[in] Sıralama noktaları bitiş sütun sayıları.</span><span class="sxs-lookup"><span data-stu-id="203b6-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="203b6-118">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="203b6-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="203b6-119">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="203b6-119">Return Value</span></span>  
 <span data-ttu-id="203b6-120">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="203b6-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="203b6-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="203b6-121">Requirements</span></span>  
 <span data-ttu-id="203b6-122">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="203b6-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="203b6-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="203b6-123">See Also</span></span>  
 [<span data-ttu-id="203b6-124">Isymunmanagedwriter arabirimi</span><span class="sxs-lookup"><span data-stu-id="203b6-124">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
