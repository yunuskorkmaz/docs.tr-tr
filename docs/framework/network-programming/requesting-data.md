---
title: Veri İsteme
ms.date: 03/30/2017
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
ms.openlocfilehash: 1f367caf7656a83597b6262a5746686df15d33b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047322"
---
# <a name="requesting-data"></a>Veri İsteme
Günümüzün Internet'in dağıtılmış çalışma ortamında çalışan uygulamalar geliştirmek, her türlü kaynaktan veri almak için verimli ve kullanımı kolay bir yöntem gerektirir. Takılabilir protokoller, birden çok Internet protokolünden veri almak için tek bir arabirim kullanan uygulamalar geliştirmenize izin verir.  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a>Bir Internet Sunucusundan Veri Yükleme ve İndirme  
 Basit istek ve yanıt <xref:System.Net.WebClient> işlemleri için sınıf, bir Internet sunucusuna veri yüklemek veya verileri indirmek için en kolay yöntemi sağlar. **WebClient,** dosyaları yüklemek ve indirmek, akış göndermek ve almak, sunucuya bir veri arabelleği göndermek ve yanıt almak için yöntemler sağlar. **WebClient,** <xref:System.Net.WebRequest> Internet <xref:System.Net.WebResponse> kaynağına gerçek bağlantıları yapmak için sınıfları kullanır, böylece kayıtlı takılabilir protokol kullanılabilir.  
  
 Daha karmaşık işlemler yapması gereken istemci **uygulamaları, WebRequest** sınıfını ve onun soyundan gelenleri kullanarak sunuculardan veri talep eder. **WebRequest,** sunucuya bağlanma, isteği gönderme ve yanıt alma ayrıntılarını kapsüller. **WebRequest,** takılabilir protokoller kullanan tüm uygulamalar için kullanılabilen özellikler ve yöntemler kümesini tanımlayan soyut bir sınıftır. **WebRequest'in**torunları , <xref:System.Net.HttpWebRequest>örneğin, **WebRequest** tarafından tanımlanan özellikleri ve yöntemleri temel protokolle tutarlı bir şekilde uygularlar.  
  
 WebRequest sınıfı, oluşturmak için türetilmiş sınıf örneğini belirlemek için <xref:System.Net.WebRequest.Create%2A> yöntemine geçirilen URI değerini kullanarak **WebRequest** torunlarının protokole özgü örneklerini oluşturur. **WebRequest** Uygulamalar, soyundan gelen oluşturucuyu <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> yöntemle kaydederek bir isteği işlemek için hangi **Webİstek** soyundan gelenin kullanılması gerektiğini belirtir.  
  
 <xref:System.Net.WebRequest.GetResponse%2A> **WebRequest'teki**yöntemi arayarak Internet kaynağına istekte bulunular. **GetResponse** **yöntemi, WebRequest'in**özelliklerinden protokole özgü isteği yapar, TCP veya UDP soketi bağlantısını sunucuya yapar ve isteği gönderir. HTTP **Post** veya FTP **Put** istekleri gibi sunucuya veri <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> gönderen istekler için yöntem, verileri göndermek için bir ağ akışı sağlar.  
  
 **GetResponse** yöntemi, **Webİsteği** ile eşleşen protokole özgü bir **WebResponse** döndürür.  
  
 **WebResponse** sınıfı aynı zamanda takılabilir protokolleri kullanan tüm uygulamalar için kullanılabilen özellikleri ve yöntemleri tanımlayan soyut bir sınıftır. **WebResponse** torunları, temel protokol için bu özellikleri ve yöntemleri uygular. Sınıf, <xref:System.Net.HttpWebResponse> örneğin, HTTP için **WebResponse** sınıfını uygular.  
  
 Sunucu tarafından döndürülen veriler <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> yöntemle döndürülen akıştaki uygulamaya sunulur. Aşağıdaki örnekte gösterildiği gibi, bu akışı diğerleri gibi kullanabilirsiniz.  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework'te Ağ Programlaması](index.md)
- [Nasıl yapılır: Web Sayfası İsteme ve Sonuçları Akış Olarak Alma](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [Nasıl yapılır: WebRequest ile Eşleşen Protokole Özgü WebResponse Alma](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
