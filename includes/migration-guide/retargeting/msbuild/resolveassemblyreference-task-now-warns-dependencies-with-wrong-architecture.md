---
ms.openlocfilehash: 4d410811095786b33580d25f6c6eab3ac2f27148
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616099"
---
### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a>ResolveAssemblyReference görevi artık yanlış mimariye sahip bağımlılıkları uyarır

#### <a name="details"></a>Ayrıntılar

Görev bir uyarı yayar, bu, bir başvurunun veya bağımlılıklarından birinin uygulamanın mimarisiyle eşleşmediği anlamına gelir. Örneğin, seçeneğiyle derlenen bir uygulama `AnyCPU` bir x86 başvurusu içeriyorsa bu durum oluşur. Bu tür bir senaryo, çalışma zamanında bir uygulama hatasına neden olabilir (Bu durumda, uygulama bir x64 işlemi olarak dağıtılırsa).

#### <a name="suggestion"></a>Öneri

İki etki alanı vardır:

- Yeniden derleme, uygulama MSBuild 'in önceki bir sürümü altında derlenmişse görünmeyen uyarılar oluşturur. Ancak, uyarı bir çalışma zamanı hatası kaynağını tanımladığından, araştırılması ve giderilmesi gerekir.
- Uyarılar hata olarak kabul edilir, uygulama derlenmeyecektir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.5.1       |
| Tür    | Yeniden Hedefleme |
