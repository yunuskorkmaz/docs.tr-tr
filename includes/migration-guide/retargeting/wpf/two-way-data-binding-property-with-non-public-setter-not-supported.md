---
ms.openlocfilehash: a70aca33d0830f3b23ff985f17c469cb7c4ff35c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774499"
---
### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>Bir özelliğe genel olmayan ayarlayıcı ile iki yönlü veri bağlama desteklenmiyor

|   |   |
|---|---|
|Ayrıntılar|Genel bir Ayarlayıcısı olmadan bir özelliğine veri bağlama girişimi desteklenen bir senaryo olmamıştı. .NET Framework 4.5.1 başlayarak, bu senaryo oluşturmaz bir <xref:System.InvalidOperationException?displayProperty=name>. Bu yeni özel durum, özellikle .NET Framework 4.5.1'i hedefleyen uygulamalar için yalnızca oluşturulur unutmayın. Bir uygulamayı .NET Framework 4.5 hedefliyse, çağrı izin verilir. Uygulama belirli bir .NET Framework sürümünü hedef almıyor, bağlama tek yönlü olarak kabul edilir.|
|Öneri|Uygulama, tek yönlü bağlamaya kullanabilir veya özelliğin Ayarlayıcısı genel olarak kullanıma sunmak için güncelleştirilmesi gerekir. Alternatif olarak, .NET Framework 4.5 hedefleyen, uygulamanın eski davranışlar neden olur.|
|Kapsam|İkincil|
|Sürüm|4.5.1|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType></li></ul>|
