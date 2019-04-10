---
title: .NET Framework'te Ağ İzleme
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework], network tracing
- methods, network tracing
- Networking
- trace enabled debugging
- network tracing, about network tracing
- network tracing
- network, network tracing
- traffic tracing
- tracing [.NET Framework], network
- deploying applications [.NET Framework], network traffic
- capturing network traffic
- Internet, network tracing
- Network Resources
- output, network tracing
- method invocations
ms.assetid: e993b7c3-087f-45d8-9c02-9dded936d804
ms.openlocfilehash: 45ec7b83824777c594b966a38d2b7fcd4f63b596
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221195"
---
# <a name="network-tracing-in-the-net-framework"></a>.NET Framework'te Ağ İzleme
.NET Framework'te ağ izleme, yönetilen uygulama tarafından oluşturulan yöntem çağrıları ve ağ trafiğiyle ilgili bilgilere erişim sağlar. Bu özellik, geliştirilen uygulamalarda hata ayıklanırken ve dağıtılan uygulamalar analiz edilirken yararlı olur. Ağ izleme tarafından sağlanan çıkış, geliştirme zamanı ve üretim ortamında farklı kullanım senaryolarını destekleyecek şekilde özelleştirilebilir.  
  
 .NET Framework'te ağ izlemeyi etkinleştirmek üzere izleme çıkışı için bir hedef seçmeniz ve ağ izleme yapılandırma ayarlarını uygulamaya ve makine yapılandırma dosyasına eklemeniz gerekir. Yapılandırma dosyaları ve bunların nasıl kullanıldığı açıklamaları için bkz. [yapılandırma dosyalarını](../../../docs/framework/configure-apps/index.md). Ağ izlemenin nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz. [Enabling Network Tracing](../../../docs/framework/network-programming/enabling-network-tracing.md). Yapılandırma dosyasına eklemeniz gereken ayarlar hakkında daha fazla bilgi için bkz: [nasıl yapılır: Ağ izlemeyi yapılandırma](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).  
  
 İzleme etkin olduğunda, tarafından çıkarılan izleme bilgilerini yakalayabilirsiniz **System.Net** sınıfları. İzleme bilgileri oluşturan ağ sınıfı üyelerinin .NET Framework sınıf kitaplığı belgelerindeki Açıklamalar bölümünde aşağıdaki not vardır:  
  
> [!NOTE]
>  Uygulamanızda ağ izlemeyi etkinleştirdiğinizde, bu üye izleme bilgilerini çıkarır. Daha fazla bilgi için bkz. Ağ İzleme.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ İzlemeyi Etkinleştirme](../../../docs/framework/network-programming/enabling-network-tracing.md)
- [Nasıl yapılır: Ağ İzlemeyi Yapılandırma](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)
- [Ağ İzlemeyi Yorumlama](../../../docs/framework/network-programming/interpreting-network-tracing.md)
- [İzleme Uygulamaları](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
