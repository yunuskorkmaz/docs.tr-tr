---
title: -refout (C# Derleyici Seçenekleri)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: f48316a1e6f657e3bd0190d269dfe0e875a833d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72771755"
---
# <a name="-refout-c-compiler-options"></a>-refout (C# Derleyici Seçenekleri)

**-refout** seçeneği, başvuru derlemesinin çıktı olması gereken bir dosya yolu belirtir. Bu Emit API `metadataPeStream` çevirir. Bu seçenek, MSBuild'in [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) proje özelliğine karşılık gelir.

## <a name="syntax"></a>Sözdizimi

```console
-refout:filepath
```

## <a name="arguments"></a>Bağımsız Değişkenler

 `filepath`Başvuru derlemesi için dosya yolu. Genellikle birincil derleme ile eşleşmelidir. Önerilen kural kuralı (MSBuild tarafından kullanılan) birincil derlemeye göre bir "ref/" alt klasörüne başvuru derlemesi yerleştirmektir.

## <a name="remarks"></a>Açıklamalar

Başvuru derlemeleri, kitaplığın genel API yüzeyini temsil etmek için gereken yalnızca minimum meta veri miktarını içeren özel bir derleme türüdür. Bunlar, yapı araçlarında bir derlemeye atıfta bulunurken önemli olan tüm üyeler için bildirimler içerir, ancak API sözleşmesi üzerinde gözlemlenebilir bir etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar. Daha fazla bilgi için .NET Kılavuzu'ndaki [Başvuru derlemelerine](../../../standard/assembly/reference-assemblies.md) bakın.

`-refout` Ve [`-refonly`](refonly-compiler-option.md) seçenekler birbirini dışlar.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
