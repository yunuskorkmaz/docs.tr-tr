---
title: ICeeGen Arabirimi
ms.date: 03/30/2017
api_name:
- ICeeGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen
helpviewer_keywords:
- ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type:
- apiref
ms.openlocfilehash: ae3c372951de00b097d0a8437039a3a85bf3aabf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426157"
---
# <a name="iceegen-interface"></a>ICeeGen Arabirimi
Provides methods for dynamic code compilation.  
  
 This interface is obsolete and should not be used.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[AddSectionReloc Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|Kullanımdan kalktı. Adds a .reloc instruction to the code base.|  
|[AllocateMethodBuffer Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|Kullanımdan kalktı. Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.|  
|[ComputePointer Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|Kullanımdan kalktı. Determines the buffer for the specified code section.|  
|[EmitString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|Kullanımdan kalktı. Emits the specified string into the code base.|  
|[GenerateCeeFile Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|Kullanımdan kalktı. Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.|  
|[GenerateCeeMemoryImage Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|Kullanımdan kalktı. Generates an image in memory for the code base.|  
|[GetIlSection Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|Kullanımdan kalktı. Gets the section of the intermediate language code base referenced by the specified handle.|  
|[GetIMapTokenIface Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|Kullanımdan kalktı. Gets the interface referenced by the specified token.|  
|[GetMethodBuffer Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|Kullanımdan kalktı. Gets a buffer of the appropriate size for the method at the specified relative virtual address.|  
|[GetSectionBlock Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|Kullanımdan kalktı. Gets a section block of the code base.|  
|[GetSectionCreate Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|Kullanımdan kalktı. Generates and gets a code section using the specified name and flag values.|  
|[GetSectionDataLen Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|Kullanımdan kalktı. Gets the length of the specified section.|  
|[GetString Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|Kullanımdan kalktı. Gets the string stored at the specified relative virtual address.|  
|[GetStringSection Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|Kullanımdan kalktı. Gets a string representation of the code section referenced by the specified handle.|  
|[TruncateSection Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|Kullanımdan kalktı. Truncates the specified code section by the specified length.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
