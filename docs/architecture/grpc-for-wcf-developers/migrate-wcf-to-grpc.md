---
title: WCF geliştiricileri için bir WCF çözümünü gRPC-gRPC 'ye geçirme
description: Farklı türlerde WCF Hizmetleri gRPC 'de eşdeğerine nasıl geçirilir.
ms.date: 12/15/2020
ms.openlocfilehash: 3bd35cb6119368ff3db3be9ab5fabf89f2652b29
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97937967"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a>WCF çözümünü gRPC'ye geçirme

Bu bölümde, ASP.NET Core 5,0 gRPC projeleriyle nasıl çalışılacağı ve farklı türlerde Windows Communication Foundation (WCF) Hizmetleri gRPC eşdeğerine nasıl geçirilerek anlatılmaktadır:

- ASP.NET Core 5,0 gRPC projesi oluşturun.
- Basit istek-gRPC birli RPC 'ye yönelik yanıt verme işlemleri.
- GRPC istemci akışı RPC 'ye tek yönlü işlemler.
- GRPC çift yönlü akış RPC 'ye tam çift yönlü hizmetler.

Ayrıca, veri kümelerini döndürmek için tekrarlanan alanlar ve akış Hizmetleri kullanmanın bir karşılaştırması vardır ve bu, bölümün sonunda istemci kitaplıklarının kullanımıyla ilgili bir tartışmadır.

Örnek WCF uygulaması, bir hisse senedi Hizmetleri kümesinin en az bir saplama örneğidir. Bağımlılık ekleme için Autofac adlı açık kaynaklı denetim (IOC) kapsayıcı kitaplığını kullanır. Her WCF hizmet türü için bir tane olmak üzere üç hizmet içerir. Hizmetler aşağıdaki bölümlerde daha ayrıntılı bir şekilde ele alınacaktır. GitHub 'da, [DotNet-Architecture/GRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) çözümlerini yükleyebilirsiniz. Hizmetler, dış bağımlılıkları en aza indirmek için sahte veriler kullanır.

Örnekler, her bir hizmetin WCF ve gRPC uygulamalarını içerir.

>[!div class="step-by-step"]
>[Önceki](ws-protocols.md) 
> [Sonraki](create-project.md)
