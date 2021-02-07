---
description: 'Daha fazla bilgi edinin: ISymUnmanagedWriter4 Interface'
title: ISymUnmanagedWriter4 Arabirimi
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: 3814d7e2728f28d224a4e9a6d99f699f220e8a4d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761687"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="d8e13-103">ISymUnmanagedWriter4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8e13-103">ISymUnmanagedWriter4 Interface</span></span>

<span data-ttu-id="d8e13-104">ISymUnmanagedWriter4 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d8e13-104">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8e13-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d8e13-105">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="d8e13-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d8e13-106">Methods</span></span>  

 <span data-ttu-id="d8e13-107">Bu arabirim aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="d8e13-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="d8e13-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d8e13-108">Method</span></span>|<span data-ttu-id="d8e13-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8e13-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d8e13-110">GetDebugInfoWithPadding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8e13-110">GetDebugInfoWithPadding Method</span></span>](isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="d8e13-111">Dize verilerini sabit boyutlu hale getirmek için, bir yol dizesinin Sonlandırıcı null karakteri izleyen sıfırlarla doldurulmasının dışında, [GetDebugInfo yöntemiyle](isymunmanagedwriter-getdebuginfo-method.md) aynı işlevi görür `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="d8e13-111">Functions the same as [GetDebugInfo Method](isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="d8e13-112">Yalnızca yol dize uzunluğu değerinden küçükse doldurma verilir `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="d8e13-112">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="d8e13-113">Bu, farklı PE dosyalarına sahip araçların yazmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d8e13-113">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d8e13-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8e13-114">Requirements</span></span>  

 <span data-ttu-id="d8e13-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d8e13-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8e13-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8e13-116">See also</span></span>

- [<span data-ttu-id="d8e13-117">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d8e13-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="d8e13-118">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8e13-118">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
