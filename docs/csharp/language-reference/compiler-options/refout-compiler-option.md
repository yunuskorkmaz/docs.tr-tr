---
title: "-refout (C# Derleyici Seçenekleri)"
ms.date: 08/08/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fbae6f461304c37ba2ef10da16b5d520377bb225
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-refout-c-compiler-options"></a>-refout (C# Derleyici Seçenekleri)

**- Refout** seçeneği, bir dosya yolu burada referans derlemesini gerektiğini belirtir. Bu şekilde dönüşür `metadataPeStream` yayma API'sindeki.

## <a name="syntax"></a>Sözdizimi

```console
-refout:filepath
```

## <a name="arguments"></a>Arguments

 `filepath`Başvuru derleme için filepath. Bu genellikle birincil derlemesi eşleşmesi. (MSBuild tarafından kullanılır) önerilen kuralı başvuru bütünleştirilmiş kodunda yerleştirmektir bir "ref /" Birincil derleme göreli alt klasör.

## <a name="remarks"></a>Açıklamalar

Yalnızca meta veri derleme sahip tek bir tıklatmayla yerine kendi yöntem gövdeleri `throw null` gövde, ancak anonim türler dışındaki tüm üyelerini içerir. Kullanmanın nedeni `throw null` gövdeleri (aksine, gövde yok) olan PEVerify çalışmasını ve (Bu nedenle meta veri bütünlüğü doğrulama) geçirin.

Başvuru derlemeleri içeren bir derleme düzeyi `ReferenceAssembly` özniteliği. Bu öznitelik kaynağında belirtilebilir (sonra derleyici onu sentezlemek gerekmez). Bu öznitelik nedeniyle çalışma zamanları başvuru yürütme derlemelerde yük reddeder (ancak bunlar hala salt yansıma modunda yüklenmiş olabilir). Başvuru derlemeleri salt yansıma olarak yük emin olmak için derlemeleri gerekir yansıtacak Araçlar, aksi halde bunlar bir typeload çalışma zamanı hatasıyla karşılaşırsınız.

Daha fazla başvuru derlemeleri meta veriler (özel üyeler) yalnızca meta veri derlemelerden kaldırın:

- Bir referans derlemesini yalnızca API yüzeyi gerekeni için başvuru içeriyor. Gerçek derleme belirli uygulamalar için ilgili ek başvurular olabilir. Örneği için başvuru bütünleştirilmiş kod `class C { private void M() { dynamic d = 1; ... } }` için gerekli herhangi bir türü başvurmuyor `dynamic`.
- Özel işlevi-üyeleri (yöntemler, özellikler ve olaylar), burada kendi kaldırma derleme garantileyebilirsiniz etkilemez durumlarda kaldırılır. Varsa hiçbir `InternalsVisibleTo` öznitelikleri, iç işlevi üyeleri için aynı yapın.
- Ancak (özel veya iç içe geçmiş türler dahil) tüm türleri başvuru derlemeleri tutulur. Tüm öznitelikleri (hatta iç olanlar) korunur.
- Tüm sanal yöntemleri korunur. Açık arabirim uygulamaları tutulur. Kendi erişimciler sanal (ve dolayısıyla korunması gibi) açıkça gerçekleştirilen özellikleri ve olayları tutulur.
- Yapı tüm alanları tutulur. (Bu bir post adaydır-C#-7.1 iyileştirme)

`-refout` Ve [ `-refonly` ](refonly-compiler-option.md) seçenekleri karşılıklı olarak birbirini dışlar.

## <a name="see-also"></a>Ayrıca Bkz.
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
