---
title: Açık kaynak .NET kitaplık Kılavuzu
description: Geliştiricilerin yüksek kaliteli .NET kitaplıkları oluşturmak en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 10/17/2018
ms.openlocfilehash: 85d76c8b2bd0f030e3fbc1987e6ff51d6da44e76
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644379"
---
# <a name="open-source-library-guidance"></a>Açık kaynak kitaplık kılavuzu

Bu kılavuz, geliştiricilerin yüksek kaliteli .NET kitaplıkları oluşturmak öneriler sağlar. Bu belge odaklanır *ne* ve *neden* olmayan bir .NET kitaplığı oluşturma sırasında *nasıl*.

Yüksek kaliteli açık kaynak .NET kitaplıkları yönlerini:

> [!div class="checklist"]
> * **Kapsamlı** -iyi .NET kitaplıkları çaba birçok Platform, programlama dilleri ve uygulamaları desteklemek.
> * **Kararlı** -birçok kitaplıkları ile oluşturulan uygulamalar çalışan .NET ekosisteminde iyi .NET kitaplıkları bir arada.
> * **Gelişmek için tasarlanmış** -.NET kitaplıkları artırmak ve zamandan, var olan kullanıcıları desteklemek için üzerinde evrim Geçiren.
> * **Hata ayıklanabilir** -.NET kitaplıkları, kullanıcılar için harika bir hata ayıklama deneyimi oluşturmak için en yeni araçlara kullanmalıdır.
> * **Güvenilen** -.NET kitaplıkları, NuGet kullanarak en iyi güvenlik uygulamaları yayımlayarak geliştiricilerin güven sahip.

> [!div class="nextstepaction"]
> [Başlarken](./get-started.md)

## <a name="types-of-recommendations"></a>Öneri türü

Her bir makaleyi dört tür önerileri sunar: **Yapmak**, **göz önünde bulundurun**, **önlemek**, ve **olmayan**. Ne kadar güçlü gelmelidir önerinin türünü gösterir.

Neredeyse her zaman izlemeniz gereken bir **yapmak** öneri. Örneğin:

**✔️ YAPMAK** bir NuGet paketi kullanarak kitaplığınızda dağıtın.

Öte yandan, **düşünün** önerileri genellikle sonrasında, ancak kuralın yasal özel durumu vardır ve yönergeleri izleyerek değil hatalı düşündüğünüz olmamalıdır:

**✔️ DÜŞÜNÜN** kullanarak [SemVer 2.0.0](https://semver.org/) sürümüne NuGet paketinizi.

**Önlemek** önerileri bahsetmek genellikle iyi bir fikir olmayan bir şey, ancak bazen kural bozucu anlamlı:

**❌ KAÇININ** tam bir sürümünü gerektirdiğinden NuGet paket başvuruları.

Son olarak, **olmayan** önerileri neredeyse hiç yapmanız bir şey gösterir:

**❌ SAĞLAMADIĞI** kitaplığınızın tanımlayıcı adlı ve olmayan-tanımlayıcı adlı sürümler yayımlayabilir. Örneğin, `Contoso.Api` ve `Contoso.Api.StrongNamed`.

>[!div class="step-by-step"]
>[Next](get-started.md)
