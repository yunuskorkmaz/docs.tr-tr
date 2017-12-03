---
title: WCF ve ASP.NET Web API
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08ceded3-fd9a-4467-9715-c4cbd9c7228e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9b311dc5b328a09bd301cc1d012ca4d13cfb70f9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-and-aspnet-web-api"></a>WCF ve ASP.NET Web API
WCF hizmet odaklı uygulamalar oluşturmak için Microsoft'un programlama modelidir. Geliştiricilerin platformlarla tümleştirilen ve Yatırımlar ile birlikte çalışmak güvenli, güvenilir ve işlenen çözümleri oluşturmasına olanak sağlar. [ASP.NET Web API](http://www.asp.net/web-api) istemciler, tarayıcılar ve mobil cihazlar dahil olmak üzere çok çeşitli ulaşmak HTTP hizmetlerini oluşturmayı kolaylaştıran bir çerçevedir. ASP.NET Web API, .NET Framework üzerinde RESTful uygulamaları geliştirmek için ideal bir platformdur. Bu konuda, hangi teknoloji gereksinimlerinizi en iyi şekilde karşılayacağını karar vermenize yardımcı olacak bazı yönergeler sunar.  
  
## <a name="choosing-which-technology-to-use"></a>Hangi teknolojinin kullanılacağını seçme  
 Aşağıdaki tabloda her bir teknolojinin ana özelliklerini açıklar.  
  
|WCF|ASP.NET Web API|  
|---------|---------------------|  
|Birden fazla aktarım protokolünü (HTTP, TCP, UDP ve özel taşımaları) Destek Hizmetleri oluşturma sağlar ve bunlar arasında geçiş sağlar.|Yalnızca HTTP. HTTP için birinci sınıf programlama modeli. Erişim çeşitli tarayıcılardan vb. etkinleştirme geniş ulaşmak mobil cihazlar için daha uygundur.|  
|Yazın ve bunlar arasında geçiş yapma sağlar, aynı iletiyi birden çok kodlamaları (metin, MTOM ve ikili) destekleyen hizmetler oluşturma sağlar.|Medya türleri XML, JSON vb. de dahil olmak üzere çeşitli destek Web API'leri oluşturmaya olanak tanır.|  
|WS - hizmetleriyle oluşturma destekler * standartları güvenilir Mesajlaşma, işlemler, ileti güvenliği ister.|Temel protokolünü kullanır ve HTTP, WebSockets, SSL, JQuery, JSON ve XML gibi biçimlendirir. Güvenilir Mesajlaşma veya işlemler gibi daha yüksek düzey protokoller için desteği yoktur.|  
|İstek-yanıt, bir yol ve çift yönlü ileti exchange desenleri destekler.|HTTP istek/yanıt olmakla birlikte ek modelleri desteklenir aracılığıyla [SignalR](https://github.com/SignalR/SignalR) ve WebSockets tümleştirme.|  
|WCF SOAP Hizmetleri karmaşık şemaları hizmetleriyle için bile istemci proxy'leri oluşturmak için WSDL otomatik araçlar sağlayan açıklanabilir.|Bir Web API OData tümleşik için yapılandırılmış meta verilerine parçacıkları açıklayan otomatik olarak oluşturulan HTML Yardım sayfasından arasında değişen bir API açıklamak için çeşitli yollar vardır.|  
|.NET framework ile gelir.|.NET framework ile birlikte gelir ancak açık kaynaklıdır ve ayrıca kullanılabilir-bant olarak bağımsız indirme.|  
  
 WCF güvenilir, güvenli web hizmetleri taşımaları çeşitli bu erişilebilir oluşturmak için kullanın. Çok çeşitli istemciler erişilebilir HTTP tabanlı hizmetler oluşturmak için ASP.NET Web API kullanın. Oluşturma ve yeni REST stili Hizmetleri tasarlama, ASP.NET Web API kullanın. WCF bazı destek REST stili Hizmetleri yazmak için sağlasa da, ASP.NET Web API REST desteği daha kapsamlı ve gelecekteki tüm REST özellik geliştirmeleri ASP.NET Web API'de yapılır. Var olan bir WCF hizmetini varsa ve ek REST uç noktalarını kullanıma sunmak istediğiniz, WCF kullanın ve <xref:System.ServiceModel.WebHttpBinding>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Communication Foundation nedir](../../../docs/framework/wcf/whats-wcf.md)  
 [Temel Windows Communication Foundation kavramları](../../../docs/framework/wcf/fundamental-concepts.md)  
