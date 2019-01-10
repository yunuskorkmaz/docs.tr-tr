---
title: '&lt;useLegacyJit&gt; öğesi'
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd4f9728338ecc66f84fe42b9bdbda9938ed518b
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612198"
---
# <a name="ltuselegacyjitgt-element"></a>&lt;useLegacyJit&gt; öğesi

Ortak dil çalışma zamanı için tam zamanında derleme eski 64 bit JIT Derleyici kullanıp kullanmadığını belirler.  
  
\<Yapılandırma >  
\<çalışma zamanı >  
\<useLegacyJit >
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
<useLegacyJit enabled=0|1 />
```

Öğe adı `useLegacyJit` büyük küçük harfe duyarlıdır.
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
| Öznitelik | Açıklama                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | Gerekli öznitelik.<br><br>Çalışma zamanının eski 64 bit JIT Derleyici kullanıp kullanmayacağını belirtir. |  
  
### <a name="enabled-attribute"></a>Etkin öznitelik  
  
| Değer | Açıklama                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| 0     | Ortak dil çalışma zamanı, .NET Framework 4.6 ve sonraki sürümlerinde eklenen yeni 64 bit JIT Derleyici kullanır. |  
| 1.     | Ortak dil çalışma zamanı, eski 64 bit JIT Derleyici kullanır.                                                     |  
  
### <a name="child-elements"></a>Alt öğeleri

Yok.
  
### <a name="parent-elements"></a>Üst öğeler  
  
| Öğe         | Açıklama                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |  
| `runtime`       | Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.                                                        |  
  
## <a name="remarks"></a>Açıklamalar  

.NET Framework 4. 6 ile başlayarak, ortak dil çalışma zamanı yeni bir 64 bit Derleyici tam zamanında (JIT) derleme için varsayılan olarak kullanır. Bazı durumlarda, bu bir davranışı fark JIT olarak derlenmiş önceki sürümü 64 bit JIT Derleyici tarafından uygulama kodu neden olabilir. Ayarlayarak `enabled` özniteliği `<useLegacyJit>` öğesine `1`, yeni 64 bit JIT Derleyici devre dışı bırakabilir ve bunun yerine eski 64 bit JIT Derleyici kullanarak uygulamanızı derleyin.  
  
> [!NOTE]
> `<useLegacyJit>` Öğesi, yalnızca 64 bit JIT derlemesi etkiler. 32-bit JIT Derleyici ile derleme etkilenmez.  
  
Yapılandırma dosyası ayarı kullanmak yerine, eski 64 bit JIT Derleyici iki yolla etkinleştirebilirsiniz:  
  
- Bir ortam değişkenini ayarlayarak

  Ayarlama `COMPLUS_useLegacyJit` ortam değişkenine ya da `0` (yeni 64 bit JIT Derleyici kullanın) veya `1` (eski 64 bit JIT Derleyici kullanın):
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  Ortam değişkenini sahip *genel kapsam*, etkilediği anlamına tüm uygulamalar makine üzerinde çalıştırın. Ayarlanırsa, bu uygulama yapılandırma dosyası ayarı tarafından geçersiz kılınabilip kılınamadığını. Ortam değişkeni adı büyük küçük harfe duyarlı değil.
  
- Bir kayıt defteri anahtarı ekleme

  Eski 64 bit JIT Derleyici ekleyerek etkinleştirebilirsiniz bir `REG_DWORD` ya da değer `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` veya `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` kayıt defteri anahtarı. Değer adlı `useLegacyJit`. Değer 0 ise, yeni derleyici kullanılır. Değer 1 ise, eski 64 bit JIT Derleyici etkinleştirilir. Kayıt defteri değeri adı büyük küçük harfe duyarlı değil.
  
  Değerine eklemek `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` anahtarı makine üzerinde çalışan tüm uygulamaları etkiler. Değerine eklemek `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` anahtar geçerli kullanıcı tarafından çalıştırılan tüm uygulamaları etkiler. Bir makine ile birden çok kullanıcı hesabı yapılandırdıysanız, değeri de diğer kullanıcılar için kayıt defteri anahtarları için eklenene kadar yalnızca geçerli kullanıcı tarafından çalıştırılan uygulamaların etkilenir. Ekleme `<useLegacyJit>` öğesini bir yapılandırma dosyası için mevcut iseler kayıt defteri ayarları geçersiz kılar.  
  
## <a name="example"></a>Örnek  

Aşağıdaki yapılandırma dosyası, yeni 64 bit JIT Derleyici ile derleme devre dışı bırakır ve bunun yerine, eski 64 bit JIT Derleyici kullanır.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<çalışma zamanı > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)   
- [\<Yapılandırma > öğesi](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)   
- [Azaltma: Yeni 64 bit JIT Derleyici](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)
