---
title: -deterministic
ms.date: 04/11/2018
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
ms.openlocfilehash: 9b611a72656bdd570eccec8a0585bf5ce6fa55f6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716787"
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
- Derleyicinin arama yollarındaki dosyaların varlığı, var olmayan ve içeriği (örneğin, veya `-lib` `-recurse`ile).
- Derleyicinin çalıştırıldığı CLR platformu.
- `%LIBPATH%`, Çözümleyici bağımlılığı yüklemeyi etkileyebilecek değeri.

Kaynaklar herkese açık olduğunda, bir ikilinin güvenilir bir kaynaktan derlenip derlenmediğini oluşturmak için belirleyici derleme kullanılabilir. Ayrıca, bir ikiliye yapılan değişikliklere bağımlı derleme adımlarının yürütülmesi gerekip gerekmediğini belirlemek için sürekli bir derleme sisteminde de yararlı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
