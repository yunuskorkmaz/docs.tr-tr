---
title: -refonly (C# Derleyici Seçenekleri)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 06b246d6e5831563389efa402ccb6a942430efa4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589733"
---
# <a name="-refonly-c-compiler-options"></a>-refonly (C# Derleyici Seçenekleri)

**- Refonly** seçeneği, bir başvuru bütünleştirilmiş kodu çıkış birincil çıktı olarak bir uygulama derleme yerine olması gerektiğini gösterir. `-refonly` Parametre sessiz bir şekilde devre dışı bırakır pdb, çıktısı olarak başvuru bütünleştirilmiş kodları yürütülemez.

## <a name="syntax"></a>Sözdizimi

```console
-refonly
```

## <a name="remarks"></a>Açıklamalar

Yalnızca meta veri bütünleştirilmiş kodları sahip tek bir yerine kendi metot gövdeleri `throw null` gövde, ancak anonim türler hariç tüm üyeleri içerir. Kullanılmasının nedeni `throw null` gövdeleri (aksine, gövde yok) olan PEVerify çalışmasını ve (Bu nedenle meta veri bütünlüğünü doğrulama) geçirin.

Başvuru derlemelerini içeren bir derleme düzeyi `ReferenceAssembly` özniteliği. Bu özniteliği, kaynakta belirtilebilir (sonra derleyici bu sentezlemek gerekmez). Bu öznitelik nedeniyle yürütme için başvuru derlemeleri yüklemeye çalışma zamanları reddeder (ancak bunlar yine de salt yansıma modunda olabilir). Bunlar salt yansıma olarak başvuru derlemelerini yüklemek emin olmak için derlemeleri ihtiyacından yansıtan araçları, aksi takdirde bunlar typeload hata çalışma zamanını şuradan alır.

Daha fazla başvuru bütünleştirilmiş kodları meta verilerini (özel üyeler) yalnızca meta veri derlemelerden kaldırın:

- Başvuru bütünleştirilmiş kodu, yalnızca bir API yüzeyi ihtiyacı olanları için başvuru içeriyor. Gerçek derleme ilgili belirli uygulamalar için ek başvurular sahip. Örneğin, başvuru bütünleştirilmiş kodu için `class C { private void M() { dynamic d = 1; ... } }` için gerekli herhangi bir türü başvurmuyor `dynamic`.
- Özel işlev-üyeler (yöntemler, özellikler ve olaylar), burada kendi kaldırma derleme garantileyebilirsiniz etkilemez durumlarda kaldırılır. Varsa hiçbir `InternalsVisibleTo` öznitelikleri, iç işlev üyeleri için aynı yapın.
- Ancak, tüm türler (özel veya iç içe türler dahil), başvuru bütünleştirilmiş kodları içinde tutulur. Tüm öznitelikleri (hatta iç olanlar) tutulur.
- Tüm sanal yöntemleri korunur. Açık arabirim uygulamalarını tutulur. Kendi erişimciler sanal (ve bu nedenle tutulur gibi) açıkça uygulanan özellikleri ve olayları tutulur.
- Bir yapının tüm alanlarını tutulur. (Bu gönderi için adayıdır-C#-7.1 iyileştirme)

`-refonly` Ve [ `-refout` ](refout-compiler-option.md) seçenekleri karşılıklı olarak birbirini dışlar.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
