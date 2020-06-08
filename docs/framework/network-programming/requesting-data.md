---
title: Veri İsteme
description: Takılabilir protokollerin birden çok protokolden veri almak için tek bir arabirim kullanan uygulamalar geliştirmenize nasıl olanak sağladığını öğrenin.
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
ms.openlocfilehash: 19350d685a81d56657ca0a117d61b50ae24fab6a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502190"
---
# <a name="requesting-data"></a>Veri İsteme
Günümüzde Internet 'in dağıtılmış işletim ortamında çalışan uygulamaların geliştirilmesi, her türden kaynaktan veri almak için verimli ve kullanımı kolay bir yöntem gerektirir. Takılabilir protokoller, birden çok Internet protokolünden veri almak için tek bir arabirim kullanan uygulamalar geliştirmenize olanak sağlar.  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a>Internet sunucusundan verileri karşıya yükleme ve Indirme  
 Basit istek ve yanıt işlemleri için, <xref:System.Net.WebClient> sınıfı Internet sunucusuna veri yüklemek veya verileri indirmek için en kolay yöntemi sağlar. **WebClient** , dosyaları karşıya yükleme ve indirme, akışları gönderme ve alma, bir veri arabelleğini sunucuya gönderme ve yanıt alma için yöntemler sağlar. **WebClient** , <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> Internet kaynağına yapılan gerçek bağlantıları oluşturmak için ve sınıflarını kullanır, bu nedenle tüm kayıtlı takılabilir protokolleri kullanılabilir.  
  
 **WebRequest** sınıfını ve alt öğelerini kullanarak sunuculardan daha karmaşık işlemler yapması gereken istemci uygulamalar. **WebRequest** , sunucuya bağlanma, isteği gönderme ve yanıtı alma ayrıntılarını kapsüller. **WebRequest** , takılabilir protokoller kullanan tüm uygulamalar için kullanılabilir olan özellikler ve yöntemler kümesini tanımlayan soyut bir sınıftır. **WebRequest**'in (gibi) alt öğeleri, <xref:System.Net.HttpWebRequest> **WebRequest** tarafından tanımlanan özellikleri ve yöntemleri temel protokolle tutarlı bir şekilde uygular.  
  
 **WebRequest** sınıfı, oluşturulacak özel türetilmiş sınıf örneğini tespit etmek üzere YÖNTEMINE geçirilen URI değerini kullanarak **WebRequest** alt öğelerinin protokolüne özgü örneklerini oluşturur <xref:System.Net.WebRequest.Create%2A> . Uygulamalar, alt öğe oluşturucusunu yöntemiyle kaydederek bir isteği işlemek için hangi **WebRequest** alt öğesinin kullanılacağını belirtir <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> .  
  
 <xref:System.Net.WebRequest.GetResponse%2A> **Web isteğindeki**yöntemi çağırarak Internet kaynağına bir istek yapılır. **GetResponse** yöntemi **WebRequest**özelliklerinden protokolüne özgü isteği oluşturur, TCP veya UDP soket bağlantısını sunucuya yapar ve isteği gönderir. HTTP **Post** veya FTP **PUT** istekleri gibi sunucuya veri gönderen isteklerde, <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> yöntemi verilerin gönderileceği bir ağ akışı sağlar.  
  
 **GetResponse** yöntemi **WebRequest** ile eşleşen protokole özgü bir **WebResponse** döndürür.  
  
 **WebResponse** sınıfı ayrıca takılabilir protokolleri kullanan tüm uygulamalar için kullanılabilen özellikleri ve yöntemleri tanımlayan bir soyut sınıftır. **WebResponse** alt öğeleri, temel alınan protokol için bu özellikleri ve yöntemleri uygular. <xref:System.Net.HttpWebResponse>Sınıfı, örneğin, http Için **WebResponse** sınıfını uygular.  
  
 Sunucu tarafından döndürülen veriler, yöntemi tarafından döndürülen akıştaki uygulamaya sunulur <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> . Bu akışı, aşağıdaki örnekte gösterildiği gibi herhangi bir gibi kullanabilirsiniz.  
  
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
