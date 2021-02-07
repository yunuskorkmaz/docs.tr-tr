---
description: 'Daha fazla bilgi edinin: yönetilen bir uygulamada barındırma'
title: Yönetilen Bir Uygulamada Barındırma
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: 14fd6b2dea1a4315567611f505f2898314a07908
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756207"
---
# <a name="hosting-in-a-managed-application"></a>Yönetilen Bir Uygulamada Barındırma

Windows Communication Foundation (WCF) Hizmetleri, herhangi bir .NET Framework uygulamasında barındırılabilir. Dağıtım için en az altyapıyı gerektirdiğinden, kendi kendine barındırma hizmetleri en esnek barındırma seçeneğidir. Bununla birlikte, yönetilen uygulamalar Internet Information Services (IIS) ve Windows Hizmetleri gibi WCF 'deki diğer barındırma seçeneklerinin gelişmiş barındırma ve yönetim özelliklerini sağlamadığı için de en az güçlü barındırma seçeneğidir.  
  
 Şirket içinde barındırılan bir hizmet oluşturmak için, <xref:System.ServiceModel.ServiceHost> ileti dinleme yapan bir hizmet Başlatan bir örneğini oluşturun ve açın. Daha fazla bilgi için bkz. [nasıl yapılır: yönetilen bir uygulamada BIR WCF hizmeti barındırma](../how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Bir sözleşmenin nasıl tanımlanacağı, sözleşmenin nasıl uygulanacağı ve bir hizmetin yönetilen bir uygulamanın içinde barındırılamadığına ilişkin tam bir örnek için, [Başlangıç öğreticisine](../getting-started-tutorial.md) ve [self-Host](../samples/self-host.md)' a bakın.  
  
 Aşağıdaki bölümlerde, bu barındırma seçeneğini kullanan yaygın senaryolar açıklanır.  
  
## <a name="console-applications"></a>Konsol uygulamaları  

 Kendini barındıran yaygın senaryolar, konsol uygulamaları içinde çalışan WCF hizmetlerdir. Bir WCF hizmetini bir konsol uygulaması içinde barındırmak, genellikle hizmetin geliştirme aşamasında yararlıdır. Bu, uygulamanın içinde neler olduğunu öğrenmek ve yeni konumlara kopyalayarak kolayca geçiş yapmak için, ' den izleme bilgilerinin oluşmasını kolay bir şekilde oluşturmanızı kolaylaştırır.  
  
## <a name="rich-client-applications"></a>Zengin Istemci uygulamaları  

 Kendi kendini barındıran yaygın senaryolar, Windows Presentation Foundation (WPF) veya Windows Forms (WinForms) tabanlı olanlar gibi zengin istemci uygulamalardır. Bu barındırma seçeneği Ayrıca, WPF ve WinForms uygulamaları gibi zengin istemci uygulamalarının dış dünya ile iletişim kurmasını kolaylaştırır. Örneğin, Kullanıcı arabirimi için WPF kullanan eşler arası işbirliği istemcisi ve ayrıca diğer istemcilerin bu sunucuya bağlanmasına ve bilgi paylaşmasına izin veren bir WCF hizmeti barındırır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Hizmetleri](../hosting-services.md)
- [Başlangıç Öğreticisi](../getting-started-tutorial.md)
