---
title: İnternet İstekleri Oluşturma
description: Uygulamaların, kendisine geçirilen URI şemasını temel alan türetilmiş bir sınıf oluşturan bir statik yöntem olan WebRequest. Create aracılığıyla Web Isteği örnekleri oluşturma hakkında bilgi edinin.
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
ms.openlocfilehash: 598ef9d44737ef6b33af833cbfb7788170165588
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502632"
---
# <a name="creating-internet-requests"></a>İnternet İstekleri Oluşturma
Uygulamalar <xref:System.Net.WebRequest> , yöntemi aracılığıyla örnek oluşturur <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> . Bu, kendisine geçirilen URI şemasını temel alan **WebRequest** 'ten türetilmiş bir sınıf oluşturan statik bir yöntemdir.  
  
## <a name="web-file-and-ftp-requests"></a>Web, dosya ve FTP Istekleri  
 .NET Framework, <xref:System.Net.HttpWebRequest> http ve https isteklerini işlemek Için **WebRequest**'ten türetilen sınıfı sağlar. Çoğu durumda, **WebRequest** sınıfı bir istek yapmak için ihtiyacınız olan tüm özellikleri sağlar; Ancak, gerekirse, isteğin HTTP 'e özgü özelliklerine erişmek için **Web isteği. Create** yöntemi tarafından oluşturulan **WebRequest** nesnelerini **HttpWebRequest** türüne çevirebilirsiniz. Benzer şekilde, **HttpWebResponse** nesnesi http ve https isteklerindeki yanıtları işler. **HttpWebResponse** nesnesinin http 'e özgü özelliklerine erişmek Için **WebResponse** nesnelerini **HttpWebResponse** türüne atamalısınız.  
  
 .NET Framework Ayrıca, <xref:System.Net.FileWebRequest> <xref:System.Net.FileWebResponse> "File:" URI düzenini kullanan kaynaklara yönelik istekleri işlemek için ve sınıflarını sağlar. Benzer şekilde, <xref:System.Net.FtpWebRequest> ve <xref:System.Net.FtpWebResponse> sınıfları "FTP:" düzenini kullanan kaynaklar için istekleri işlemek üzere sağlanır. İsteğiniz bu düzenlerden herhangi birini kullanan bir kaynak için ise, isteğinizi yapmak için bir nesne elde etmek üzere **WebRequest. Create** yöntemini kullanabilirsiniz.  
  
 Diğer uygulama düzeyi protokolleri kullanan istekleri işlemek için **WebRequest** ve **WebResponse**'dan türetilmiş protokole özgü sınıfları uygulamanız gerekir. Daha fazla bilgi için bkz. [takılabilir protokolleri programlama](programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: WebRequest Sınıfını Kullanarak Veri İsteme](how-to-request-data-using-the-webrequest-class.md)
- [Veri İsteme](requesting-data.md)
