---
title: Merkezi yapılandırma
description: Azure Key Vault kullanan merkezi yapılandırma, bulutta yerel uygulamaların yönetilmesini kolaylaştırabilir.
ms.date: 06/30/2019
ms.openlocfilehash: 4c516b6773d913acd71ff06742302e9766a141e2
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214001"
---
# <a name="centralized-configuration"></a>Merkezi yapılandırma

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bulutta yerel uygulamalar geleneksel tek örnekli tek parçalı uygulamalar 'dan daha fazla çalışan çok sayıda hizmet içerir. Birbirine bağlı onlarca hizmet veren hizmetlerin yapılandırma ayarlarını yönetmek zor olabilir, bu nedenle merkezi yapılandırma depoları genellikle dağıtılmış uygulamalar için uygulanır.

[Bölüm 1](introduction.md)' de anlatıldığı gibi, on Iki öğeli uygulama önerileri, kod ve yapılandırma arasında katı ayrım gerektirir. Bu, yapılandırma ayarlarının sabitler olarak depolanması veya koddaki değişmez değerlerin bir ihlalin olması anlamına gelir. Geliştirme, test, hazırlama ve üretim dahil olmak üzere birden çok ortamda aynı kodun kullanılması gerektiğinden bu öneri vardır. Ancak, yapılandırma değerleri bu ortamların her biri arasında farklılık gösterebilir. Bu nedenle, yapılandırma değerleri ortamın kendisinde depolanmalıdır veya ortamın kimlik bilgilerini merkezi bir yapılandırma deposuna depolaması gerekir.

EShopOnContainers uygulaması, her mikro hizmetle yerel uygulama ayarları dosyalarını içerir. Bu dosyalar kaynak denetimine iade edilir ancak bağlantı dizeleri veya API anahtarları gibi üretim sırları dahil değildir. Üretimde, hizmet başına ortam değişkenleriyle bireysel ayarların üzerine yazılabilir. Bu, barındırılan uygulamalar için yaygın bir uygulamadır, ancak merkezi bir yapılandırma deposu sağlamaz. Yapılandırma ayarlarının merkezi yönetimini desteklemek için her mikro hizmet, yerel ayarları veya Azure Key Vault ayarları kullanımı arasında geçiş yapmak için bir ayar içerir.

## <a name="azure-key-vault"></a>Azure Key Vault

Azure Key Vault, belirteçlerin, parolaların, sertifikaların, API anahtarlarının ve diğer gizli parolaların güvenli bir şekilde depolanmasını sağlar. Key Vault erişim, eShopOnContainers mikro hizmetleri için bir ClientID/ClientSecret bileşiminin kullanılması gereken, uygun bir arayan kimlik doğrulaması ve yetkilendirme gerektirir. Bu kimlik bilgilerini kaynak denetimine iade etmeyin, ancak bunun yerine uygulamanın ortamında ayarlayın. AKS 'ten Key Vault doğrudan erişim, [Key Vault FlexVolume](https://github.com/Azure/kubernetes-keyvault-flexvol)kullanılarak elde edilebilir.

Merkezi yapılandırma sayesinde, Merkezi günlük uç noktası gibi tüm uygulama için uygulanan ayarlar bir kez ayarlanabilir ve Dağıtılmış uygulamanın her bölümü tarafından kullanılır. Mikro hizmetlerin bir diğerinden bağımsız olması gerekse de, yapılandırma ayrıntıları merkezi bir yapılandırma deposundan faydalanabilir bazı paylaşılan bağımlılıklar de vardır.

>[!div class="step-by-step"]
>[Önceki](deploy-eshoponcontainers-azure.md)
>[İleri](scale-applications.md)
