---
title: <useLegacyJit> Öğesi
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d79479d1836963fcbdaaf8d40bfc3648b88c4a3
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663406"
---
# <a name="uselegacyjit-element"></a>\<useLegacyJit > öğesi

Ortak dil çalışma zamanının, Just-In-Time derlemesi için eski 64-bit JıT derleyicisini kullanıp kullanmadığını belirler.  
  
\<Yapılandırma >  
\<çalışma zamanı >  
\<useLegacyJit >
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
<useLegacyJit enabled=0|1 />
```

Öğe adı `useLegacyJit` büyük/küçük harfe duyarlıdır.
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
| Öznitelik | Açıklama                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | Gerekli öznitelik.<br><br>Çalışma zamanının eski 64-bit JıT derleyicisini kullanıp kullanmadığını belirtir. |  
  
### <a name="enabled-attribute"></a>enabled özniteliği  
  
| Değer | Açıklama                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| 0     | Ortak dil çalışma zamanı, .NET Framework 4,6 ve sonraki sürümlerde bulunan yeni 64-bit JıT derleyicisini kullanır. |  
| 1\.     | Ortak dil çalışma zamanı, eski 64 bit JıT derleyicisini kullanır.                                                     |  
  
### <a name="child-elements"></a>Alt öğeleri

Yok.
  
### <a name="parent-elements"></a>Üst öğeler  
  
| Öğe         | Açıklama                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |  
| `runtime`       | Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.                                                        |  
  
## <a name="remarks"></a>Açıklamalar  

.NET Framework 4,6 ' den başlayarak, ortak dil çalışma zamanı, varsayılan olarak tam zamanında (JıT) derleme için yeni bir 64 bit derleyicisi kullanır. Bazı durumlarda bu durum, 64 bit JıT derleyicisi 'nin önceki sürümü tarafından derlenen uygulama kodundan kaynaklanan bir farklılık oluşmasına neden olabilir. `enabled` Öğesinin özniteliğini olarak`1`ayarlayarak, yeni 64-bit JIT derleyicisini devre dışı bırakabilir ve bunun yerine eski 64 bit JIT derleyicisini kullanarak `<useLegacyJit>` uygulamanızı derleyebilirsiniz.  
  
> [!NOTE]
> `<useLegacyJit>` Öğesi yalnızca 64 bitlik JIT derlemesini etkiler. 32 bit JıT derleyicisi ile derleme etkilenmemiştir.  
  
Yapılandırma dosyası ayarı kullanmak yerine, eski 64 bit JıT derleyicisini iki farklı şekilde etkinleştirebilirsiniz:  
  
- Ortam değişkenini ayarlama

  Ortam değişkenini ya `0` (yeni 64-bit JIT derleyicisini kullanın) veya `1` (eski 64 bit JIT derleyicisini kullanın) olarak ayarlayın: `COMPLUS_useLegacyJit`
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  Ortam değişkeni *genel kapsama*sahiptir, yani makinede çalıştırılan tüm uygulamaları etkiler. Ayarlanırsa, uygulama yapılandırma dosyası ayarı tarafından geçersiz kılınabilir. Ortam değişkeni adı büyük/küçük harfe duyarlı değildir.
  
- Kayıt defteri anahtarı ekleme

  Kayıt defterindeki `REG_DWORD` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` veya anahtarınabirdeğerekleyerekeski64bitJITderleyicisinietkinleştirebilirsiniz.`HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` Değer olarak adlandırılır `useLegacyJit`. Değer 0 ise, yeni derleyici kullanılır. Değer 1 ise, eski 64 bit JıT derleyicisi etkinleştirilir. Kayıt defteri değer adı büyük/küçük harfe duyarlı değildir.
  
  Değeri `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` anahtara eklemek, makinede çalışan tüm uygulamaları etkiler. Değeri `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` anahtara eklemek, geçerli kullanıcı tarafından çalıştırılan tüm uygulamaları etkiler. Bir makine birden çok kullanıcı hesabıyla yapılandırıldıysa, değer diğer kullanıcılar için de kayıt defteri anahtarlarına eklenmediği sürece yalnızca geçerli kullanıcı tarafından çalıştırılan uygulamalar etkilenir. `<useLegacyJit>` Öğesini bir yapılandırma dosyasına eklemek, varsa kayıt defteri ayarlarını geçersiz kılar.  
  
## <a name="example"></a>Örnek  

Aşağıdaki yapılandırma dosyası, derlemeyi yeni 64-bit JıT derleyicisi ile devre dışı bırakır ve bunun yerine eski 64 bit JıT derleyicisini kullanır.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<çalışma zamanı > öğesi](runtime-element.md)
- [\<Yapılandırma > öğesi](../configuration-element.md)
- [Mayı Yeni 64-bit JıT derleyicisi](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
