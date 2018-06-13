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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 505c5f39890f7f362c5f5d8525a65f8c3d05624a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398046"
---
# <a name="network-tracing-in-the-net-framework"></a>.NET Framework'te Ağ İzleme
.NET Framework'te ağ izleme, yönetilen uygulama tarafından oluşturulan yöntem çağrıları ve ağ trafiğiyle ilgili bilgilere erişim sağlar. Bu özellik, geliştirilen uygulamalarda hata ayıklanırken ve dağıtılan uygulamalar analiz edilirken yararlı olur. Ağ izleme tarafından sağlanan çıkış, geliştirme zamanı ve üretim ortamında farklı kullanım senaryolarını destekleyecek şekilde özelleştirilebilir.  
  
 .NET Framework'te ağ izlemeyi etkinleştirmek üzere izleme çıkışı için bir hedef seçmeniz ve ağ izleme yapılandırma ayarlarını uygulamaya ve makine yapılandırma dosyasına eklemeniz gerekir. Yapılandırma dosyaları ve bunların nasıl kullanıldığı açıklamaları için bkz: [yapılandırma dosyalarını](../../../docs/framework/configure-apps/index.md). Ağ izlemeyi etkinleştirme hakkında daha fazla bilgi için bkz: [etkinleştirme ağ izleme](../../../docs/framework/network-programming/enabling-network-tracing.md). Yapılandırma dosyası eklemek için gereken ayarları hakkında daha fazla bilgi için bkz: [nasıl yapılır: yapılandırma ağ izleme](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).  
  
 İzleme etkinleştirildiğinde tarafından çıkış izleme bilgileri yakalamak için **System.Net** sınıfları. İzleme bilgileri oluşturan ağ sınıfı üyelerinin .NET Framework sınıf kitaplığı belgelerindeki Açıklamalar bölümünde aşağıdaki not vardır:  
  
> [!NOTE]
>  Uygulamanızda ağ izlemeyi etkinleştirdiğinizde, bu üye izleme bilgilerini çıkarır. Daha fazla bilgi için bkz. Ağ İzleme.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ağ İzlemeyi Etkinleştirme](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [Nasıl yapılır: Ağ İzlemeyi Yapılandırma](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)  
 [Ağ İzlemeyi Yorumlama](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [İzleme ve izleme giriş](http://msdn.microsoft.com/library/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
