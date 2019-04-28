---
title: -deterministic
ms.date: 04/11/2018
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
ms.openlocfilehash: 95c9add0521208ef04ff47c071a2e04abc968f27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648743"
---
# <a name="-deterministic"></a>-deterministic

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

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
