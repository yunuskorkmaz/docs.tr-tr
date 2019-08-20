---
title: -refout (C# derleyici seçenekleri)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 97cbf540527d0449387b71bb1d97df95b6a4aba4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602508"
---
# <a name="-refout-c-compiler-options"></a>-refout (C# derleyici seçenekleri)

**-Refout** seçeneği, başvuru derlemesinin çıkış olması gereken bir dosya yolunu belirtir. Bu, yayma `metadataPeStream` API 'sine çevrilir. Bu seçenek, MSBuild 'in [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) Project özelliğine karşılık gelir.

## <a name="syntax"></a>Sözdizimi

```console
-refout:filepath
```

## <a name="arguments"></a>Arguments

 `filepath`Başvuru derlemesinin FilePath 'i. Genellikle birincil derlemenin ile eşleşmelidir. Önerilen kural (MSBuild tarafından kullanılır), başvuru derlemesini birincil derlemeye göre bir "ref/" alt klasörüne yerleştirmelidir.

## <a name="remarks"></a>Açıklamalar

Yalnızca meta veri derlemelerinde kendi yöntem gövdeleri tek `throw null` bir gövdele değiştirilmiştir, ancak anonim türler hariç tüm üyeleri dahil edin. Gövdeler kullanmanın `throw null` nedeni (gövdeden farklı olarak), Peverify 'ın çalıştırılabilmesi ve geçmesi (Bu nedenle meta verilerin tamamlanmasının doğrulanması).

Başvuru derlemeleri bir derleme düzeyi `ReferenceAssembly` özniteliği içerir. Bu öznitelik kaynakta belirtilebilir (derleyicinin onu birleştirmesini gerektirmez). Bu öznitelik nedeniyle, çalışma zamanları yürütme için başvuru derlemelerini yüklemeyi reddeder (ancak yine de yalnızca yansıma modunda yüklenebilirler). Derlemeleri yansıtan araçların başvuru derlemelerini yalnızca yansıma olarak yüklediklerinden emin olunması gerekir, aksi takdirde çalışma zamanından bir türde hatası alırlar.

Başvuru derlemeleri meta verileri (özel Üyeler) yalnızca meta veri derlemelerinden daha da kaldırır:

- Bir başvuru derlemesinin yalnızca API yüzeyinde ihtiyacı olan başvurular vardır. Gerçek derlemenin belirli uygulamalarla ilgili ek başvuruları olabilir. Örneğin, için `class C { private void M() { dynamic d = 1; ... } }` başvuru derlemesi için `dynamic`gereken herhangi bir türe başvurmuyor.
- Özel işlev-Üyeler (Yöntemler, Özellikler ve olaylar) kaldırma işleminin derleme observably etkisi olmadığı durumlarda kaldırılır. <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Öznitelik yoksa, iç işlev üyeleri için aynı işlemi yapın.
- Ancak tüm türler (özel veya iç içe türler dahil) başvuru Derlemeleriyle tutulur. Tüm öznitelikler (hatta iç olmasalar bile) tutulur.
- Tüm sanal yöntemler tutulur. Açık arabirim uygulamaları tutulur. Açıkça uygulanan özellikler ve olaylar, erişimcileri sanal olduğundan (ve bu nedenle saklanır) tutulur.
- Bir yapının tüm alanları tutulur. (Bu,-C#-7,1 geliştirme sonrası için bir adaydır)

`-refout` [Ve`-refonly`](refonly-compiler-option.md) seçenekleri birbirini dışlıyor.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
