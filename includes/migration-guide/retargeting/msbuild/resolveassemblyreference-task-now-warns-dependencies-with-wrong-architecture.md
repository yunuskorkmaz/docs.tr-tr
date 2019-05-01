---
ms.openlocfilehash: 39a329597ef28e002242103a247515d94761676a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62093632"
---
### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a>ResolveAssemblyReference görevi bağımlılıklarının yanlış mimarisi ile artık uyarır.

|   |   |
|---|---|
|Ayrıntılar|Görev bir başvurusu veya bağımlılıklarından biri uygulamanın mimarisi eşleşmediğini gösteren MSB3270 bir uyarı gönderir. Örneğin, bu ile derlenen bir uygulamayı ortaya çıkar <code>AnyCPU</code> seçeneği içeren bir x86 başvuru. Bu tür bir senaryonun çalışma zamanında bir uygulama hatasına neden (Bu durumda, uygulama bir x64 dağıtılırsa işlem).|
|Öneri|İki etki alanı vardır:<ul><li>Yeniden derleme MSBuild'ın önceki bir sürümünden altında uygulama derlendiğinde görülmedi uyarılar oluşturur. Uyarı, çalışma zamanı hatası olası kaynak tanımladığından, ancak, araştırılması ele ve.</li><li>Uyarıları hata olarak kabul edilir, uygulama derlemek başarısız olur.</li></ul>|
|Kapsam|İkincil|
|Sürüm|4.5.1|
|Tür|Yeniden Hedefleme|
