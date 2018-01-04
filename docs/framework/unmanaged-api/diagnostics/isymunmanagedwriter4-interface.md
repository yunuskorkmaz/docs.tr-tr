---
title: ISymUnmanagedWriter4 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5531b491da70cb78de1234e750c2e15390c10ce5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="9de42-102">ISymUnmanagedWriter4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9de42-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="9de42-103">Isymunmanagedwriter4 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9de42-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9de42-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9de42-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="9de42-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9de42-105">Methods</span></span>  
 <span data-ttu-id="9de42-106">Bu arabirim, aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="9de42-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="9de42-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9de42-107">Method</span></span>|<span data-ttu-id="9de42-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9de42-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9de42-109">GetDebugInfoWithPadding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9de42-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="9de42-110">Aynı işlevleri [Getdebugınfo yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) yol dizesi sabit bir boyuta dize verilerini yapmak için bir sonlandırma null karakteri aşağıdaki sıfırlarla dışında `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="9de42-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="9de42-111">Doldurma yolu dize uzunluğu kendisi ise yalnızca verilen değerinden `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="9de42-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="9de42-112">Bu araçlar, fark PE dosyaları yazmak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="9de42-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9de42-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9de42-113">Requirements</span></span>  
 <span data-ttu-id="9de42-114">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9de42-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9de42-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9de42-115">See Also</span></span>  
 [<span data-ttu-id="9de42-116">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9de42-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="9de42-117">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9de42-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
