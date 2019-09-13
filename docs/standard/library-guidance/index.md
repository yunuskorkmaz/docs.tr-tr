---
title: Açık kaynaklı .NET kitaplığı Kılavuzu
description: Geliştiricilerin yüksek kaliteli .NET kitaplıkları oluşturmalarına yönelik en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 10/17/2018
ms.openlocfilehash: eff6c822757af6fb85622e88714accd40c32bcf5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928958"
---
# <a name="open-source-library-guidance"></a>Açık kaynak kitaplık kılavuzu

Bu kılavuz, geliştiricilerin yüksek kaliteli .NET kitaplıkları oluşturmalarına yönelik öneriler sağlar. Bu belgeler, *nasıl*bir .NET kitaplığı oluşturamadığına göre değil, *neden* ve ne *olduğuna* odaklanmaktadır.

Yüksek kaliteli açık kaynaklı .NET kitaplıklarının yönleri:

> [!div class="checklist"]
>
> * **Kapsamlı** .NET kitaplıkları birçok platformu, programlama dilini ve uygulamayı desteklemek için çaba harcar.
> * **Kararlı** -iyi .NET kitaplıkları, çok sayıda kitaplıklarla oluşturulmuş uygulamalarda çalışan .net ekosisteminde birlikte yer vardır.
> * **Geliştirecek şekilde tasarlanan** .NET kitaplıkları, mevcut kullanıcıları desteklerken zaman içinde iyileştirmeli ve gelişmelidir.
> * **Hata ayıklanabilir** -.NET kitaplıkları, kullanıcılar için harika bir hata ayıklama deneyimi oluşturmak üzere en son araçları kullanmalıdır.
> * **Güvenilen** -.net kitaplıklarında, en iyi güvenlik uygulamalarını kullanarak NuGet 'e yayımlayarak geliştiricilerin güveni vardır.

> [!div class="nextstepaction"]
> [Başlarken](./get-started.md)

## <a name="types-of-recommendations"></a>Öneri türleri

Her makalede dört tür öneri sunulmaktadır: **Bunu yapın**, **düşünün**, **önleyin**ve **Not**edin. Öneri türü, ne kadar önemli olduğunu gösterir.

Neredeyse her zaman bir **Do** önerisi izlemeniz gerekir. Örneğin:

**✔️** , bir NuGet paketi kullanarak kitaplığınızı dağıtır.

Diğer yandan, önerilerin genellikle izlenmesi gerektiğine **dikkat** edin, ancak kuralın meşru özel durumları vardır ve bu kılavuzdan sonra da kötü bir sorun olmaz:

**✔️** NuGet paketinizi sürüm Için [Semver 2.0.0](https://semver.org/) kullanmayı düşünün.

Genellikle iyi bir fikir olmayan ancak kuralın bölünmesi bazen anlamlı hale getirmeyen önerilerden **kaçının** :

**❌ Önlemek** Tam bir sürümü talep eden NuGet paket başvuruları.

Son **olarak, önermeyin,** neredeyse asla yapmanız gereken bir şeyi gösterir:

❌, Kitaplığınızın güçlü adlandırılmış ve tanımlayıcı olmayan sürümlerini **yayımlamaz** . Örneğin, `Contoso.Api` ve `Contoso.Api.StrongNamed`.

>[!div class="step-by-step"]
>[Next](get-started.md)
