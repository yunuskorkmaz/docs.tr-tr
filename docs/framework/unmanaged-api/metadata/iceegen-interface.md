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
ms.openlocfilehash: 2c180a135608350b0feec3f419be98f4f428b186
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704519"
---
# <a name="iceegen-interface"></a>ICeeGen Arabirimi

Dinamik kod derleme için yöntemler sağlar.  
  
 Bu arabirim artık kullanılmıyor ve kullanılmamalıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[AddSectionReloc Yöntemi](iceegen-addsectionreloc-method.md)|Kullanımdan kalktı. Kod tabanına bir. reloc yönergesi ekler.|  
|[AllocateMethodBuffer Yöntemi](iceegen-allocatemethodbuffer-method.md)|Kullanımdan kalktı. Bir yöntem için belirtilen boyutun bir arabelleğini oluşturur ve yöntemin göreli sanal adresini alır.|  
|[ComputePointer Yöntemi](iceegen-computepointer-method.md)|Kullanımdan kalktı. Belirtilen kod bölümünün arabelleğini belirler.|  
|[EmitString Yöntemi](iceegen-emitstring-method.md)|Kullanımdan kalktı. Belirtilen dizeyi kod tabanına yayar.|  
|[GenerateCeeFile Yöntemi](iceegen-generateceefile-method.md)|Kullanımdan kalktı. Şu anda bu dosyaya yüklenmiş kod tabanını içeren bir kod tabanı dosyası oluşturur `ICeeGen` .|  
|[GenerateCeeMemoryImage Yöntemi](iceegen-generateceememoryimage-method.md)|Kullanımdan kalktı. Kod tabanı için bellekte bir görüntü oluşturur.|  
|[GetIlSection Yöntemi](iceegen-getilsection-method.md)|Kullanımdan kalktı. Belirtilen tanıtıcı tarafından başvurulan ara dil kodu tabanının bölümünü alır.|  
|[GetIMapTokenIface Yöntemi](iceegen-getimaptokeniface-method.md)|Kullanımdan kalktı. Belirtilen belirteç tarafından başvurulan arabirimi alır.|  
|[GetMethodBuffer Yöntemi](iceegen-getmethodbuffer-method.md)|Kullanımdan kalktı. Belirtilen göreli sanal adreste Yöntem için uygun boyutun bir arabelleğini alır.|  
|[GetSectionBlock Yöntemi](iceegen-getsectionblock-method.md)|Kullanımdan kalktı. Kod tabanının bir bölüm bloğunu alır.|  
|[GetSectionCreate Yöntemi](iceegen-getsectioncreate-method.md)|Kullanımdan kalktı. Belirtilen ad ve bayrak değerlerini kullanarak bir kod bölümü üretir ve alır.|  
|[GetSectionDataLen Yöntemi](iceegen-getsectiondatalen-method.md)|Kullanımdan kalktı. Belirtilen bölümün uzunluğunu alır.|  
|[GetString Yöntemi](iceegen-getstring-method.md)|Kullanımdan kalktı. Belirtilen göreli sanal adreste depolanan dizeyi alır.|  
|[GetStringSection Yöntemi](iceegen-getstringsection-method.md)|Kullanımdan kalktı. Belirtilen tanıtıcı tarafından başvurulan kod bölümünün dize gösterimini alır.|  
|[TruncateSection Yöntemi](iceegen-truncatesection-method.md)|Kullanımdan kalktı. Belirtilen uzunluğa göre belirtilen kod bölümünü keser.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](metadata-interfaces.md)
