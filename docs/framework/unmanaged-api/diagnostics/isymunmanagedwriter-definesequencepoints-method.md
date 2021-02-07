---
description: 'Hakkında daha fazla bilgi edinin: ı, Esequencepoints yöntemi:D'
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
ms.openlocfilehash: 0c5ac9854ef341512f58cb1cd63ed7dfcde9962e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762337"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="e8fba-103">ISymUnmanagedWriter::DefineSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e8fba-103">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>

<span data-ttu-id="e8fba-104">Geçerli yöntem içindeki bir dizi noktası grubunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e8fba-104">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="e8fba-105">Her başlangıç satırı ve başlangıç sütunu, bir yöntem içinde bir deyimin başlangıcını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e8fba-105">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="e8fba-106">Her bitiş satırı ve bitiş sütunu, bir yöntem içindeki bir deyimin sonunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e8fba-106">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="e8fba-107">Dizilerin, uzaklıklarda artan sırada sıralanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8fba-107">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="e8fba-108">Konum her zaman yöntemin başından (bayt cinsinden) ölçülür.</span><span class="sxs-lookup"><span data-stu-id="e8fba-108">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8fba-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8fba-109">Syntax</span></span>  
  
```cpp  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8fba-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e8fba-110">Parameters</span></span>  

 `document`  
 <span data-ttu-id="e8fba-111">'ndaki Sıra noktalarının tanımlandığı belge nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e8fba-111">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="e8fba-112">'ndaki ,,, `ULONG32` `offsets` `lines` `columns` `endLines` Ve `endColumns` arabelleklerinin her birinin boyutunu belirten bir.</span><span class="sxs-lookup"><span data-stu-id="e8fba-112">[in] A `ULONG32` that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="e8fba-113">'ndaki Yöntemin başından itibaren ölçülen dizi noktalarının boşluğu.</span><span class="sxs-lookup"><span data-stu-id="e8fba-113">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="e8fba-114">'ndaki Sıra noktalarının başlangıç satırı numaraları.</span><span class="sxs-lookup"><span data-stu-id="e8fba-114">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="e8fba-115">'ndaki Sıra noktalarının başlangıç sütunu numaraları.</span><span class="sxs-lookup"><span data-stu-id="e8fba-115">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="e8fba-116">'ndaki Sıra noktalarının bitiş çizgisi numaraları.</span><span class="sxs-lookup"><span data-stu-id="e8fba-116">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="e8fba-117">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e8fba-117">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="e8fba-118">'ndaki Sıra noktalarının bitiş sütun numaraları.</span><span class="sxs-lookup"><span data-stu-id="e8fba-118">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="e8fba-119">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e8fba-119">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8fba-120">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e8fba-120">Return Value</span></span>  

 <span data-ttu-id="e8fba-121">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="e8fba-121">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8fba-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8fba-122">Requirements</span></span>  

 <span data-ttu-id="e8fba-123">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e8fba-123">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8fba-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8fba-124">See also</span></span>

- [<span data-ttu-id="e8fba-125">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e8fba-125">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
