---
description: Çeşitli C# derleyici seçenekleri. Bu seçenekler derleyiciye genel seçenekler sağlar.
title: Diğer kategorilere sığmayan C# derleyici seçenekleri
ms.date: 03/12/2021
f1_keywords:
- cs.build.options
helpviewer_keywords:
- ResponseFiles compiler option [C#]
- NoLogo compiler option [C#]
- NoConfig compiler option [C#]
ms.openlocfilehash: ec7d9c3685c9acb5ca3cda28aca55abb26b836cf
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103482914"
---
# <a name="miscellaneous-c-compiler-options"></a>Çeşitli C# derleyici seçenekleri

Aşağıdaki seçenekler çeşitli derleyici davranışlarını denetler. Yeni MSBuild sözdizimi **kalın** olarak gösterilir. Eski *csc.exe* sözdizimi içinde gösterilir `code style` .

- **ResponseFiles**  /  `-@` : daha fazla seçenek için yanıt dosyasını okuyun.
-   /  Nologo `-nologo` : Derleyici telif hakkı iletisini bastır.
- **Noconfig**  /  `-noconfig` : *CSC. rsp* dosyasını otomatik olarak eklemeyin.

## <a name="responsefiles"></a>Yanıt dosyaları

**ResponseFiles** seçeneği, derlemek için derleyici seçeneklerini ve kaynak kodu dosyalarını içeren bir dosya belirtmenize olanak tanır.

```xml
<ResponseFiles>response_file</ResponseFiles>
```

, `response_file` Derlemek için derleyici seçeneklerini veya kaynak kodu dosyalarını listeleyen dosyayı belirtir. Derleyici seçenekleri ve kaynak kodu dosyaları, derleyici tarafından komut satırında belirtildikleri gibi işlenecek. Bir derlemede birden fazla yanıt dosyası belirtmek için, birden çok yanıt dosyası seçeneği belirtin. Bir yanıt dosyasında, bir satırda birden çok derleyici seçeneği ve kaynak kodu dosyası görünebilir. Tek bir derleyici seçenek belirtiminin tek bir satırda görünmesi gerekir (birden çok satıra yayılamaz). Yanıt dosyaları # simgesiyle başlayan açıklamalara sahip olabilir. Bir yanıt dosyası içinden derleyici seçeneklerinin belirtilmesi, komut satırında bu komutları verme gibidir. Derleyici, okunan komut seçeneklerini işler. Komut satırı bağımsız değişkenleri, yanıt dosyalarında daha önce listelenen seçenekleri geçersiz kılabilir. Buna karşılık, bir yanıt dosyasındaki seçenekler, önceden komut satırında veya diğer yanıt dosyalarında listelenen seçenekleri geçersiz kılar. C#, csc.exe dosyası ile aynı dizinde bulunan CSC. rsp dosyasını sağlar. Yanıt dosyası biçimi hakkında daha fazla bilgi için bkz. [**noconfig**](#noconfig). Bu derleyici seçeneği Visual Studio geliştirme ortamında ayarlanamaz veya program aracılığıyla değiştirilemez. Örnek yanıt dosyasından birkaç satır aşağıda verilmiştir:

```console
# build the first output file
-target:exe -out:MyExe.exe source1.cs source2.cs
```

## <a name="nologo"></a>NoLogo

**Nologo** seçeneği, derleyici başlatıldığında ve derleme sırasında bilgilendirici iletileri görüntülerken oturum açma başlığının görüntülenmesini önler.

```xml
<NoLogo>true</NoLogo>
```

## <a name="noconfig"></a>NoConfig

**Noconfig** seçeneği derleyicinin *CSC. rsp* dosyasıyla derlenmeyeceğini söyler.

```xml
<NoConfig>true</NoConfig>
```

*CSC. rsp* dosyası .NET Framework ile gönderilen tüm derlemelere başvurur. Visual Studio .NET geliştirme ortamının içerdiği gerçek başvurular proje türüne bağlıdır. *CSC. rsp* dosyasını değiştirebilir ve her derlemede dahil edilecek ek derleyici seçeneklerini belirtebilirsiniz. Derleyicinin *CSC. rsp* dosyasındaki ayarları araması ve kullanması Istemiyorsanız, **noconfig**' i belirtin. Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.
