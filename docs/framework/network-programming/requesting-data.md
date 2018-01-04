---
title: "İstekte bulunan verileri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sending data
- WebRequest class, sending and receiving data
- requesting data from Internet, about requesting data
- WebClient class, sending and receiving data
- network, requesting data
- receiving data
- sending data, about sending data
- response to Internet request, about responding to Internet requests
- data requests
- receiving data, about receiving data
- Internet, requesting data
ms.assetid: df6f1e1d-6f2a-45dd-8141-4a85c3dafe1d
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 76ea605444b5d1776c5a85891db4f3460e9df24b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="requesting-data"></a>İstekte bulunan verileri
Bugünün Internet dağıtılmış işletim ortamında çalışan uygulamalar geliştirme, tüm türleri kaynaklardan veri almak için verimli, kullanımı kolay bir yöntem gerektirir. Takılabilir Protokol birden çok Internet kurallarından veri almak için tek bir arabirim kullanan uygulamalar geliştirmenize olanak tanır.  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a>Karşıya yükleme ve Internet sunucusundan veri indirme  
 Basit istek ve yanıt işlemler için <xref:System.Net.WebClient> sınıfı verileri yüklemeyi veya bir Internet sunucusundan veri indirmek için en kolay yöntem sağlar. **WebClient** karşıya yükleme ve indirme dosyaları, gönderme ve alma akışlar ve veri arabelleği sunucuya göndermek ve bir yanıt almak için yöntemleri sağlar. **WebClient** kullanan <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları herhangi takılabilir protokolü kayıtlı Internet kaynağının gerçek bağlantıları olmak için kullanılabilir.  
  
 Daha karmaşık işlemleri istek verileri kullanarak sunucularından yapmanız gereken istemci uygulamaları **WebRequest** sınıfı ve alt öğeleri. **WebRequest** bağlanırken, bu isteği göndermek ve yanıt alma ayrıntılarını yalıtır. **WebRequest** özellikleri ve takılabilir protokoller kullanan tüm uygulamalar için kullanılabilir yöntemleri kümesini tanımlayan bir Özet sınıf. Alt öğeleri **WebRequest**, gibi <xref:System.Net.HttpWebRequest>, özellikleri ve yöntemleri tarafından tanımlanan uygulama **WebRequest** temel protokolü ile tutarlı bir şekilde.  
  
 **WebRequest** sınıfı protokole özgü örneklerini oluşturur **WebRequest** URI değeri kullanılarak alt geçirilen kendi <xref:System.Net.WebRequest.Create%2A> belirli türetilmiş sınıf belirlemek amacıyla yöntemi oluşturmak için örneği. Uygulamaları belirtmek, **WebRequest** alt öğesi, alt öğesi'nin oluşturucusu ile kaydederek bir isteği işlemek için kullanılmalıdır <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> yöntemi.  
  
 Bir istek için Internet kaynağının çağırarak yapıldığında <xref:System.Net.WebRequest.GetResponse%2A> yöntemi **WebRequest**. **GetResponse** yöntemi oluşturur özelliklerini protokole özgü isteğinden **WebRequest**, sunucuya TCP veya UDP yuva bağlantı yapar ve isteği gönderir. HTTP gibi sunucusuna veri gönderme istekleri için **Post** veya FTP **Put** istekleri <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> yöntemi, veri göndermek bir ağ akışı sağlar.  
  
 **GetResponse** yöntemi döndürür protokole özgü **WebResponse** eşleşen **WebRequest.**  
  
 **WebResponse** sınıfı, ayrıca özellikleri ve takılabilir protokoller kullanan tüm uygulamalar için kullanılabilir yöntemleri tanımlayan bir Özet sınıf. **WebResponse** descendants uygulamak bu özellikleri ve yöntemleri temel protokolü için. <xref:System.Net.HttpWebResponse> , Örneğin, uygulayan sınıf **WebResponse** HTTP için sınıf.  
  
 Sunucu tarafından döndürülen veri tarafından döndürülen akış uygulamasına sunulan <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> yöntemi. Aşağıdaki örnekte gösterildiği gibi diğer, bu akış kullanabilirsiniz.  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework'te Ağ Programlaması](../../../docs/framework/network-programming/index.md)  
 [Nasıl yapılır: Web Sayfası İsteme ve Sonuçları Akış Olarak Alma](../../../docs/framework/network-programming/how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)  
 [Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma](../../../docs/framework/network-programming/how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
