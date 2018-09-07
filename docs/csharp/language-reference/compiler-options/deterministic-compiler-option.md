---
title: -belirleyici (C# Derleyici Seçenekleri)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f9aca20a3ff65d061c04a21e31db3fb5eab62ba
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44099223"
---
# <a name="-deterministic"></a>-belirleyici

Bayt için çıktısı, aynı girişleri için derlemeler arasında özdeş bir derleme oluşturmak derleyicinin neden olur. 

## <a name="syntax"></a>Sözdizimi

```
-deterministic
```

## <a name="remarks"></a>Açıklamalar

Derleyici bir zaman damgası ve rastgele sayı oluşturulan bir GUID ekler olduğundan varsayılan olarak, belirli bir giriş kümesini derleyici çıktısını benzersizdir. Kullandığınız `-deterministic` üretmek için seçeneği bir *belirlenimci derlemeyi*, bir giriş aynı kaldığı sürece ikili içeriğe sahip derlemeler arasında aynı.

Derleyici, aşağıdaki girişleri gerekircilik amacıyla göz önünde bulundurur:

- Komut satırı parametreleri dizisi.
- Derleyicinin .rsp yanıt dosyasının içeriği.
- Kullanılan derleme kesin sürümünü ve onun başvurulmuş derlemeler.
- Geçerli dizin yolu.
- Tüm dosyaları ikili içeriğini açıkça derleyici doğrudan veya dolaylı olarak dahil olmak üzere geçirilen:
    - Kaynak dosyaları
    - Başvurulan derlemeler
    - Başvurulan modül
    - Kaynaklar
    - Tanımlayıcı ad anahtar dosyası
    - @ yanıt dosyaları
    - Çözümleyiciler
    - Rulesets
    - Çözümleyiciler tarafından kullanılan ek dosyalar
- Geçerli kültür (hangi tanılama ve özel durum iletileri üretilir dilin).
- Varsayılan kodlama (veya mevcut kod sayfasında) kodlama belirtilmezse.
- Varlığı, var olmayan ve derleyicinin arama yolları dosya içeriklerini (örneğin, tarafından belirtilen `/lib` veya `/recurse`).
- Derleyici çalıştığı CLR platform.
- Değerini `%LIBPATH%`, çözümleyici bağımlılık yükleniyor etkileyebilir.

Kaynakları genel kullanıma açık olduğunda, belirlenimci derlemeyi güvenilir bir kaynaktan bir ikili derlenmiş olup olmadığını kurmak için kullanılabilir. Ayrıca bir ikili değişiklikleri bağımlı derleme adımları yürütülecek gerekip gerekmediğini belirlemek için bir sürekli derleme sistemi de yararlı olabilir. 

## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
