---
title: ICorDebugSymbolProvider2::GetGenericDictionaryInfo yöntemi
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f171af8dbfa4e812711e95e5587b314753cd9350
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216827"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a>ICorDebugSymbolProvider2::GetGenericDictionaryInfo yöntemi
Genel bir sözlük harita alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetGenericDictionaryInfo(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppMemoryBuffer`  
 [out] Adresine bir işaretçi bir [Icordebugmemorybuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) genel bir sözlük harita içeren nesne. Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
 Eşleme, üst düzey iki bölümden oluşur:  
  
-   A [dizin](#Directory) bu dahil tüm sözlüklerin göreli sanal adreslerine (RVA) içeren.  
  
-   Bayt hizalı [yığın](#Heap) nesne oluşturmada bilgileri içeren. Son directory girişinin hemen sonra başlar.  
  
<a name="Directory"></a>   
## <a name="the-directory"></a>Dizin  
 Her giriş dizininde yığın içinde bir uzaklık başvuruyor; yani yığın başlangıç göre bir uzaklık değildir. Girişler değerini mutlaka benzersiz değil; birden çok dizin girdisi yığınındaki aynı uzaklık işaret edecek şekilde mümkündür.  
  
 Genel bir sözlük harita öğesinin dizin bölümü aşağıdaki yapıya sahiptir:  
  
-   İlk 4 baytı dictionary girişlerinin (diğer bir deyişle, sözlükteki göreli sanal adreslerine sayısı) sayısını içerir. Bu değer anılacaktır *N*. Yüksek bit ayarlanmışsa girişleri artan düzende göreli sanal adres göre sıralanır.  
  
-   *N* dizin girdisi izleyin. Her girişin iki 4 baytlık Segment 8 baytlık oluşur:  
  
    -   Bayt 0-3: RVA; sözlüğün göreli sanal adres.  
  
    -   4-7 baytlar: Uzaklık; yığın başlangıcını göre bir uzaklık.  
  
<a name="Heap"></a>   
## <a name="the-heap"></a>Yığın  
 Dizin boyutu + 4 akıştan uzunluğunu çıkararak göre bir akış okuyucusunu yığının boyutu hesaplanabilir. Diğer bir deyişle:  
  
```  
Heap Size = Stream.Length – (Directory Size + 4)  
```  
  
 dizin boyutu olduğu `N * 8`.  
  
 Yığındaki her örneklemesi bilgi öğesi için biçimi şu şekildedir:  
  
-   Bu örnek oluşturma bilgi öğesi sıkıştırılmış ECMA meta veri biçimi bayt uzunluğu. Değeri, bu uzunluğu bilgileri içermez.  
  
-   Genel örnek oluşturma türleri sayısı veya *T*, sıkıştırılmış ECMA meta veri biçiminde.  
  
-   *T* türlerini, her temsil ECMA türü imza biçiminde.  
  
 Her yığın öğe uzunluğu dahilini Basit Dizin bölümü yığın etkilemeden sıralama sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugSymbolProvider2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
