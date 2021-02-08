---
description: 'Hakkında daha fazla bilgi edinin: GUID_ManagedName özniteliği'
title: GUID_ManagedName Özniteliği
ms.date: 03/30/2017
api_name:
- GUID_ManagedName
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GUID_ManagedName
helpviewer_keywords:
- GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type:
- apiref
ms.openlocfilehash: c139e8bdc00aa3b008a706de0c42cfbf8e3510c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799999"
---
# <a name="guid_managedname-attribute"></a><span data-ttu-id="c799c-103">GUID_ManagedName Özniteliği</span><span class="sxs-lookup"><span data-stu-id="c799c-103">GUID_ManagedName Attribute</span></span>

<span data-ttu-id="c799c-104">Bir bileşen nesne modeli (COM) kitaplığı için yönetilen ad alanı adını belirten bir özel arabirim özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c799c-104">Defines a custom interface attribute that specifies the managed namespace name for a component object model (COM) library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c799c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c799c-105">Syntax</span></span>  
  
```idl
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a><span data-ttu-id="c799c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c799c-106">Parameters</span></span>  

 `value`  
 <span data-ttu-id="c799c-107">Kitaplık için yönetilen ad alanı adı.</span><span class="sxs-lookup"><span data-stu-id="c799c-107">The managed namespace name for the library.</span></span>  
  
## <a name="definition"></a><span data-ttu-id="c799c-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="c799c-108">Definition</span></span>  

 <span data-ttu-id="c799c-109">`GUID_ManagedName` , Cor. h içinde aşağıdaki gibi tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="c799c-109">`GUID_ManagedName` is defined in Cor.h as follows:</span></span>  
  
```cpp
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a><span data-ttu-id="c799c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c799c-110">Remarks</span></span>  

 <span data-ttu-id="c799c-111">Özel bir arabirim özniteliği tür kitaplığındaki bir nesne için meta verileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c799c-111">A custom interface attribute defines metadata for an object in the type library.</span></span>  
  
 <span data-ttu-id="c799c-112"><xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> Özniteliğinden yönetilen adı almak için veya kullanın.</span><span class="sxs-lookup"><span data-stu-id="c799c-112">Use <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> to retrieve the managed name from the attribute.</span></span>  
  
 <span data-ttu-id="c799c-113">Daha fazla bilgi için Visual C++ başvuru belgelerindeki [arabirim öznitelikleri](/cpp/windows/attributes/interface-attributes) ' ne bakın.</span><span class="sxs-lookup"><span data-stu-id="c799c-113">For more information, see [Interface Attributes](/cpp/windows/attributes/interface-attributes) in the Visual C++ reference documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c799c-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="c799c-114">Example</span></span>  

 <span data-ttu-id="c799c-115">Aşağıdaki örnek, özniteliğini kullanan bir kitaplık tanımını gösterir `GUID_ManagedName` .</span><span class="sxs-lookup"><span data-stu-id="c799c-115">The following example shows a library definition using the `GUID_ManagedName` attribute.</span></span>  
  
```idl
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a><span data-ttu-id="c799c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c799c-116">Requirements</span></span>  

 <span data-ttu-id="c799c-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c799c-117">**Header:** Cor.h</span></span>
