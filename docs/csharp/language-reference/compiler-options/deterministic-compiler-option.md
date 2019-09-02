---
title: -belirleyici (C# derleyici seçenekleri)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e77c14a1c3a4ba11b8ae6556be4f1c3c0cd42788
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202927"
---
# <a name="-deterministic"></a>-deterministic

Derleyicinin bayt çıkışı, aynı girişlerin derlemeleri arasında özdeş olan bir derleme üretmesine neden olur.

## <a name="syntax"></a>Sözdizimi

```console
-deterministic
```

## <a name="remarks"></a>Açıklamalar

Varsayılan olarak, belirli bir giriş kümesinden Derleyici çıktısı benzersizdir, çünkü derleyici bir zaman damgası ve rastgele sayıdan oluşturulan bir GUID ekliyor. Değer aynı kaldığı `-deterministic` sürece, bir *belirleyici derleme*oluşturmak için bu seçeneği kullanın.

Derleyici, belirlemeleri için aşağıdaki girişleri dikkate alır:

- Komut satırı parametrelerinin sırası.
- Derleyicinin. rsp yanıt dosyasının içeriği.
- Kullanılan derleyicinin kesin sürümü ve başvurulan derlemeleri.
- Geçerli dizin yolu.
- Açıkça derleyiciye doğrudan veya dolaylı olarak geçirilen tüm dosyaların ikili içeriği:
  - Kaynak dosyalar
  - Başvurulan derlemeler
  - Başvurulan modüller
  - Kaynaklar
  - Tanımlayıcı ad anahtar dosyası
  - @ Yanıt dosyaları
  - Çözümleyiciler
  - RuleSets
  - Çözümleyiciler tarafından kullanılabilecek ek dosyalar
- Geçerli kültür (tanılama ve özel durum iletilerinin oluşturulduğu dil için).
- Kodlama belirtilmemişse, varsayılan kodlama (veya geçerli kod sayfası).
- Derleyicinin arama yollarındaki dosyaların varlığı, var olmayan ve içeriği (örneğin, veya `/lib` `/recurse`ile).
- Derleyicinin çalıştırıldığı CLR platformu.
- `%LIBPATH%`, Çözümleyici bağımlılığı yüklemeyi etkileyebilecek değeri.

Kaynaklar herkese açık olduğunda, bir ikilinin güvenilir bir kaynaktan derlenip derlenmediğini oluşturmak için belirleyici derleme kullanılabilir. Ayrıca, bir ikiliye yapılan değişikliklere bağımlı derleme adımlarının yürütülmesi gerekip gerekmediğini belirlemek için sürekli bir derleme sisteminde de yararlı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
