---
title: İnternet İstekleri Oluşturma
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
ms.openlocfilehash: 80e3a6bd199691df9391e88d5a64fab5df2a08a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048614"
---
# <a name="creating-internet-requests"></a>İnternet İstekleri Oluşturma
Uygulamalar <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> yöntem <xref:System.Net.WebRequest> üzerinden örnekler oluşturur. Bu, **webisteğinden** türetilen bir sınıfı, ona geçirilen URI düzenini temel alan statik bir yöntemdir.  
  
## <a name="web-file-and-ftp-requests"></a>Web, Dosya ve FTP İstekleri  
 .NET Framework, <xref:System.Net.HttpWebRequest> HTTP ve HTTPS isteklerini işlemek için **WebRequest'ten**türetilen sınıfı sağlar. Çoğu durumda, **Webİstek** sınıfı istekte bulunmak için gereken tüm özellikleri sağlar; ancak, gerekirse, isteğin HTTP'ye özgü özelliklerine erişmek için **WebRequest.Create** yöntemi tarafından oluşturulan **WebRequest** nesnelerini **HttpWebRequest** türüne atabilirsiniz. Benzer şekilde, **HttpWebResponse** nesnesi HTTP ve HTTPS isteklerinden gelen yanıtları işler. **HttpWebResponse** nesnesinin HTTP'ye özgü özelliklerine erişmek için **WebResponse** nesnelerini **HttpWebResponse** türüne dökmeniz gerekir.  
  
 .NET Framework ayrıca <xref:System.Net.FileWebRequest> "dosya:" URI düzenini kullanan kaynaklar için istekleri işlemek için <xref:System.Net.FileWebResponse> ve sınıfları sağlar. Aynı şekilde, <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> ve sınıflar "ftp:" düzenini kullanan kaynaklar için istekleri işlemek için sağlanır. İsteğiniz bu düzenlerden herhangi birini kullanan bir kaynak içinse, isteğinizi yapmak için bir nesne elde etmek için **WebRequest.Create** yöntemini kullanabilirsiniz.  
  
 Diğer uygulama düzeyi protokollerini kullanan istekleri işlemek için **WebRequest** ve **WebResponse'dan**türetilen protokole özgü sınıfları uygulamanız gerekir. Daha fazla bilgi için, [Takılabilir Programlama Protokolleri'ne](programming-pluggable-protocols.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: WebRequest Sınıfını Kullanarak Veri İsteme](how-to-request-data-using-the-webrequest-class.md)
- [Veri İsteme](requesting-data.md)
