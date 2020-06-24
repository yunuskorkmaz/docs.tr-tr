---
title: WCF ve ASP.NET Web API
description: Her teknolojinin önemli özelliklerini karşılaştırarak WCF veya ASP.NET Web API 'sinin gereksinimlerinize daha uygun olup olmadığını öğrenin.
ms.date: 03/30/2017
ms.assetid: 08ceded3-fd9a-4467-9715-c4cbd9c7228e
ms.openlocfilehash: de8d1905866c860da96983c2f3d52599e3342403
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245983"
---
# <a name="wcf-and-aspnet-web-api"></a>WCF ve ASP.NET Web API
WCF, Microsoft 'un hizmet odaklı uygulamalar oluşturmaya yönelik Birleşik programlama modelidir. Geliştiricilerin platformlar arasında tümleşen ve mevcut yatırımlarla birlikte çalışan güvenli, güvenilir, işlem temelli çözümler oluşturmalarına olanak sağlar. [ASP.NET Web API 'si](https://www.asp.net/web-api) , tarayıcılar ve mobil cihazlar dahil olmak üzere çok çeşitli ISTEMCILERE ulaşan HTTP Hizmetleri oluşturmayı kolaylaştıran bir çerçevedir. ASP.NET Web API 'SI, .NET Framework üzerinde yeniden uygulamalar oluşturmaya yönelik ideal bir platformdur. Bu konuda, ihtiyaçlarınıza en iyi şekilde hangi teknolojinin karşılaacağına karar vermenize yardımcı olacak bazı rehberlik sunulmaktadır.  
  
## <a name="choosing-which-technology-to-use"></a>Hangi teknolojinin kullanılacağını seçme  
 Aşağıdaki tabloda her teknolojinin önemli özellikleri açıklanmaktadır.  
  
|WCF|ASP.NET Web API|  
|---------|---------------------|  
|Birden çok aktarım protokolünü (HTTP, TCP, UDP ve özel aktarımları) destekleyen hizmetlerin oluşturulmasına olanak sağlar ve aralarında geçiş yapılmasına izin verir.|Yalnızca HTTP. HTTP için birinci sınıf programlama modeli. Çeşitli tarayıcıların, mobil cihazların erişimine açık ve geniş erişim olanağı sağlayan daha uygun.|  
|Aynı ileti türünün birden çok kodlamasını (metin, MTOM ve Ikili) destekleyen ve aralarında geçiş yapmasına olanak tanıyan hizmetler oluşturmayı sağlar.|XML, JSON vb. dahil olmak üzere çok çeşitli medya türlerini destekleyen Web API 'Leri oluşturmaya izin vermez.|  
|, Güvenilir mesajlaşma, Işlemler, Ileti güvenliği gibi WS-* standartları ile hizmet oluşturmayı destekler.|, HTTP, WebSockets, SSL, JSON ve XML gibi temel protokol ve biçimleri kullanır. Güvenilir Mesajlaşma veya Işlemler gibi daha yüksek düzey protokoller için destek yoktur.|  
|Istek-yanıt, bir yol ve çift yönlü ileti değişimi düzenlerini destekler.|HTTP istek/yanıt, ancak ek desenler, [SignalR](https://github.com/SignalR/SignalR) ve WebSockets tümleştirmesi aracılığıyla desteklenebilir.|  
|WCF SOAP Hizmetleri, karmaşık şemaları olan hizmetler için bile otomatik araçların istemci proxy 'leri oluşturmasını sağlayan WSDL 'de açıklanabilir.|Web API 'sini açıklayan ve OData tümleşik API 'Ler için, kod parçacıklarını yapılandırılmış meta verilere açıklayan otomatik oluşturulan HTML yardım sayfasından bir Web API 'si tanımlamaya yönelik çeşitli yollar vardır.|  
|.NET Framework ile birlikte gönderilir.|.NET Framework ile birlikte gelir, ancak açık kaynaklı ve ayrıca, bağımsız indirme olarak bant dışı kullanılabilir.|  
  
 Çeşitli aktarımlara erişilebilen güvenilir, güvenli Web hizmetleri oluşturmak için WCF 'yi kullanın. Çok çeşitli istemcilerden erişilebilen HTTP tabanlı hizmetler oluşturmak için ASP.NET Web API 'sini kullanın. Yeni REST stili hizmetler oluşturuyorsanız ve tasarlıyorsanız ASP.NET Web API 'sini kullanın. WCF, REST stil Hizmetleri yazmak için bazı destek sağlasa da, ASP.NET Web API 'sindeki REST desteği daha tamamlanmıştır ve gelecekteki tüm REST özelliklerinin geliştirmeleri ASP.NET Web API 'sinde yapılır. Mevcut bir WCF hizmetiniz varsa ve ek REST uç noktalarını göstermek istiyorsanız, WCF ve ' yi kullanın <xref:System.ServiceModel.WebHttpBinding> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation nedir?](whats-wcf.md)
- [Temel Windows Communication Foundation Kavramları](fundamental-concepts.md)
