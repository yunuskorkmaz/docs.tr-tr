---
title: ISymUnmanagedWriter::GetDebugInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.GetDebugInfo
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 562e9015f2aa402a90a7b31e4b7002e68893a812
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="94ff0-102">ISymUnmanagedWriter::GetDebugInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="94ff0-102">ISymUnmanagedWriter::GetDebugInfo Method</span></span>
<span data-ttu-id="94ff0-103">Taşınabilir yürütülebilir (PE) dosya üstbilgisinde hata ayıklama dizin girişi yazmak bir derleyici için gerekli bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="94ff0-103">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="94ff0-104">Sembol yazan dışındaki tüm alanları doldurur `TimeDateStamp` ve `PointerToRawData`.</span><span class="sxs-lookup"><span data-stu-id="94ff0-104">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="94ff0-105">(Derleyici, bu iki alan uygun şekilde ayarlamak için sorumlu değildir.)</span><span class="sxs-lookup"><span data-stu-id="94ff0-105">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="94ff0-106">Derleyici bu yöntemi çağırın, verileri blob PE dosyaya yayma, Ayarla `PointerToRawData` verilmiş veri noktası ve IMAGE_DEBUG_DIRECTORY PE dosyaya yazmak için IMAGE_DEBUG_DIRECTORY alanındaki.</span><span class="sxs-lookup"><span data-stu-id="94ff0-106">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="94ff0-107">Derleyici de ayarlamalısınız `TimeDateStamp` eşit alan `TimeDateStamp` oluşturulan PE dosyasının.</span><span class="sxs-lookup"><span data-stu-id="94ff0-107">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94ff0-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94ff0-108">Syntax</span></span>  
  
```  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94ff0-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94ff0-109">Parameters</span></span>  
 `pIDD`  
 <span data-ttu-id="94ff0-110">[içinde out] Bir işaretçi simge yazan doldurur bir IMAGE_DEBUG_DIRECTORY için.</span><span class="sxs-lookup"><span data-stu-id="94ff0-110">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="94ff0-111">[in] A `DWORD` hata ayıklama verilerin boyutunu içerir.</span><span class="sxs-lookup"><span data-stu-id="94ff0-111">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="94ff0-112">[out] Bir işaretçi bir `DWORD` hata ayıklama verileri içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="94ff0-112">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="94ff0-113">[out] Sembol deposu için hata ayıklama verileri tutmak için yeterince büyük bir arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94ff0-113">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94ff0-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="94ff0-114">Return Value</span></span>  
 <span data-ttu-id="94ff0-115">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="94ff0-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94ff0-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94ff0-116">Requirements</span></span>  
 <span data-ttu-id="94ff0-117">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="94ff0-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94ff0-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94ff0-118">See Also</span></span>  
 [<span data-ttu-id="94ff0-119">Isymunmanagedwriter arabirimi</span><span class="sxs-lookup"><span data-stu-id="94ff0-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
