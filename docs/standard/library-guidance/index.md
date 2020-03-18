---
title: Açık kaynak .NET kitaplık kılavuzu
description: Geliştiricilerin yüksek kaliteli .NET kitaplıkları oluşturması için en iyi uygulama önerileri.
ms.date: 10/17/2018
ms.openlocfilehash: 4c76dfae6ffc39df7f15381be64e33657067d79d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731429"
---
# <a name="open-source-library-guidance"></a>Açık kaynak kitaplık kılavuzu

Bu kılavuz, geliştiricilerin yüksek kaliteli .NET kitaplıkları oluşturması için öneriler sağlar. Bu dokümantasyon, bir .NET kitaplığı oluştururken *ne* ve *neden* değil, *nasıl*odaklanır.

Yüksek kaliteli açık kaynak .NET kitaplıklarının yönleri:

> [!div class="checklist"]
>
> * **Kapsayıcı** - İyi .NET kitaplıkları birçok platformu, programlama dilini ve uygulamayı desteklemeye çalışır.
> * **Kararlı** - İyi .NET kitaplıkları .NET ekosisteminde bir arada bulunur ve birçok kitaplıkla oluşturulmuş uygulamalarda çalışır.
> * **Gelişmeye yönelik** - .NET kitaplıkları, mevcut kullanıcıları desteklerken zaman içinde gelişmeli ve gelişmelidir.
> * **Hata ayıklanabilir** - .NET kitaplıkları, kullanıcılar için harika bir hata ayıklama deneyimi oluşturmak için en son araçları kullanmalıdır.
> * **Güvenilen** - .NET kitaplıkları, güvenlik en iyi uygulamalarını kullanarak NuGet'e yayımlayarak geliştiricilerin güvenine sahiptir.

> [!div class="nextstepaction"]
> [Başlayın](./get-started.md)

## <a name="types-of-recommendations"></a>Öneri türleri

Her makale dört tür öneri sunar: **Do**, **Göz at**, **Kaçın**, ve **etmeyin**. Öneri türü, ne kadar güçlü bir şekilde izlenmesi gerektiğini gösterir.

Hemen hemen her zaman bir **Do** önerisi takip etmelidir. Örnek:

✔️ DO kitaplığınızı bir NuGet paketi kullanarak dağıtın.

Diğer taraftan, **düşünün** önerileri genellikle takip edilmelidir, ancak kuralın meşru istisnaları vardır ve kılavuzu izlemediğiniz için kendinizi kötü hissetmemelisiniz:

✔️ NuGet paketinizi kullanmak için [SemVer 2.0.0'ı](https://semver.org/) kullanmayı düşünün.

Öneriler genellikle iyi bir fikir değildir şeyler söz **kaçının,** ancak kuralı ihlal bazen mantıklı:

❌Kaçının NuGet paket başvuruları tam bir sürümünü talep.

Ve son olarak, öneriler hemen hemen hiç yapmamanız gereken bir şey gösterir **etmeyin:**

❌Kitaplığınızın güçlü adlandırılmış ve güçlü olmayan adlandırılmış sürümlerini yayımlamayın. Örneğin, `Contoso.Api` ve `Contoso.Api.StrongNamed`.

>[!div class="step-by-step"]
>[Sonraki](get-started.md)
