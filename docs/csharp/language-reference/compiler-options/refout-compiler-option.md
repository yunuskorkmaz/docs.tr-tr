---
title: -refonly (C# Derleyici Seçenekleri)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: e204a053f6f68a4b848d22c95c98f04edff58716
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506631"
---
# <a name="-refout-c-compiler-options"></a>-refonly (C# Derleyici Seçenekleri)

**- Refonly** seçeneği, başvuru bütünleştirilmiş kodu çıkış olmalıdır nerede bir dosya yolu belirtir. Bu şekilde dönüşür `metadataPeStream` yayma API.

## <a name="syntax"></a>Sözdizimi

```console
-refout:filepath
```

## <a name="arguments"></a>Arguments

 `filepath` Başvuru bütünleştirilmiş kodu için dosya yolu. Bu genellikle, birincil derlemenin eşleşmelidir. Başvuru derlemesinde yerleştirmek için (MSBuild tarafından kullanılır) önerilen kuralı olan bir "ref /" Birincil derleme göreli alt klasör.

## <a name="remarks"></a>Açıklamalar

Yalnızca meta veri bütünleştirilmiş kodları sahip tek bir yerine kendi metot gövdeleri `throw null` gövde, ancak anonim türler hariç tüm üyeleri içerir. Kullanılmasının nedeni `throw null` gövdeleri (aksine, gövde yok) olan PEVerify çalışmasını ve (Bu nedenle meta veri bütünlüğünü doğrulama) geçirin.

Başvuru derlemelerini içeren bir derleme düzeyi `ReferenceAssembly` özniteliği. Bu özniteliği, kaynakta belirtilebilir (sonra derleyici bu sentezlemek gerekmez). Bu öznitelik nedeniyle yürütme için başvuru derlemeleri yüklemeye çalışma zamanları reddeder (ancak bunlar yine de salt yansıma modunda olabilir). Bunlar salt yansıma olarak başvuru derlemelerini yüklemek emin olmak için derlemeleri ihtiyacından yansıtan araçları, aksi takdirde bunlar typeload hata çalışma zamanını şuradan alır.

Daha fazla başvuru bütünleştirilmiş kodları meta verilerini (özel üyeler) yalnızca meta veri derlemelerden kaldırın:

- Başvuru bütünleştirilmiş kodu, yalnızca bir API yüzeyi ihtiyacı olanları için başvuru içeriyor. Gerçek derleme ilgili belirli uygulamalar için ek başvurular sahip. Örneğin, başvuru bütünleştirilmiş kodu için `class C { private void M() { dynamic d = 1; ... } }` için gerekli herhangi bir türü başvurmuyor `dynamic`.
- Özel işlev-üyeler (yöntemler, özellikler ve olaylar), burada kendi kaldırma derleme garantileyebilirsiniz etkilemez durumlarda kaldırılır. Varsa hiçbir `InternalsVisibleTo` öznitelikleri, iç işlev üyeleri için aynı yapın.
- Ancak, tüm türler (özel veya iç içe türler dahil), başvuru bütünleştirilmiş kodları içinde tutulur. Tüm öznitelikleri (hatta iç olanlar) tutulur.
- Tüm sanal yöntemleri korunur. Açık arabirim uygulamalarını tutulur. Kendi erişimciler sanal (ve bu nedenle tutulur gibi) açıkça uygulanan özellikleri ve olayları tutulur.
- Bir yapının tüm alanlarını tutulur. (Bu gönderi için adayıdır-C#-7.1 iyileştirme)

`-refout` Ve [ `-refonly` ](refonly-compiler-option.md) seçenekleri karşılıklı olarak birbirini dışlar.

## <a name="see-also"></a>Ayrıca Bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
