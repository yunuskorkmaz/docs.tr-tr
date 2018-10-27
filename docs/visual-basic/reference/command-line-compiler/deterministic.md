---
title: -belirleyici
ms.date: 04/11/2018
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
ms.openlocfilehash: dde79ca9ce6e77102c05fce7c507784457af4a4b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187942"
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
[Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
[Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
