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
ms.openlocfilehash: a2cb45ea6ed5c5795c910b2f6c3575b12f8189cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-deterministic"></a>-belirleyici

Bayt için bayt çıktısı, aynı girişleri için derlemeleri arasında aynı olan bir derleme üretmek derleyici neden olur. 

## <a name="syntax"></a>Sözdizimi

```
-deterministic
```

## <a name="remarks"></a>Açıklamalar

Bir zaman damgası ve rastgele sayı oluşturulmuş bir GUID derleyici ekler beri varsayılan olarak, belirli bir giriş kümesini Derleyici çıktısı benzersizdir. Kullandığınız `-deterministic` üretmek için seçeneği bir *belirleyici derleme*, bir giriş aynı kaldığı sürece ikili içerikleri derlemeleri arasında aynı olan.

Derleyici determinism amacıyla aşağıdaki girişleri göz önünde bulundurur:

- Komut satırı parametreleri dizisi.
- Derleyicinin .rsp yanıt dosyasının içeriği.
- Kullanılan derleyici'nın tam sürümünü ve başvurulan derlemeler.
- Geçerli dizin yolu.
- Tüm dosyalar ikili içeriğini açıkça derleyiciye doğrudan veya dolaylı olarak dahil olmak üzere geçirildi:
    - Kaynak dosyaları
    - Başvurulan derlemeler
    - Başvurulan modül
    - Kaynaklar
    - Güçlü ad anahtar dosyası
    - @ yanıt dosyaları
    - Çözümleyiciler
    - Rulesets
    - Çözümleyicileri tarafından kullanılan ek dosyalar
- Geçerli kültür (hangi tanılama ve özel durum iletileri üretilen dilin).
- Varsayılan kodlama (veya geçerli kod sayfası) kodlama belirtilmediği takdirde.
- Varlığı, varlığı olmayan ve derleyicinin arama yolları dosyaların içeriğini (örneğin, tarafından belirtilen `/lib` veya `/recurse`).
- CLR platform derleyici çalıştırılır.
- Değeri `%LIBPATH%`, Çözümleyicisi bağımlılık yükleniyor etkileyebilir.

Kaynakları genel kullanıma açık olduğunda belirleyici derleme güvenilir bir kaynaktan bir ikili derlenmiş olup olmadığını kurmak için kullanılabilir. Ayrıca bir sürekli yapı sistemindeki bir ikili değişiklikler bağımlı derleme adımları yürütülebilir gerekip gerekmediğini belirlemek için yararlı olabilir. 

## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
