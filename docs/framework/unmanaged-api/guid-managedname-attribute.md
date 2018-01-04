---
title: "GUID_ManagedName Özniteliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GUID_ManagedName
api_location: alink.dll
api_type: COM
f1_keywords: GUID_ManagedName
helpviewer_keywords: GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 116a9e38b9885f0d0a5afc8f4915b9ce2b50f1dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="guidmanagedname-attribute"></a>GUID_ManagedName Özniteliği
Bir Bileşen Nesne Modeli (COM) kitaplığı için yönetilen ad alanı adı belirten bir özel arabirim özniteliği tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
#### <a name="parameters"></a>Parametreler  
 `value`  
 Kitaplık için yönetilen ad alanı adı.  
  
## <a name="definition"></a>Tanım  
 `GUID_ManagedName`içinde COR.h şu şekilde tanımlanır:  
  
```  
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Özel arabirim özniteliği bir nesne için meta veri türü Kitaplığı'nda tanımlar.  
  
 Kullanım <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> veya <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> özniteliğinden yönetilen adı alınamadı.  
  
 Daha fazla bilgi için bkz: [arabirim öznitelikleri](/cpp/windows/interface-attributes) Visual c++'ta başvuru belgelerini.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir kitaplık tanımı kullanılarak gösterir `GUID_ManagedName` özniteliği.  
  
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
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** Cor.h
