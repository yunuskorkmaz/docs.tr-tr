---
title: -refonly (C# Derleyici Seçenekleri)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 856b65d3b2217dbe5d53ecda00723b47247d80a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72773848"
---
# <a name="-refonly-c-compiler-options"></a>-refonly (C# Derleyici Seçenekleri)

**-refonly** seçeneği, birincil çıktı olarak bir uygulama derlemesi yerine bir başvuru derlemesinin çıktı olması gerektiğini gösterir. `-refonly` Parametre, başvuru derlemeleri yürütülemediği için PDB'leri sessizce devre dışı bıraktı. Bu seçenek, MSBuild'in [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) proje özelliğine karşılık gelir.

## <a name="syntax"></a>Sözdizimi

```console
-refonly
```

## <a name="remarks"></a>Açıklamalar

Başvuru derlemeleri, kitaplığın genel API yüzeyini temsil etmek için gereken yalnızca minimum meta veri miktarını içeren özel bir derleme türüdür. Bunlar, yapı araçlarında bir derlemeye atıfta bulunurken önemli olan tüm üyeler için bildirimler içerir, ancak API sözleşmesi üzerinde gözlemlenebilir bir etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar. Daha fazla bilgi için .NET Kılavuzu'ndaki [Başvuru derlemelerine](../../../standard/assembly/reference-assemblies.md) bakın.

`-refonly` Ve [`-refout`](refout-compiler-option.md) seçenekler birbirini dışlar.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
