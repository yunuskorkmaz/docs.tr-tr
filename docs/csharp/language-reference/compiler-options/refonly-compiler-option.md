---
title: -refonly (C# Derleyici Seçenekleri)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: c380df1cb473fcd187e56bb0a338a909dd3ac894
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-refonly-c-compiler-options"></a>-refonly (C# Derleyici Seçenekleri)

**- Refonly** seçeneği, bir referans derlemesini çıkış uygulaması derleme, birincil çıktı olarak yerine olması gerektiğini gösterir. `-refonly` Parametre sessiz bir şekilde devre dışı bırakır pdb, kayıt çıkarma başvuru derlemeleri yürütülemez gibi.

## <a name="syntax"></a>Sözdizimi

```console
-refonly
```

## <a name="remarks"></a>Açıklamalar

Yalnızca meta veri derleme sahip tek bir tıklatmayla yerine kendi yöntem gövdeleri `throw null` gövde, ancak anonim türler dışındaki tüm üyelerini içerir. Kullanmanın nedeni `throw null` gövdeleri (aksine, gövde yok) olan PEVerify çalışmasını ve (Bu nedenle meta veri bütünlüğü doğrulama) geçirin.

Başvuru derlemeleri içeren bir derleme düzeyi `ReferenceAssembly` özniteliği. Bu öznitelik kaynağında belirtilebilir (sonra derleyici onu sentezlemek gerekmez). Bu öznitelik nedeniyle çalışma zamanları başvuru yürütme derlemelerde yük reddeder (ancak bunlar hala salt yansıma modunda yüklenmiş olabilir). Başvuru derlemeleri salt yansıma olarak yük emin olmak için derlemeleri gerekir yansıtacak Araçlar, aksi halde bunlar bir typeload çalışma zamanı hatasıyla karşılaşırsınız.

Daha fazla başvuru derlemeleri meta veriler (özel üyeler) yalnızca meta veri derlemelerden kaldırın:

- Bir referans derlemesini yalnızca API yüzeyi gerekeni için başvuru içeriyor. Gerçek derleme belirli uygulamalar için ilgili ek başvurular olabilir. Örneği için başvuru bütünleştirilmiş kod `class C { private void M() { dynamic d = 1; ... } }` için gerekli herhangi bir türü başvurmuyor `dynamic`.
- Özel işlevi-üyeleri (yöntemler, özellikler ve olaylar), burada kendi kaldırma derleme garantileyebilirsiniz etkilemez durumlarda kaldırılır. Varsa hiçbir `InternalsVisibleTo` öznitelikleri, iç işlevi üyeleri için aynı yapın.
- Ancak (özel veya iç içe geçmiş türler dahil) tüm türleri başvuru derlemeleri tutulur. Tüm öznitelikleri (hatta iç olanlar) korunur.
- Tüm sanal yöntemleri korunur. Açık arabirim uygulamaları tutulur. Kendi erişimciler sanal (ve dolayısıyla korunması gibi) açıkça gerçekleştirilen özellikleri ve olayları tutulur.
- Yapı tüm alanları tutulur. (Bu bir post adaydır-C#-7.1 iyileştirme)

`-refonly` Ve [ `-refout` ](refout-compiler-option.md) seçenekleri karşılıklı olarak birbirini dışlar.

## <a name="see-also"></a>Ayrıca bkz.
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
