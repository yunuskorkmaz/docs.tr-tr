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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047322"
---
# <a name="requesting-data"></a>Veri İsteme
Günümüzde Internet 'in dağıtılmış işletim ortamında çalışan uygulamaların geliştirilmesi, her türden kaynaktan veri almak için verimli ve kullanımı kolay bir yöntem gerektirir. Takılabilir protokoller, birden çok Internet protokolünden veri almak için tek bir arabirim kullanan uygulamalar geliştirmenize olanak sağlar.  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a>Internet sunucusundan verileri karşıya yükleme ve Indirme  
 Basit istek ve yanıt işlemleri için, <xref:System.Net.WebClient> sınıfı Internet sunucusuna veri yüklemek veya verileri indirmek için en kolay yöntemi sağlar. **WebClient** , dosyaları karşıya yükleme ve indirme, akışları gönderme ve alma, bir veri arabelleğini sunucuya gönderme ve yanıt alma için yöntemler sağlar. **WebClient** , <xref:System.Net.WebRequest> Internet kaynağına <xref:System.Net.WebResponse> yapılan gerçek bağlantıları oluşturmak için ve sınıflarını kullanır, bu nedenle tüm kayıtlı takılabilir protokolleri kullanılabilir.  
  
 **WebRequest** sınıfını ve alt öğelerini kullanarak sunuculardan daha karmaşık işlemler yapması gereken istemci uygulamalar. **WebRequest** , sunucuya bağlanma, isteği gönderme ve yanıtı alma ayrıntılarını kapsüller. **WebRequest** , takılabilir protokoller kullanan tüm uygulamalar için kullanılabilir olan özellikler ve yöntemler kümesini tanımlayan soyut bir sınıftır. **WebRequest** <xref:System.Net.HttpWebRequest>'in (gibi) alt öğeleri, **WebRequest** tarafından tanımlanan özellikleri ve yöntemleri temel protokolle tutarlı bir şekilde uygular.  
  
 **WebRequest** sınıfı, oluşturulacak özel türetilmiş sınıf örneğini tespit etmek üzere yöntemine geçirilen URI değerini kullanarak **WebRequest** alt <xref:System.Net.WebRequest.Create%2A> öğelerinin protokolüne özgü örneklerini oluşturur. Uygulamalar, alt öğe oluşturucusunu <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> yöntemiyle kaydederek bir isteği işlemek için hangi **WebRequest** alt öğesinin kullanılacağını belirtir.  
  
 <xref:System.Net.WebRequest.GetResponse%2A> **Web isteğindeki**yöntemi çağırarak Internet kaynağına bir istek yapılır. **GetResponse** yöntemi **WebRequest**özelliklerinden protokolüne özgü isteği oluşturur, TCP veya UDP soket bağlantısını sunucuya yapar ve isteği gönderir. HTTP **Post** veya FTP **PUT** <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> istekleri gibi sunucuya veri gönderen isteklerde, yöntemi verilerin gönderileceği bir ağ akışı sağlar.  
  
 **GetResponse** yöntemi **WebRequest** ile eşleşen protokole özgü bir **WebResponse** döndürür.  
  
 **WebResponse** sınıfı ayrıca takılabilir protokolleri kullanan tüm uygulamalar için kullanılabilen özellikleri ve yöntemleri tanımlayan bir soyut sınıftır. **WebResponse** alt öğeleri, temel alınan protokol için bu özellikleri ve yöntemleri uygular. Sınıfı, örneğin, http için WebResponse sınıfını uygular. <xref:System.Net.HttpWebResponse>  
  
 Sunucu tarafından döndürülen veriler, <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> yöntemi tarafından döndürülen akıştaki uygulamaya sunulur. Bu akışı, aşağıdaki örnekte gösterildiği gibi herhangi bir gibi kullanabilirsiniz.  
  
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
- [Nasıl yapılır: Web sayfası isteme ve sonuçları akış olarak alma](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [Nasıl yapılır: WebRequest Ile eşleşen protokole özgü bir WebResponse alma](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
