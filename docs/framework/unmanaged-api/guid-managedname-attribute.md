---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bae50f695de81856d4fddcb2af3d1188d896642
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430017"
---
# <a name="guidmanagedname-attribute"></a><span data-ttu-id="c9b5d-102">GUID_ManagedName Özniteliği</span><span class="sxs-lookup"><span data-stu-id="c9b5d-102">GUID_ManagedName Attribute</span></span>
<span data-ttu-id="c9b5d-103">Bir Bileşen Nesne Modeli (COM) kitaplığı için yönetilen ad alanı adı belirten bir özel arabirim özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9b5d-103">Defines a custom interface attribute that specifies the managed namespace name for a component object model (COM) library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9b5d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9b5d-104">Syntax</span></span>  
  
```  
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9b5d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c9b5d-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="c9b5d-106">Kitaplık için yönetilen ad alanı adı.</span><span class="sxs-lookup"><span data-stu-id="c9b5d-106">The managed namespace name for the library.</span></span>  
  
## <a name="definition"></a><span data-ttu-id="c9b5d-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="c9b5d-107">Definition</span></span>  
 <span data-ttu-id="c9b5d-108">`GUID_ManagedName` içinde COR.h şu şekilde tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="c9b5d-108">`GUID_ManagedName` is defined in Cor.h as follows:</span></span>  
  
```  
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a><span data-ttu-id="c9b5d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9b5d-109">Remarks</span></span>  
 <span data-ttu-id="c9b5d-110">Özel arabirim özniteliği bir nesne için meta veri türü Kitaplığı'nda tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9b5d-110">A custom interface attribute defines metadata for an object in the type library.</span></span>  
  
 <span data-ttu-id="c9b5d-111">Kullanım <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> veya <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> özniteliğinden yönetilen adı alınamadı.</span><span class="sxs-lookup"><span data-stu-id="c9b5d-111">Use <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> to retrieve the managed name from the attribute.</span></span>  
  
 <span data-ttu-id="c9b5d-112">Daha fazla bilgi için bkz: [arabirim öznitelikleri](/cpp/windows/interface-attributes) Visual c++'ta başvuru belgelerini.</span><span class="sxs-lookup"><span data-stu-id="c9b5d-112">For more information, see [Interface Attributes](/cpp/windows/interface-attributes) in the Visual C++ reference documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9b5d-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9b5d-113">Example</span></span>  
 <span data-ttu-id="c9b5d-114">Aşağıdaki örnek, bir kitaplık tanımı kullanılarak gösterir `GUID_ManagedName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c9b5d-114">The following example shows a library definition using the `GUID_ManagedName` attribute.</span></span>  
  
```  
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a><span data-ttu-id="c9b5d-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9b5d-115">Requirements</span></span>  
 <span data-ttu-id="c9b5d-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c9b5d-116">**Header:** Cor.h</span></span>
