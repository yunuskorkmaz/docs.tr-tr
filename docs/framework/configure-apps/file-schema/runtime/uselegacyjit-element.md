---
title: <useLegacyJit> Öğesi
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
ms.openlocfilehash: 47aacb629dc234d9aeaab1ef6e6844fbbe5dbfdb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115102"
---
# <a name="uselegacyjit-element"></a>\<useLegacyJit > öğesi

Ortak dil çalışma zamanının, Just-In-Time derlemesi için eski 64-bit JıT derleyicisini kullanıp kullanmadığını belirler.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<useLegacyJit >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
<useLegacyJit enabled=0|1 />
```

`useLegacyJit` öğe adı, büyük/küçük harfe duyarlıdır.
  
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

.NET Framework 4,6 ' den başlayarak, ortak dil çalışma zamanı, varsayılan olarak tam zamanında (JıT) derleme için yeni bir 64 bit derleyicisi kullanır. Bazı durumlarda bu durum, 64 bit JıT derleyicisi 'nin önceki sürümü tarafından derlenen uygulama kodundan kaynaklanan bir farklılık oluşmasına neden olabilir. `<useLegacyJit>` öğesinin `enabled` özniteliğini `1`olarak ayarlayarak, yeni 64 bit JıT derleyicisini devre dışı bırakabilir ve bunun yerine eski 64 bit JıT derleyicisini kullanarak uygulamanızı derleyebilirsiniz.  
  
> [!NOTE]
> `<useLegacyJit>` öğesi yalnızca 64 bitlik JıT derlemesini etkiler. 32 bit JıT derleyicisi ile derleme etkilenmemiştir.  
  
Yapılandırma dosyası ayarı kullanmak yerine, eski 64 bit JıT derleyicisini iki farklı şekilde etkinleştirebilirsiniz:  
  
- Ortam değişkenini ayarlama

  `COMPLUS_useLegacyJit` ortam değişkenini `0` (yeni 64-bit JıT derleyicisini kullanın) veya `1` (eski 64 bit JıT derleyicisini kullanın) olarak ayarlayın:
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  Ortam değişkeni *genel kapsama*sahiptir, yani makinede çalıştırılan tüm uygulamaları etkiler. Ayarlanırsa, uygulama yapılandırma dosyası ayarı tarafından geçersiz kılınabilir. Ortam değişkeni adı büyük/küçük harfe duyarlı değildir.
  
- Kayıt defteri anahtarı ekleme

  Kayıt defterindeki `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` veya `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` anahtarına `REG_DWORD` bir değer ekleyerek eski 64 bit JıT derleyicisini etkinleştirebilirsiniz. Değer `useLegacyJit`olarak adlandırılır. Değer 0 ise, yeni derleyici kullanılır. Değer 1 ise, eski 64 bit JıT derleyicisi etkinleştirilir. Kayıt defteri değer adı büyük/küçük harfe duyarlı değildir.
  
  `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` anahtarına değer eklemek, makinede çalışan tüm uygulamaları etkiler. `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` anahtarına değer eklemek, geçerli kullanıcı tarafından çalıştırılan tüm uygulamaları etkiler. Bir makine birden çok kullanıcı hesabıyla yapılandırıldıysa, değer diğer kullanıcılar için de kayıt defteri anahtarlarına eklenmediği sürece yalnızca geçerli kullanıcı tarafından çalıştırılan uygulamalar etkilenir. Bir yapılandırma dosyasına `<useLegacyJit>` öğesi eklemek, varsa kayıt defteri ayarlarını geçersiz kılar.  
  
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

- [\<Runtime > öğesi](runtime-element.md)
- [\<Yapılandırma > öğesi](../configuration-element.md)
- [Risk azaltma: yeni 64-bit JıT derleyicisi](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
