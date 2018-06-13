---
title: Addımport Method1
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98fefc0240f6496a3e7bfb491e27a57e98cfea1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404072"
---
# <a name="addimport-method1"></a><span data-ttu-id="6ec2c-102">Addımport Method1</span><span class="sxs-lookup"><span data-stu-id="6ec2c-102">AddImport Method1</span></span>
<span data-ttu-id="6ec2c-103">İçeri aktarmalar derlemeye ekler.</span><span class="sxs-lookup"><span data-stu-id="6ec2c-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ec2c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ec2c-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ec2c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ec2c-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6ec2c-106">Derleme engagement'ta benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="6ec2c-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="6ec2c-107">Benzersiz kimliği alınan [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), içeri aktarılacak dosya.</span><span class="sxs-lookup"><span data-stu-id="6ec2c-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6ec2c-108">COM + FileDef bayrakları gibi `ffContainsNoMetaData` ve `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="6ec2c-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="6ec2c-109">`dwFlags` geçirilir [DefineFile yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="6ec2c-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="6ec2c-110">Sonuç dosyası kimliği aldığı belirteci işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6ec2c-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ec2c-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6ec2c-111">Return Value</span></span>  
 <span data-ttu-id="6ec2c-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="6ec2c-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ec2c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ec2c-113">Requirements</span></span>  
 <span data-ttu-id="6ec2c-114">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="6ec2c-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ec2c-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ec2c-115">See Also</span></span>  
 [<span data-ttu-id="6ec2c-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ec2c-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="6ec2c-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ec2c-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="6ec2c-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="6ec2c-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
