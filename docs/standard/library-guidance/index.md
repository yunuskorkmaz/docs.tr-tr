---
title: Açık kaynaklı .NET kitaplığı Kılavuzu
description: Geliştiricilerin yüksek kaliteli .NET kitaplıkları oluşturmalarına yönelik en iyi yöntem önerileri.
ms.date: 10/17/2018
ms.openlocfilehash: c1e1c302eede86fd5555a8e84630e216e96f1ce7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706458"
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

Her makalede dört tür öneri sunulmaktadır: **Do**, **düþünün**, **önleyin**ve **Not**. Öneri türü, ne kadar önemli olduğunu gösterir.

Neredeyse her zaman bir **Do** önerisi izlemeniz gerekir. Örneğin:

**✔️** , bir NuGet paketi kullanarak kitaplığınızı dağıtır.

Diğer yandan, önerilerin genellikle izlenmesi gerektiğine **dikkat** edin, ancak kuralın meşru özel durumları vardır ve bu kılavuzdan sonra da kötü bir sorun olmaz:

**✔️** NuGet paketinizi sürüm Için [Semver 2.0.0](https://semver.org/) kullanmayı düşünün.

Genellikle iyi bir fikir olmayan ancak kuralın bölünmesi bazen anlamlı hale getirmeyen önerilerden **kaçının** :

**❌ önlemek** Tam bir sürümü talep eden NuGet paket başvuruları.

Son **olarak, önermeyin,** neredeyse asla yapmanız gereken bir şeyi gösterir:

❌, kitaplığınızın güçlü adlandırılmış ve tanımlayıcı olmayan sürümlerini **yayımlamaz** . Örneğin, `Contoso.Api` ve `Contoso.Api.StrongNamed`.

>[!div class="step-by-step"]
>[Next](get-started.md)
