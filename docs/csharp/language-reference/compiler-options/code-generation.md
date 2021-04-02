---
description: Kod oluşturmayı denetlemek için C# derleyici seçenekleri. Seçenekler, belirtilen derleme için derleyici tarafından oluşturulan kodu etkiler.
title: C# derleyici seçenekleri-kod oluşturma seçenekleri
ms.date: 03/12/2021
f1_keywords:
- cs.build.options
helpviewer_keywords:
- DebugType compiler option [C#]
- Optimize compiler option [C#]
- Deterministic compiler option [C#]
- ProduceOnlyReferenceAssembly compiler option [C#]
ms.openlocfilehash: 02610c9d0142643bdb553f8b8177d1a4a2237717
ms.sourcegitcommit: 652f62fc8f3ab6a264681b6eb5211ac7539bd115
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105964799"
---
# <a name="c-compiler-options-that-control-code-generation"></a>Kod oluşturmayı denetleyen C# derleyici seçenekleri

Aşağıdaki seçenekler derleyici tarafından kod oluşturmayı denetler. Yeni MSBuild sözdizimi **kalın** olarak gösterilir. Eski *csc.exe* sözdizimi içinde gösterilir `code style` .

- **DEBUGTYPE**  /  `-debug` : hata ayıklama bilgilerini yayma (veya yayma).
- **Optimize**  /  `-optimize` : iyileştirmeleri etkinleştir.
- **Belirleyici**  /  `-deterministic` : aynı giriş kaynağından bayt için bayt eşdeğeri çıkış üretir.
- **ProduceOnlyReferenceAssembly**  /  `-refonly` : birincil çıkış olarak tam derleme yerine bir başvuru derlemesi üretin.

## <a name="debugtype"></a>DebugType

**DEBUGTYPE** seçeneği derleyicinin hata ayıklama bilgileri oluşturmasına ve bunu çıkış dosyasına veya dosyalarına yerleştirmesine neden olur. *Hata ayıklama oluşturma yapılandırması* için varsayılan olarak hata ayıklama bilgileri eklenir. *Yayın* derleme yapılandırması için varsayılan olarak kapalıdır.

```xml
<DebugType>pdbonly</DebugType>
```

C# 6,0 ile başlayan tüm derleyici sürümleri için, *pdbonly* ve *Full* arasında bir fark yoktur. *Yalnızca pdbonly* öğesini seçin. *. Pdb* dosyasının konumunu değiştirmek için bkz. [**pdbdosya**](./advanced.md#pdbfile).

Aşağıdaki değerler geçerlidir:

| Değer      | Anlamı                                                                                                 |
|------------|---------------------------------------------------------------------------------------------------------|
| `full`     | Geçerli platform için varsayılan biçimi kullanarak hata ayıklama bilgilerini _. pdb_ dosyasına yay:<br>**Windows**: bir Windows pdb dosyası. <br>**Linux/macOS**: [taşınabilir bir PDB](https://github.com/dotnet/core/blob/main/Documentation/diagnostics/portable_pdb.md) dosyası. |
| `pdbonly`  | Aynı `full` . Daha fazla bilgi için aşağıdaki nota bakın. |
| `portable` | Platformlar arası [TAŞINABILIR pdb](https://github.com/dotnet/core/blob/main/Documentation/diagnostics/portable_pdb.md) biçimini kullanarak hata ayıklama bilgilerini. pdb dosyasına yayma. |
| `embedded` | Hata ayıklama bilgilerini [TAŞINABILIR pdb](https://github.com/dotnet/core/blob/main/Documentation/diagnostics/portable_pdb.md) biçimi kullanılarak _. dll/. exe_ ' ye (_. pdb_ dosyası üretilmez) yayma. |

> [!IMPORTANT]
> Aşağıdaki bilgiler yalnızca C# 6,0 ' den eski derleyiciler için geçerlidir.
> Bu öğenin değeri ya da olabilir `full` `pdbonly` . *Yalnızca pdbbelirtmezseniz* geçerli olan *tam* bağımsız değişken, çalışan programa bir hata ayıklayıcı eklemeye olanak sağlar. Yalnızca program hata ayıklayıcıda başlatıldığında, *pdbyalnızca* kaynak kodu hata ayıklamasına izin verir, ancak çalışan program hata ayıklayıcıya eklendiğinde yalnızca assembler görüntülenir. Hata ayıklama derlemeleri oluşturmak için bu seçeneği kullanın. *Tam*' ı KULLANıRSANıZ, JIT ile iyileştirilmiş kodun hız ve boyutunu ve *tam* olarak kod kalitesiyle ilgili küçük bir etkisi olduğunu unutmayın. Yayın kodu oluşturmak için *yalnızca pdbonly* veya pdb yok önerilir. *Yalnızca pdbonly* ve *Full* arasındaki bir *fark, derleyicinin* <xref:System.Diagnostics.DebuggableAttribute> hata ayıklama bilgilerinin kullanılabilir olduğunu JIT derleyicisine bildirmek için kullanılan bir ' ın yayar. Bu nedenle, tam ' ı <xref:System.Diagnostics.DebuggableAttribute> kullanırsanız kodunuzun yanlış olarak ayarla ' yı içermesi halinde bir hata alırsınız . Bir uygulamanın hata ayıklama performansını yapılandırma hakkında daha fazla bilgi için bkz. [bir görüntüyü hata ayıklamayı kolaylaştırın](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).

## <a name="optimize"></a>İyileştirme

**İyileştirme** seçeneği, çıkış dosyanızı daha küçük, daha hızlı ve daha verimli hale getirmek için derleyici tarafından gerçekleştirilen iyileştirmeleri sağlar veya devre dışı bırakır. *En iyileştirme* seçeneği, *yayın* derleme yapılandırması için varsayılan olarak etkindir. *Hata ayıklama* oluşturma yapılandırması için varsayılan olarak kapalıdır.

```xml
<Optimize>true</Optimize>
```

Visual Studio 'da projeniz için **derleme** Özellikleri sayfasından **en iyileştirme** seçeneğini ayarlarsınız.

**Optimizasyon** , ortak dil çalışma zamanına kodu çalışma zamanında iyileştirmek için de bildirir. Varsayılan olarak, iyileştirmeler devre dışıdır. İyileştirmeleri etkinleştirmek için **optimize et +** ' i belirtin. Bir derleme tarafından kullanılacak bir modül oluştururken, derleme tarafından kullanılan **en iyileştirme** ayarlarını kullanın. **En iyileştirme** ve [**hata ayıklama**](#debugtype) seçeneklerini birleştirmek mümkündür.

## <a name="deterministic"></a>Belirlenimci

Derleyicinin bayt çıkışı, aynı girişlerin derlemeleri arasında özdeş olan bir derleme üretmesine neden olur.

```xml
<Deterministic>true</Deterministic>
```

Varsayılan olarak, belirli bir giriş kümesinden Derleyici çıktısı benzersizdir, çünkü derleyici bir zaman damgası ve rastgele sayıdan oluşturulan bir MVıD ekliyor. `<Deterministic>`Değer aynı kaldığı sürece, bir *belirleyici derleme* oluşturmak için bu seçeneği kullanın. Böyle bir derlemede, zaman damgası ve MVıD alanları, tüm derleme girişlerinin bir karmasından türetilen değerlerle birlikte değişir. Derleyici, determinronizi etkileyen aşağıdaki girişleri dikkate alır:

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
  - Çözümleyiciler tarafından kullanılabilecek diğer dosyalar
- Geçerli kültür (tanılama ve özel durum iletilerinin oluşturulduğu dil için).
- Kodlama belirtilmemişse varsayılan kodlama (veya geçerli kod sayfası).
- Derleyicinin arama yollarındaki dosyaların varlığı, var olmayan ve içeriği (örneğin, `-lib` veya ile `-recurse` ).
- Derleyicinin çalıştırıldığı ortak dil çalışma zamanı (CLR) platformu.
- `%LIBPATH%`, Çözümleyici bağımlılığı yüklemeyi etkileyebilecek değeri.

Belirleyici derleme, bir ikilinin güvenilir bir kaynaktan derlenip derlenmediğini oluşturmak için kullanılabilir. Belirleyici çıkış, kaynak herkese açık olduğunda yararlı olabilir. Ayrıca derleme sürecinde kullanılan ikiliye bağımlı derleme adımlarının olup olmadığını da belirleyebilir.

## <a name="produceonlyreferenceassembly"></a>ProduceOnlyReferenceAssembly

**ProduceOnlyReferenceAssembly** seçeneği, başvuru derlemesinin birincil çıkış olarak bir uygulama derlemesi yerine çıkış olması gerektiğini gösterir. Başvuru derlemeleri yürütülene kadar **ProduceOnlyReferenceAssembly** parametresi, pdb 'leri çıktısını sessizce devre dışı bırakır.

```xml
<ProduceOnlyReferenceAssembly>true</ProduceOnlyReferenceAssembly>
```

Başvuru derlemeleri özel bir derleme türüdür. Başvuru derlemeleri, kitaplığın ortak API yüzeyini göstermek için gereken en az meta veri miktarını içerir. Derleme araçlarındaki bir derlemeye başvururken önemli olan tüm Üyeler için bildirimler içerirler, ancak API sözleşmeleri üzerinde herhangi bir observable etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar. Daha fazla bilgi için bkz. [başvuru derlemeleri](../../../standard/assembly/reference-assemblies.md).

**ProduceOnlyReferenceAssembly** ve [**ProduceReferenceAssembly**](output.md#producereferenceassembly) seçenekleri birbirini dışlıyor.
