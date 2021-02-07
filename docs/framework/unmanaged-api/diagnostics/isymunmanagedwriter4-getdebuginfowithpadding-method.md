---
description: 'Şu konuda daha fazla bilgi edinin: ISymUnmanagedWriter4:: GetDebugInfoWithPadding yöntemi'
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding Metodu
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: f5a2026a4ddf12b741b670097e31260e68f33c7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761713"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="2ad15-103">ISymUnmanagedWriter4::GetDebugInfoWithPadding Metodu</span><span class="sxs-lookup"><span data-stu-id="2ad15-103">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>

<span data-ttu-id="2ad15-104">Dize verilerini sabit boyutlu hale getirmek için, bir yol dizesinin Sonlandırıcı null karakteri izleyen sıfırlarla doldurulmasının dışında, [GetDebugInfo yöntemiyle](isymunmanagedwriter-getdebuginfo-method.md) aynı işlevi görür `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="2ad15-104">Functions the same as [GetDebugInfo Method](isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="2ad15-105">Yalnızca yol dize uzunluğu değerinden küçükse doldurma verilir `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="2ad15-105">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="2ad15-106">Bu, farklı PE dosyalarına sahip araçların yazmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="2ad15-106">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ad15-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ad15-107">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ad15-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ad15-108">Parameters</span></span>  
  
|<span data-ttu-id="2ad15-109">Parametre</span><span class="sxs-lookup"><span data-stu-id="2ad15-109">Parameter</span></span>|<span data-ttu-id="2ad15-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ad15-110">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="2ad15-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2ad15-111">Return Value</span></span>  

 <span data-ttu-id="2ad15-112">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ad15-112">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ad15-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ad15-113">Requirements</span></span>  

 <span data-ttu-id="2ad15-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2ad15-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ad15-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ad15-115">See also</span></span>

- [<span data-ttu-id="2ad15-116">ISymUnmanagedWriter4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ad15-116">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
