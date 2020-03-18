---
title: -deterministic (C# Derleyici Seçenekleri)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
ms.openlocfilehash: ed5d1db4618649391f88affad67e62dd9fc95925
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73455177"
---
# <a name="-deterministic"></a>-deterministic

Derleyicinin, bayt için bayt çıktısı aynı girişler için derlemeler arasında aynı olan bir derleme oluşturmasına neden olur.

## <a name="syntax"></a>Sözdizimi

```console
-deterministic
```

## <a name="remarks"></a>Açıklamalar

Derleyici rasgele sayılardan oluşturulan bir zaman damgası ve GUID eklediğiiçin, varsayılan olarak, belirli bir giriş kümesinden derleyici çıktısı benzersizdir. Giriş aynı `-deterministic` kaldığı sürece ikili içeriği derlemeler arasında aynı olan *deterministik*bir derleme oluşturmak için bu seçeneği kullanırsınız.

Derleyici determinizm amacıyla aşağıdaki girdileri dikkate alır:

- Komut satırı parametrelerinin sırası.
- Derleyicinin .rsp yanıt dosyasının içeriği.
- Derleyicinin kullanılan kesin sürümü ve başvurulan derlemeleri.
- Geçerli dizin yolu.
- Aşağıdakiler dahil olmak üzere, tüm dosyaların ikili içeriği doğrudan veya dolaylı olarak derleyiciye açıkça iletilir:
  - Kaynak dosyaları
  - Başvurulan derlemeler
  - Başvurulan modüller
  - Kaynaklar
  - Güçlü ad anahtarı dosyası
  - @ yanıt dosyaları
  - Çözümleyiciler
  - Kural kümeleri
  - Çözümleyiciler tarafından kullanılabilecek ek dosyalar
- Geçerli kültür (tanılama ve özel durum iletilerinin üretildiği dil için).
- Kodlama belirtilmemişse varsayılan kodlama (veya geçerli kod sayfası).
- Derleyicinin arama yollarında dosyaların varlığı, varlığı ve içeriği (örneğin, tarafından `-lib` veya `-recurse`tarafından belirtilir).
- Derleyicinin çalıştırıldığı CLR platformu.
- Çözümleyici `%LIBPATH%`bağımlılık yüklemesini etkileyebilecek değeri.

Kaynaklar genel kullanıma sunulduğunda, ikilinin güvenilir bir kaynaktan derlenip derlenmediğini belirlemek için deterministik derleme kullanılabilir. Ayrıca, ikili gereksinimdeki değişikliklere bağlı olan yapı adımlarının yürütülmesi gerekip gerekmediğini belirlemek için sürekli bir yapı sisteminde de yararlı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
