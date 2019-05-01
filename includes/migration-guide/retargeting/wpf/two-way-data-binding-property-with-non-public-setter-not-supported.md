---
ms.openlocfilehash: a70aca33d0830f3b23ff985f17c469cb7c4ff35c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62093631"
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
