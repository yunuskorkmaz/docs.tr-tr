---
title: Internet istekleri oluşturma
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
ms.openlocfilehash: ff346c5b4241f7ac037088adbe068bab2232d12f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190690"
---
# <a name="creating-internet-requests"></a>Internet istekleri oluşturma
Uygulamaları oluşturmak <xref:System.Net.WebRequest> aracılığıyla örnekler <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> yöntemi. Türetilen bir sınıf oluşturur statik bir yöntem budur **WebRequest** geçirilen URI şeması göre.  
  
## <a name="web-file-and-ftp-requests"></a>Web, dosya ve FTP istekleri  
 .NET Framework sağlar <xref:System.Net.HttpWebRequest> sınıfından türetilen sınıf **WebRequest**, HTTP ve HTTPS isteklerini işlemek için. Çoğu durumda **WebRequest** sınıfı bir istekte bulunmak için ihtiyacınız olan tüm özellikler sağlar; gerekirse, ancak çevirebilirsiniz **WebRequest** tarafından oluşturulmuş nesneleri **WebRequest.Create**  yönteme **HttpWebRequest** isteğin HTTP'ye özgü özelliklere erişim türü. Benzer şekilde, **HttpWebResponse** nesnesini işleme alınan HTTP ve HTTPS istekleri yanıtlar. HTTP özel özelliklerine erişmek için **HttpWebResponse** nesnesi, tür dönüştürme için gereksinim duyduğunuz **WebResponse** nesneleri için **HttpWebResponse** türü.  
  
 .NET Framework ayrıca sağlar <xref:System.Net.FileWebRequest> ve <xref:System.Net.FileWebResponse> kullandığınız kaynaklar için istekleri işlemek için sınıflar "dosya:" URI şeması. Benzer şekilde, <xref:System.Net.FtpWebRequest> ve <xref:System.Net.FtpWebResponse> sınıfları kullanan kaynaklar için istekleri işlemek için sağlanan "ftp:" düzeni. İsteğiniz bu düzenleri birini kullanan bir kaynak varsa kullanabileceğiniz **WebRequest.Create** hangi, istekte bulunmak bir nesne elde etmek için yöntemi.  
  
 Diğer uygulama düzeyi protokolleri kullanan isteklerini işlemek için türetilen protokole özgü sınıfların uygulamanız gereken **WebRequest** ve **WebResponse**. Daha fazla bilgi için [takılabilir protokoller programlama](../../../docs/framework/network-programming/programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: WebRequest Sınıfını Kullanarak Veri İsteme](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)  
 [Veri İsteme](../../../docs/framework/network-programming/requesting-data.md)
