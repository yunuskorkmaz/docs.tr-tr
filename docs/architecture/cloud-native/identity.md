---
title: Kimlik
description: Azure için Cloud Native .NET uygulamaları tasarlama | IDENTITY
ms.date: 09/23/2019
ms.openlocfilehash: 4cc7c04bf323d2589777df466321f6801f511b6f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183051"
---
# <a name="identity"></a>Kimlik

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Çoğu yazılım uygulamasının, bunları çağıran kullanıcı veya işlemle ilgili bazı bilgileri olması gerekir. Bir uygulamayla etkileşim kuran kullanıcı veya işlem güvenlik sorumlusu olarak bilinir ve bu sorumluların kimlik doğrulama ve yetkilendirme süreci kimlik yönetimi veya yalnızca *kimlik*olarak bilinir. Basit uygulamalar uygulama içindeki tüm kimlik yönetimini içerebilir, ancak bu yaklaşım birçok uygulamayla ve birçok güvenlik sorumlusu ile iyi ölçeklenmez. Windows, merkezi kimlik doğrulaması ve yetkilendirme sağlamak için Active Directory kullanımını destekler.

<!-- (insert figure showing Windows AD auth model) -->

Bu çözüm kurumsal ağlarda geçerli olsa da, AD etki alanı dışındaki kullanıcılar veya uygulamalar tarafından kullanılmak üzere tasarlanmamıştır. Internet tabanlı uygulamaların büyümesi ve bulut Yerel uygulamalarının yüksei sayesinde güvenlik modelleri geliştirilmiştir.

Bugünün bulutta yerel kimlik modelinde, mimarinin dağıtılması varsayılır. Uygulamalar her yerde dağıtılabilir ve diğer uygulamalarla her yerde iletişim kurabilir. İstemciler bu uygulamalarla her yerden iletişim kurabilir ve aslında istemciler platformların ve cihazların herhangi bir birleşimini içerebilir. Bulutta yerel kimlik çözümleri, istemcilerden güvenli uygulama erişimi elde etmek için açık standartlardan yararlanır. Bu istemciler PC veya telefonlardaki insan kullanıcılarından, her yerde barındırılan diğer uygulamalara, dünyanın herhangi bir yerindeki herhangi bir yazılım platformunu çalıştıran en üst kutular ve ıOT cihazlarına göre değişir.

Modern bulutla yerel kimlik çözümleri, genellikle bir güvenli belirteç hizmeti/sunucusu (STS) tarafından kimlik saptandıktan sonra bir güvenlik sorumlusu tarafından verilen erişim belirteçlerine faydalanır. Erişim belirteci, genellikle bir JSON Web Token (JWT), güvenlik sorumlusu hakkında *talepler* içerir. Bu talepler, kullanıcının kimliğini en düşük düzeyde içerir, ancak aynı zamanda, sorumlu vermek için erişim düzeyini belirlemede uygulamalar tarafından kullanılabilecek ek talepler de içerebilir.

<!-- (insert figure showing basic handshake involving a principal, an STS, and an app) -->

Genellikle STS yalnızca Sorumlunun kimliğini doğrulamaktan sorumludur. Kaynaklara erişim düzeyini belirleme, uygulamanın diğer bölümlerine bırakılır.

## <a name="references"></a>Referanslar

- [Microsoft Identity platformu](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
>[Önceki](azure-monitor.md)
>[İleri](authentication-authorization.md)
