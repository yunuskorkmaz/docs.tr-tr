---
title: "ICorDebugSymbolProvider2::GetGenericDictionaryInfo yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63126e4f34ea7ea7dee7dd0b9cae0dc0fea57ed9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a>ICorDebugSymbolProvider2::GetGenericDictionaryInfo yöntemi
Genel bir sözlük harita alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetGenericDictionaryInfo(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppMemoryBuffer`  
 [out] Adresine bir işaretçi bir [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) genel sözlük eşleme içeren nesne. Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET yerel ile kullanılabilir.  
  
 Harita en üst düzey iki bölümden oluşur:  
  
-   A [directory](#Directory) bu eşlemesinde dahil tüm sözlükleri, göreli sanal adresleri (RAV) içeren.  
  
-   Bayt hizalı [yığın](#Heap) nesne örneğini oluşturmada bilgileri içerir. Son dizin girişinin hemen sonra başlar.  
  
<a name="Directory"></a>   
## <a name="the-directory"></a>Dizini  
 Her giriş dizininde öbek içinde uzaklığı gösterir; diğer bir deyişle, öbek başlangıç göreli bir uzaklık dayalıdır. Girişler değeri mutlaka benzersiz değil; aynı uzaklık yığınındaki işaret etmek birden çok dizin girdisi mümkündür.  
  
 Genel bir sözlük harita dizin bölümü aşağıdaki yapıya sahiptir:  
  
-   İlk 4 bayt dictionary girişlerinin (diğer bir deyişle, göreli sanal adresleri sözlükteki sayısı) sayısını içerir. Bu değere başvurur *N*. Yüksek bit ayarlanmışsa girişleri artan düzende göreli sanal adres göre sıralanır.  
  
-   *N* dizin girişlerini izleyin. Her giriş iki 4 baytlık kesimi 8 bayt oluşur:  
  
    -   Bayt 0-3: RVA; sözlüğün göreli sanal adres.  
  
    -   Bayt 4-7: uzaklığı; Öbek başlangıcı göre uzaklığı.  
  
<a name="Heap"></a>   
## <a name="the-heap"></a>Öbek  
 Yığın 's boyutu dizin boyutu + 4 akış uzunluğu çıkarılmasıyla akış okuyucu tarafından hesaplanabilir. Diğer bir deyişle:  
  
```  
Heap Size = Stream.Length – (Directory Size + 4)  
```  
  
 dizin boyutu olduğu `N * 8`.  
  
 Her örneklemesi bilgi öğesi yığında biçimdedir:  
  
-   Bu örnek oluşturma bilgi öğesi sıkıştırılmış ECMA meta veri biçimi bayt cinsinden uzunluğu. Değer bu uzunluğu bilgileri dışlar.  
  
-   Genel olgu türlerinin sayısı veya *T*, sıkıştırılmış ECMA meta veri biçiminde.  
  
-   *T* türleri, her temsil ECMA türü imza biçiminde.  
  
 Her yığın öğesi için uzunluk eklenmesi, Basit Dizin bölümü öbek etkilemeden sıralama sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugSymbolProvider2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
