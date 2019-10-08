---
title: -deterministic
ms.date: 04/11/2018
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
ms.openlocfilehash: 6a83b636dd83534788f3a38971e0fef2919314f5
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005632"
---
# <a name="-deterministic"></a>-deterministic

Derleyicinin bayt çıkışı, aynı girişlerin derlemeleri arasında özdeş olan bir derleme üretmesine neden olur.

## <a name="syntax"></a>Sözdizimi

```console
-deterministic
```

## <a name="remarks"></a>Açıklamalar

Varsayılan olarak, belirli bir giriş kümesinden Derleyici çıktısı benzersizdir, çünkü derleyici bir zaman damgası ve rastgele sayıdan oluşturulan bir GUID ekliyor. Değer aynı kaldığı sürece, bir *belirleyici derleme*oluşturmak için `-deterministic` seçeneğini kullanın.

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
- Derleyicinin arama yollarındaki dosyaların varlığı, var olmayan ve içeriği (örneğin, `/lib` veya `/recurse`).
- Derleyicinin çalıştırıldığı CLR platformu.
- Çözümleyici bağımlılığı yüklemeyi etkileyebilecek `%LIBPATH%` değeri.

Kaynaklar herkese açık olduğunda, bir ikilinin güvenilir bir kaynaktan derlenip derlenmediğini oluşturmak için belirleyici derleme kullanılabilir. Ayrıca, bir ikiliye yapılan değişikliklere bağımlı derleme adımlarının yürütülmesi gerekip gerekmediğini belirlemek için sürekli bir derleme sisteminde de yararlı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
