---
title: Internet isteği oluşturma
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8ebe861fc2de8b21ee766e52dada1eec10169f16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="creating-internet-requests"></a>Internet isteği oluşturma
Uygulamaları oluşturma <xref:System.Net.WebRequest> aracılığıyla örnekleri <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> yöntemi. Bu, türetilmiş bir sınıf oluşturur, statik bir yöntemdir **WebRequest** kendisine geçirilen URI şeması göre.  
  
## <a name="web-file-and-ftp-requests"></a>Web, dosya ve FTP istekleri  
 .NET Framework sağlar <xref:System.Net.HttpWebRequest> türetilmiş sınıf **WebRequest**, HTTP ve HTTPS isteklerini işlemek için. Çoğu durumda, **WebRequest** sınıfı, bir isteği yapmak için gereken tüm özellikleri sağlar; gerekirse, ancak çevirebilirsiniz **WebRequest** tarafından oluşturulan nesneler **WebRequest.Create**  yönteme **HttpWebRequest** isteğin HTTP özgü özelliklere erişmek için türü. Benzer şekilde, **HttpWebResponse** nesne HTTP ve HTTPS istekleri yanıtlarının işler. HTTP özgü özelliklerine erişmek için **HttpWebResponse** nesnesi, cast gereken **WebResponse** nesneleri **HttpWebResponse** türü.  
  
 .NET Framework ayrıca sağlar <xref:System.Net.FileWebRequest> ve <xref:System.Net.FileWebResponse> kullanan kaynaklar için istekleri işlemek için sınıflar "dosya:" URI düzeni. Benzer şekilde, <xref:System.Net.FtpWebRequest> ve <xref:System.Net.FtpWebResponse> sınıfları kullanan kaynaklar için istekleri işlemek için sağlanan "ftp:" düzeni. İsteğiniz bu düzenleri birini kullanan bir kaynak için ise, kullanabileceğiniz **WebRequest.Create** hangi isteğiniz yapmak bir nesne elde etmek için yöntemi.  
  
 Diğer uygulama düzeyi protokolleri kullanan isteklerini işlemek için türetilmiş protokole özgü sınıflar uygulamanız gereken **WebRequest** ve **WebResponse**. Daha fazla bilgi için bkz: [programlama Takılabilir Protokol](../../../docs/framework/network-programming/programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: WebRequest Sınıfını Kullanarak Veri İsteme](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)  
 [Veri İsteme](../../../docs/framework/network-programming/requesting-data.md)
