---
title: WCF geliştiricileri için bir WCF çözümünü gRPC-gRPC 'ye geçirme
description: Farklı türlerde WCF hizmetini gRPC 'de eşdeğerine geçirme.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 77bcb1412803b371778943763308c3010ed35aac
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72770110"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a>WCF çözümünü gRPC'ye geçirme

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bu bölümde, ASP.NET Core 3,0 gRPC projeleriyle nasıl çalışılacağı ve farklı türlerde WCF hizmetinin gRPC eşdeğerine geçirilmesi gösterilmektedir:

- ASP.NET Core 3,0 gRPC projesi oluşturun.
- Basit Istek-gRPC birli RPC 'ye yönelik yanıt verme işlemleri.
- GRPC istemci akışı RPC 'ye tek yönlü işlemler.
- GRPC çift yönlü akış RPC 'ye tam çift yönlü hizmetler.

Ayrıca, veri kümelerinin döndürülmesi için yinelenen alanlar ve Bölüm sonundaki istemci kitaplıklarının kullanımı gibi akış Hizmetleri kullanmanın bir karşılaştırması de vardır.

Örnek WCF uygulaması, bağımlılık ekleme için *Autofac* adlı, açık kaynaklı denetim (IOC) kapsayıcı kitaplığının kullanıldığı bir hisse senedi Hizmetleri kümesinin en az bir saplaması örneğidir. Her WCF hizmet türü için bir tane olmak üzere üç hizmet içerir. Hizmetler aşağıdaki bölümlerde daha ayrıntılı bir şekilde ele alınacaktır. Çözümler, GitHub 'da [DotNet-Architecture/GRPC-for-WCF-geliştiricilerinden](https://github.com/dotnet-architecture/grpc-for-wcf-developers) indirilebilir. Hizmetler, dış bağımlılıkları en aza indirmek için sahte veriler kullanır.

Örnekler, her bir hizmetin WCF ve gRPC uygulamalarını içerir.

>[!div class="step-by-step"]
>[Önceki](ws-protocols.md)
>[İleri](create-project.md)
