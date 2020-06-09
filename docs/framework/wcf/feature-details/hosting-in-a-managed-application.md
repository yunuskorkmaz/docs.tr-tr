---
title: Yönetilen Bir Uygulamada Barındırma
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: 759257edf89d1af5c453bb98f41361b54cf113ae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597351"
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
