---
title: İnternet İstekleri Oluşturma
description: Uygulamaların, kendisine geçirilen URI şemasını temel alan türetilmiş bir sınıf oluşturan WebRequest. Create yöntemi aracılığıyla WebRequest örnekleri oluşturma yöntemini öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
ms.openlocfilehash: 389c7bf5969eca4322aa680a6f28dec0b899709a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325633"
---
# <a name="create-internet-requests"></a>İnternet istekleri oluşturma

Uygulamalar <xref:System.Net.WebRequest> , yöntemi aracılığıyla örnek oluşturur <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> . <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>, <xref:System.Net.WebRequest> kendisine GEÇIRILEN URI şemasına göre türetilmiş bir sınıf oluşturan statik bir yöntemdir.  
  
## <a name="web-file-and-ftp-requests"></a>Web, dosya ve FTP istekleri

.NET Framework, <xref:System.Net.HttpWebRequest> `WebRequest` http ve https isteklerini işlemek için öğesinden türetilmiş sınıfı sağlar. Çoğu durumda, `WebRequest` sınıfı bir istek yapmak için ihtiyacınız olan tüm özellikleri sağlar; ancak, gerekirse, `WebRequest` `WebRequest.Create` `HttpWebRequest` isteğin HTTP 'e özgü özelliklerine erişmek için yöntemi tarafından oluşturulan nesneleri türüne çevirebilirsiniz. Benzer şekilde, `HttpWebResponse` nesne http ve https isteklerindeki yanıtları işler. Nesnenin HTTP 'ye özgü özelliklerine erişmek için `HttpWebResponse` `WebResponse` nesneleri `HttpWebResponse` türe atamalısınız.  
  
.NET Framework Ayrıca, <xref:System.Net.FileWebRequest> <xref:System.Net.FileWebResponse> "File:" URI düzenini kullanan kaynaklara yönelik istekleri işlemek için ve sınıflarını sağlar. Benzer şekilde, <xref:System.Net.FtpWebRequest> ve <xref:System.Net.FtpWebResponse> sınıfları "FTP:" düzenini kullanan kaynaklar için istekleri işlemek üzere sağlanır. İsteğiniz bu düzenlerden herhangi birini kullanan bir kaynak için ise, `WebRequest.Create` isteğinizi yapmak için bir nesne elde etmek üzere yöntemini kullanabilirsiniz.  
  
Diğer uygulama düzeyi protokolleri kullanan istekleri işlemek için, ve ' den türetilen protokole özgü sınıflar uygulayın `WebRequest` `WebResponse` . Daha fazla bilgi için bkz. [takılabilir protokolleri programlama](programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: WebRequest Sınıfını Kullanarak Veri İsteme](how-to-request-data-using-the-webrequest-class.md)
- [Veri İsteme](requesting-data.md)
